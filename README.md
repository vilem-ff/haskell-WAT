# Haskell WATs

This is a collection of Haskell's WATs

## Eq Double

``` haskell
Prelude> let nan = read "NaN" :: Double
Prelude> nan == nan
False
Prelude> nan /= nan
True
```

## Ord Double

``` haskell
Prelude> let nan = read "NaN" :: Double
Prelude> nan >= nan
False
Prelude> nan > nan
False
Prelude> nan <= nan
False
Prelude> nan < nan
False
Prelude> compare nan nan
GT
```

## Real Double

``` Haskell
Prelude> let nan = read "NaN" :: Double
Prelude> toRational nan
(-269653970229347386159395778618353710042696546841345985910145121736599013708251444699062715983611304031680170819807090036488184653221624933739271145959211186566651840137298227914453329401869141179179624428127508653257226023513694322210869665811240855745025766026879447359920868907719574457253034494436336205824) % 1
Prelude> realToFrac nan -- With -O0
-Infinity
Prelude> realToFrac nan
NaN
```

## RealFrac Double

```
Prelude> let nan = read "NaN" :: Double
Prelude> properFraction nan
(-269653970229347386159395778618353710042696546841345985910145121736599013708251444699062715983611304031680170819807090036488184653221624933739271145959211186566651840137298227914453329401869141179179624428127508653257226023513694322210869665811240855745025766026879447359920868907719574457253034494436336205824,0.0)
truncate nan
-269653970229347386159395778618353710042696546841345985910145121736599013708251444699062715983611304031680170819807090036488184653221624933739271145959211186566651840137298227914453329401869141179179624428127508653257226023513694322210869665811240855745025766026879447359920868907719574457253034494436336205824
Prelude> round nan
-269653970229347386159395778618353710042696546841345985910145121736599013708251444699062715983611304031680170819807090036488184653221624933739271145959211186566651840137298227914453329401869141179179624428127508653257226023513694322210869665811240855745025766026879447359920868907719574457253034494436336205824
Prelude> floor nan
-269653970229347386159395778618353710042696546841345985910145121736599013708251444699062715983611304031680170819807090036488184653221624933739271145959211186566651840137298227914453329401869141179179624428127508653257226023513694322210869665811240855745025766026879447359920868907719574457253034494436336205824
Prelude> ceiling nan
-269653970229347386159395778618353710042696546841345985910145121736599013708251444699062715983611304031680170819807090036488184653221624933739271145959211186566651840137298227914453329401869141179179624428127508653257226023513694322210869665811240855745025766026879447359920868907719574457253034494436336205824
Prelude> properFraction nan :: (Int, Double)
(0,0.0)
Prelude> round nan :: Int
0
Prelude> floor nan :: Int
0
Prelude> ceiling nan :: Int
0
```

## Num Int

```
Prelude> minBound * (-1) :: Int
-9223372036854775808
Prelude> abs (minBound :: Int)
-9223372036854775808
Prelude> minBound `div` (-1) :: Int
*** Exception: arithmetic overflow
Prelude> minBound `quot` (-1) :: Int
*** Exception: arithmetic overflow
```

Do we want modular arithmetic on `Int` or do we want to throw errors on (over|under)flow?
