---
title: "functional programming in Haskell"
date: 2011-06-08
forum: Programming Talk
---

### Post by manish411 on 2011-06-08
I have started functional programming in Haskell and I need a mentor 
to clear some basic doubts. Plz someone help me!!

---

### Post by simeon87 on 2011-06-08
Could you post your questions here? That's usually easier than asking for a mentor. I know that several people here know Haskell (including me, to some extent).

---

### Post by manish411 on 2011-06-08
I am writing a basic functions which calculates ave of marks given in a list
<code>
percent a =
        let sum = addition a
            per = fromIntegral sum/fromIntegral $ length a
        in per
</code>

but I am getting an error

  No instance for (Fractional (Int -> b))
      arising from a use of `percent' at <interactive>:1:0-17
    Possible fix:
      add an instance declaration for (Fractional (Int -> b))
    In the expression: percent [23, 44, 55]
    In the definition of `it': it = percent [23, 44, 55]

---

### Post by simeon87 on 2011-06-08
Not sure what's going on there but it looks like you're giving a function where a number is expected. Can you try:

```
fromIntegral sum / fromIntegral (length a)
```

I must say it has been a while since I did Haskell.

---

### Post by manish411 on 2011-06-08
thanks it worked,but what was the problem??

---

### Post by simeon87 on 2011-06-08
The problem is:

```
fromIntegral sum/fromIntegral $ length a
```

It's wrong to have a $ in that location, it messes up the types. You can use $ to correctly do function composition, such as:

```
funcOne.funcTwo.funcThree $ arg
```

This will cause Haskell to do the function composition first (combine funcOne, funcTwo and funcThree into one function) and then apply that combined function to arg. That's what I know about using $. In your case you have

```
fromIntegral sum / fromIntegral
```

on the left side which is weird because you can't divide by a function (which is what Haskell will try to do due to the $).

---

### Post by manish411 on 2011-06-09
Now I want to modify the code and want to include IO actions
```
 
percent a =
        let sum = addition a
            per = fromIntegral sum /fromIntegral (length a)
        in per

main = do
       putStrLn " Enter the marks in a list"
       marks <- getLine
       print $ percent fromIntegral $ marks


```

However the getLine function is the functions which binds the input which is of type String
There are different functions for taking input of different types .
What if we want an input of a type which is of Int, a list , an algebraic data type?

---

### Post by simeon87 on 2011-06-09
What you'll get from getLine is a String. That means you'll need to convert it to a different data type yourself with a parser.

---

### Post by schauerlich on 2011-06-09
Please use [noparse][code][/noparse] tags when you post code (those are square brackets, not angle brackets).

---

### Post by manish411 on 2011-06-09
This wont work either:
```



addition x:xs
       | x ==[] = 0
       | otherwise = x + addition xs

--percent :: [Int] -> Float

percent a =
        let sum = addition a
            per = fromIntegral sum /fromIntegral (length a)
        in per

main = do
       putStrLn " Enter the marks in a list"
       marks <- getLine
       let mark = (read marks :: [Int])
       print $ percent mark


```error
Prelude> :load functions.hs
[1 of 1] Compiling Main             ( functions.hs, interpreted )

functions.hs:1:0: Parse error in pattern
Failed, modules loaded: none.

---

### Post by schauerlich on 2011-06-09
> **manish411 said:**
> ```

addition x:xs
       | x ==[] = 0
       | otherwise = x + addition xs

--percent :: [Int] -> Float

percent a =
        let sum = addition a
            per = fromIntegral sum /fromIntegral (length a)
        in per

main = do
       putStrLn " Enter the marks in a list"
       marks <- getLine
       let mark = (read marks :: [Int])
       print $ percent fromIntegral $ mark


```

You need parentheses around the [noparse](x:xs)[/noparse] when it's in a pattern match, that's why it fails. In [noparse](x:xs) :: [a][/noparse], x must be of type a, and xs must be of type [a]. You try to compare x, which is some integer, to the empty list. You want something like this:

```
addition :: (Num a) => [a] -> a
addition [] = 0
addition (x:xs) = x + (addition xs)
```

---

