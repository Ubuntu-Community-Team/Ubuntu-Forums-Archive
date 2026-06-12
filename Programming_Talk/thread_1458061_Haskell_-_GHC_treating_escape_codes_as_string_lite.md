---
title: "Haskell - GHC treating escape codes as string literals"
date: 2010-04-19
forum: Programming Talk
---

### Post by Drone022 on 2010-04-19
Hey,

For some reason if, for example, I have a function like this:
```
onThreeLines :: String -> String -> String -> String
onThreeLines x y z = x ++ "\n" ++ y ++ "\n" ++ z
```

The output is this :
```
onThreeLines "one" "two" "three"

"one\ntwo\nthree"
```

Am I doing something totally stupid? I probably am but I can't spot it. I checked my slashes were the right way round this time aswell.

---

### Post by Drone022 on 2010-04-19
Look like in order to get his simple exercise to work I have to do this :

```
onThreeLines :: String -> String -> String -> IO()
onThreeLines x y z = putStrLn $ x ++ "\n" ++ y ++ "\n" ++ z
```

Anyone tried it the first way in HUGS?

---

### Post by Drone022 on 2010-04-19
Nevermind, I was being an idiot.

I just had to put 
```
putStr( onThreeLines "one" "two" "three")
```
in the interpreter.

Doh.

---

