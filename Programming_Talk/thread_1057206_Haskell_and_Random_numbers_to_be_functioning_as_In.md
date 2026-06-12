---
title: "Haskell and Random numbers to be functioning as Int's"
date: 2009-02-01
forum: Programming Talk
---

### Post by amityak on 2009-02-01
Hello Everyone!

So, as a part of homework assignment I have to simulate 'noise' which will randomally flip some bits over a stream, given a stream and noise rate (in precentage)

My strategy is following:

1. Using random numbers to create a list (of position) of the bits needs to be 'flipped'. something that would work to example like that

```
ranPOS 10 4 = [3,8,3,6] 
```

where 10 is the top limit (length of my bit stream) and 4 is the number of interferences i want (here is 4/10 = 40%)

so I wrote something like that:

```
ranPOS :: Int -> Int -> [Int]
ranPOS n top | n > top = error "not enough numbers fora unique list"
             | otherwise = rP [] n top

rP :: [Int] -> Int -> Int -> [Int]
rP list n top   |length list == n = list
                |(elem m list) == False = rP (m:list) n top
                |otherwise = rP list n top
                         where m = getStdRandom (randomR (1,n))
```

ofcourse this is not working because of the IO Int type, i just got to know. Can anyone tell me how could i make this work ??

I read about the unsafe function but couldnt make it work either, how do I do that, and if I shouldn't, what are the alternatives??

Thank you all

Amit from Berlin

---

