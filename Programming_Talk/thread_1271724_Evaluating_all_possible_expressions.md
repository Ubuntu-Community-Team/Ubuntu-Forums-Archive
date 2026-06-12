---
title: "Evaluating all possible expressions"
date: 2009-09-21
forum: Programming Talk
---

### Post by Nevon on 2009-09-21
I need some help with a problem I've encountered in a semi-educational game that I'm making in Lua using [Löve](http://love2d.org). The basic object of the game is to create as large a difference between two sums as possible, by positioning 6 given numbers in various places relative to 4 operators. To show you what I mean, here's a rough visualization:
[img]http://i33.tinypic.com/igkpp0.png[/img]

The operators are all distributed randomly, and the user can then place the numbers freely in the colored boxes. The three numbers on the left (together with the two operators on the left) form one expression, and the ones on the right form another. Once all numbers have been placed, the two expressions should be evaluated to see if it creates the largest inequality possible.

So basically, this is the objective of the game:
```
num[1] operator[1] num[2] operator[2] num[3] = sum[1]
num[4] operator[3] num[5] operator[4] num[6] = sum[2]

if sum[1] > sum[2] then
    difference = sum[1] - sum[2]
else
    difference = sum[2] - sum[1]
end

if difference == LARGEST_POSSIBLE_DIFFERENCE then
    print "Winner!"
end
```

To do this, I assume the program would have to evaluate all possible configurations of the numbers and find the largest one. If the player's configuration evaluates to that value, he or she has won.

What I don't know is how to evaluate all possible configurations, and as such, that is what I would very much appreciate it if you could help me with. :) 

Thank you, and please let me know if you have any questions.

---

### Post by MadCow108 on 2009-09-21
the simple but slow way would be to to permutate your numbers:
[http://www.lua.org/pil/9.3.html](http://www.lua.org/pil/9.3.html)
maybe there's are builtin function in lua to do that.

a faster way would be to calculate from the operators which is the highest possible combination but this, depending on the complecity of your operator combinations (parantheses allowed? etc), may need a bit of thinking

---

### Post by Nevon on 2009-09-21
> **MadCow108 said:**
> the simple but slow way would be to to permutate your numbers:
[http://www.lua.org/pil/9.3.html](http://www.lua.org/pil/9.3.html)
maybe there's are builtin function in lua to do that.

a faster way would be to calculate from the operators which is the highest possible combination but this, depending on the complecity of your operator combinations (parantheses allowed? etc), may need a bit of thinking

I'm not sure how fast Lua is, but with 720 possible combinations for each set of six numbers, it doesn't seem like a brute force approach would be all that bad. However, I wouldn't say it's simple to do so. Me and a math-geek friend of mine had a pow-wow yesterday, but were unable to come up with a complete solution - hence, I'm asking you. 

I asked another guy as well, and he did give me an example of what the solution could look like. However, it was all done in Haskell, so of course it was utterly unreadable. :P

```
import Data.List (permutations)
import System.Random (randomR, newStdGen)

main = do g <- newStdGen
          putStrLn $ (show . values) g
          putStrLn $ (show . largestDiff . values) g

values g = snd $ foldl f (g, []) [1..6] :: [Int]
    where f (g, l) x = let (n,g') = randomR (0,100) g in (g', n:l)

ops = [(+), div, (*), (-)]

largestDiff = foldl each (0, []) . permutations :: [Int] -> (Int, [Int]) where
    (o0,o1,o2,o3) = (ops !! 0, ops !! 1, ops !! 2, ops !! 3)
    each (old, l) x = case   abs(  ((x!!0) `o0` (x!!1) `o1` (x!!2))
                                 - ((x!!3) `o2` (x!!4) `o3` (x!!5))) of
                        new | new > old -> (new, x)
                        _               -> (old, l)
```

---

