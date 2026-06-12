---
title: "How to compile and run program using QuickCheck with Haskell Platform"
date: 2011-11-04
forum: Programming Talk
---

### Post by william2011 on 2011-11-04
sudo apt-get install Haskell-Platform cabal install QuickCheck 2.4.1 success

when following manual to run an example [http://www.cse.chalmers.se/~rjmh/QuickCheck/manual.html](http://www.cse.chalmers.se/~rjmh/QuickCheck/manual.html)

Prelude> prop_RevRev xs = reverse (reverse xs) == xs where types = xs::[Int]

parse error on input '='

Prelude>quickCheck

not in scope

Prelude>QuickCheck

not in scope data constructor

Then download QuickCheck.hs ghc -O2 --make QuickCheck.hs -threaded -rtsopts 147.52 Not in scopr 'chr' 148.27 Not in scope 'ord' 155.41 not in scope fromInt 155.51 Not in scope fromInt

then run a test.hs which contain

main = QuickCheck some_properties

compile with

ghc -O2 --make test.hs -threaded -rtsopts

Not in scope data constructor 'QuickCheck'

---

### Post by william2011 on 2011-11-04
import Test.QuickCheck.Function
import Test.QuickCheck.Gen

promote :: (a -> Gen b) -> (Gen (a->b))
promote f = Gen (\n r -> 
         \a -> m n r where Gen m = f a)

class Coarbitrary a where
coarbitrary :: a -> (Gen b -> Gen b)

instance (Coarbitrary a, Arbitrary b) => Arbitrary (a -> b) where
arbitrary = promote (a -> coarbitrary a arbitrary)

variant :: Int -> Gen a -> Gen a
variant v (Gen m) = Gen (\n r -> m n (rands r !! (v+1)))
where rands r0 = r1 : rands r2
where (r1, r2) = Random.split r0

instance Coarbitrary Bool where
coarbitrary b = if b then variant 0 else variant 1

instance Arbitrary Int where
arbitrary = sized $ \n -> choose (-n,n)
coarbitrary n = variant (if n >= 0 then 2*n else 2*(-n) + 1)

instance (Coarbitrary a, Coarbitrary b)
=> Coarbitrary (a, b) where
coarbitrary (a, b) = coarbitrary a . coarbitrary b

instance Coarbitrary a => Coarbitrary [a] where
coarbitrary []
= variant 0
coarbitrary (a:as) = coarbitrary a . variant 1 . coarbitrary

main :: IO ()
main = QuickCheck promote

---

### Post by william2011 on 2011-11-04
import Test.QuickCheck.Function
import Test.QuickCheck.Gen

promote :: (a -> Gen b) -> (Gen (a->b))
promote f = Gen (\n r -> 
         \a -> m n r where Gen m = f a)

class Coarbitrary a where
coarbitrary :: a -> (Gen b -> Gen b)

instance (Coarbitrary a, Arbitrary b) => Arbitrary (a -> b) where
arbitrary = promote (a -> coarbitrary a arbitrary)

variant :: Int -> Gen a -> Gen a
variant v (Gen m) = Gen (\n r -> m n (rands r !! (v+1)))
where rands r0 = r1 : rands r2
where (r1, r2) = Random.split r0

instance Coarbitrary Bool where
coarbitrary b = if b then variant 0 else variant 1

instance Arbitrary Int where
arbitrary = sized $ \n -> choose (-n,n)
coarbitrary n = variant (if n >= 0 then 2*n else 2*(-n) + 1)

instance (Coarbitrary a, Coarbitrary b)
=> Coarbitrary (a, b) where
coarbitrary (a, b) = coarbitrary a . coarbitrary b

instance Coarbitrary a => Coarbitrary [a] where
coarbitrary []
= variant 0
coarbitrary (a:as) = coarbitrary a . variant 1 . coarbitrary

main :: IO ()
main = QuickCheck promote

---

### Post by william2011 on 2011-11-04
sudo apt-get install Haskell-Platform cabal install QuickCheck 2.4.1 success

when following manual to run an example [http://www.cse.chalmers.se/~rjmh/QuickCheck/manual.html]("http://www.cse.chalmers.se/%7Erjmh/QuickCheck/manual.html")

Prelude> prop_RevRev xs = reverse (reverse xs) == xs where types = xs::[Int]

parse error on input '='

Prelude>quickCheck

not in scope

Prelude>QuickCheck

not in scope data constructor

Then download QuickCheck.hs ghc -O2 --make QuickCheck.hs -threaded  -rtsopts 147.52 Not in scopr 'chr' 148.27 Not in scope 'ord' 155.41 not  in scope fromInt 155.51 Not in scope fromInt

then run a test.hs which contain

main = QuickCheck some_properties

compile with

ghc -O2 --make test.hs -threaded -rtsopts

Not in scope data constructor 'QuickCheck'

---

### Post by lisati on 2011-11-04
Which language is it? Python? Some [noparse]```
 and 
```[/noparse] tags might be useful too....

---

### Post by william2011 on 2011-11-04
Haskell

---

### Post by lisati on 2011-11-04
Threads merged. Please do not start multiple theads in multiple locations for the same problem.

---

### Post by william2011 on 2011-11-04
As no one watch in the section "compiling", i post two places

---

### Post by SevenMachines on 2011-11-05
I'm not sure i really follow what you're doing here, can you post the code inside code tags please and state the steps you're following. Note that the link you provide is out of date, quickcheck is part of the haskell support available in the main ubuntu repositories.

# install haskell and quickcheck
```
$ sudo apt-get install ghc libghc-quickcheck1-dev 
``` Just to check that you've got everything set up properly here are 2 examples

(1) This example from the [haskell wiki]("http://www.haskell.org/haskellwiki/Introduction_to_QuickCheck")

# Thing to test
```
$ cat take5.hs 
``````
import Data.Char
import Test.QuickCheck
 
instance Arbitrary Char where
    arbitrary     = choose ('\32', '\128')
    coarbitrary c = variant (ord c `rem` 4)
```# Run a quickcheck test 
```
$ ghci take5.hs 
``````
*Main> quickCheck ((\s -> s == s) :: [Char] -> Bool)
OK, passed 100 tests.
```Or this one
[http://www.haskell.org/haskellwiki/How_to_write_a_Haskell_program#Add_some_automated_testing:_QuickCheck](http://www.haskell.org/haskellwiki/How_to_write_a_Haskell_program#Add_some_automated_testing:_QuickCheck)

```
$ cat Test.hs 
``````
import Char
import List
import Test.QuickCheck
import Text.Printf
 
main  = mapM_ (\(s,a) -> printf "%-25s: " s >> a) tests
 
instance Arbitrary Char where
    arbitrary     = choose ('\0', '\128')
    coarbitrary c = variant (ord c `rem` 4)

prop_reversereverse s = (reverse . reverse) s == id s
    where _ = s :: [Int]
 
-- and add this to the tests list
tests  = [("reverse.reverse/id", test prop_reversereverse)]
``````
$ runhaskell Test.hs 
reverse.reverse/id       : OK, passed 100 tests.

```

---

### Post by william2011 on 2011-11-11
```

import Test.QuickCheck.Function
import Test.QuickCheck.Gen

promote :: (a -> Gen b) -> (Gen (a->b))
promote f = Gen (\n r -> 
\a -> m n r where Gen m = f a)

class Coarbitrary a where
coarbitrary :: a -> (Gen b -> Gen b)

instance (Coarbitrary a, Arbitrary b) => Arbitrary (a -> b) where
arbitrary = promote (a -> coarbitrary a arbitrary)

variant :: Int -> Gen a -> Gen a
variant v (Gen m) = Gen (\n r -> m n (rands r !! (v+1)))
where rands r0 = r1 : rands r2
where (r1, r2) = Random.split r0

instance Coarbitrary Bool where
coarbitrary b = if b then variant 0 else variant 1

instance Arbitrary Int where
arbitrary = sized $ \n -> choose (-n,n)
coarbitrary n = variant (if n >= 0 then 2*n else 2*(-n) + 1)

instance (Coarbitrary a, Coarbitrary b)
=> Coarbitrary (a, b) where
coarbitrary (a, b) = coarbitrary a . coarbitrary b

instance Coarbitrary a => Coarbitrary [a] where
coarbitrary []
= variant 0
coarbitrary (a:as) = coarbitrary a . variant 1 . coarbitrary

main :: IO ()
main = QuickCheck promote

```

---

