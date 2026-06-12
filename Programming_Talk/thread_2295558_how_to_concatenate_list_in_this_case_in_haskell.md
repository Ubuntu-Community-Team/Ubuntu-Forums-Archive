---
title: "how to concatenate list in this case in haskell"
date: 2015-09-19
forum: Programming Talk
---

### Post by zerop2 on 2015-09-19
[B]update 3

```

[/B][COLOR=#666666][FONT=Segoe UI]let aa = splitOn " " "I marry yanki"
let bb = filter (not . null) aa 
let cc = Data.Map.fromList $ zip [1..(length bb)] bb
forM_ [1..(length bb)] $ \i -> putStr $ (cc Data.Map.! i) ++ " "
let bb = [1,2,3]
let dd = filter nondec . choose (length bb -1) $ bb
[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]forM_ [0..(length bb -1)] $ \i -> forM_ [0..(length dd!!i -1)] $ \j -> putStr $ (cc Data.Map.! dd!!i!!j) ++ " "[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]i understand the errors but i do not admit above line having error, where is wrong?[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]<interactive>:58:46:[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    Couldn't match expected type &#8216;[Int]&#8217; with actual type &#8216;Int&#8217;[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    In the first argument of &#8216;(!!)&#8217;, namely &#8216;length dd&#8217;[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    In the first argument of &#8216;(-)&#8217;, namely &#8216;length dd !! i&#8217;[/FONT][/COLOR]

[COLOR=#666666][FONT=Segoe UI]<interactive>:58:82:[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    Couldn't match type &#8216;Char&#8217; with &#8216;[[Char]]&#8217;[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    Expected type: containers-0.5.6.2:Data.Map.Base.Map Int [[[Char]]][/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]      Actual type: containers-0.5.6.2:Data.Map.Base.Map Int [Char][/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    In the first argument of &#8216;(containers-0.5.6.2:Data.Map.Base.!)&#8217;, namely[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]      &#8216;cc&#8217;[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    In the first argument of &#8216;(!!)&#8217;, namely[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]      &#8216;cc containers-0.5.6.2:Data.Map.Base.! dd&#8217;[/FONT][/COLOR]

[COLOR=#666666][FONT=Segoe UI]<interactive>:58:96:[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    Couldn't match expected type &#8216;Int&#8217; with actual type &#8216;[[Integer]]&#8217;[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    In the second argument of &#8216;(containers-0.5.6.2:Data.Map.Base.!)&#8217;, namely[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]      &#8216;dd&#8217;[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]    In the first argument of &#8216;(!!)&#8217;, namely[/FONT][/COLOR]
[COLOR=#666666][FONT=Segoe UI]      &#8216;cc containers-0.5.6.2:Data.Map.Base.! dd&#8217;
[/FONT][/COLOR][B]
```

update 2

[/B]let xs = [2,3,4]
let ys = []
do {ys <- ys:(filter nondec (choose 2 xs)); return ys}

this works

but after using mapM_ and forM_, not work

mapM_ (\ i -> do {ys <- ys:(filter nondec (choose i xs)); return ys}) [1, 2, 3]


do {mapM_ (\ i -> do {ys <- ys ++ (filter nondec (choose i [2,3,4])); return ys}) [1, 2];}
do {mapM_ (\ i -> do {zs <- do {ys <- ys ++ (filter nondec (choose i [2,3,4])); return ys}; return zs}) [1, 2];}




let hello ys xs = do {xx <- forM_ [1..(length xs -1)] $ \i -> do {ys <- ys:(filter nondec (choose i xs)); return ys}; return xx}
hello [] [2,3,4]




[B]
update
[/B]
filter nondec . choose 2 $ ["I","have","dinner"]


i have       ---- [1,2]
have dinner  ---- [2,3]


*Main> filter nondec . choose 2 $ ["I","have","dinner"]
[["I","have"],["I","dinner"],["dinner","have"]]

how to output the original order after filter with nondec, such ["have", "dinner"]


**Original question**




method 1 and method 2 and method 3 still can not return normal result

for clear version, please read
[https://gist.github.com/anonymous/7cf197e49d6a6ce4a48d](https://gist.github.com/anonymous/7cf197e49d6a6ce4a48d)


choose n list = concatMap permutations $ choose' list [] where
 choose' []     r = if length r == n then [r] else []
 choose' (x:xs) r | length r == n = [r]
                  | otherwise     = choose' xs (x:r) 
                                  ++ choose' xs r


nondec :: Ord a => [a] -> Bool
nondec xs = and (map leq (zip xs (tail xs)))
            where leq (x, y) = x <= y

Method 1


let hello ys xs = forM_ [1..length xs] $ \i -> ys:(filter nondec . choose i $ xs)
hello [] [2,3,4]

[(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),(),()]

Method 2

hello 0 ys xs = []
hello n ys xs = ys:(filter nondec . choose n-1 $ xs)

*Main Data.List> hello 2 [] [2,3,4]


<interactive>:288:1:
    No instance for (Num ([a0] -> [[a0]]))
      (maybe you haven't applied enough arguments to a function?)
      arising from a use of &#8216;it&#8217;
    In the first argument of &#8216;print&#8217;, namely &#8216;it&#8217;
    In a stmt of an interactive GHCi command: print it


Method 3

*Main Data.List> mapM_ (\ i -> filter nondec . choose i $ [2,3,4]) [1, 2, 3]
[(),(),(),(),(),(),(),(),()]

---

