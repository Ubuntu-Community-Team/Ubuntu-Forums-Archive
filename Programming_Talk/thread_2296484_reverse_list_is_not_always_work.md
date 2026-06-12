---
title: "reverse list is not always work"
date: 2015-09-26
forum: Programming Talk
---

### Post by zerop2 on 2015-09-26
There is no difference between using rev and not use rev

*Main> rev mm!!1
["[1,2,3]","head"]
*Main> mm!!1
["[1,2,3]","head"]

goal is to design a syntax which can run no matter how the statement split



reference from 
[http://stackoverflow.com/questions/17893710/haskell-reverse-function](http://stackoverflow.com/questions/17893710/haskell-reverse-function)

choose n list = concatMap permutations $ choose' list [] where
 choose' []     r = if length r == n then [r] else []
 choose' (x:xs) r | length r == n = [r]
                  | otherwise     = choose' xs (x:r) 
                                  ++ choose' xs r


nondec :: Ord a => [a] -> Bool
nondec xs = and (map leq (zip xs (tail xs)))
            where leq (x, y) = x <= y


foo xs = [(length xs-1), (length xs -2)..0]
rev xs = [xs !! k| k <- foo xs]


let aa = splitOn " " "head tail [1,2,3]"
let mm = filter nondec (choose (length aa -1) $ aa)

---

