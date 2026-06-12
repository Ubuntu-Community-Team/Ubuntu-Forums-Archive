---
title: "Haskell question--handling EOF in interactive program"
date: 2011-07-03
forum: Programming Talk
---

### Post by ceclauson on 2011-07-03
Hello, I'm new to Haskell, and would like to try to use it to process files (i.e., tasks similar to something that might be done in awk).  Specifically, I'd like it to process text from an input file until it reaches EOF printing output at appropriate times, and maintain state as it does it.

Here's my stab at a program that does this kind of thing:
[PHP]
--simple interactive program with state, takes
--user input string, appends it to current state
--string, and prints the state string
--state string grows as program is run

main :: IO ()
main = helper("") --initial state is empty string

helper :: String -> IO ()
helper initialState = do
       linein <- getLine
       putStrLn(snd (transition (linein, initialState)))
       helper(fst (transition (linein, initialState)))

--pure function to implement logic--translates
--input and current state to next state and
--output
transition :: (String, String) -> (String, String)
transition inpair = (nextState, nextState) where nextState = (snd inpair) ++ (fst inpair)

[/PHP]

The only problem with this is that at the end of the input file, it prints the error message:

```

interact.hs: <stdin>: hGetLine: end of file

```

I figure I could eliminate this message by checking for EOF, but I'm not sure how to do this.  Does anyone know of a simple way to do this?

Thanks in advance

---

### Post by Bachstelze on 2011-07-03
isEOF :)

[php]--simple interactive program with state, takes
--user input string, appends it to current state
--string, and prints the state string
--state string grows as program is run

import System.IO

main :: IO ()
main = helper("") --initial state is empty string

helper :: String -> IO ()
helper initialState = do end <- isEOF
                         if end
                             then putStr ""
                             else do linein <- getLine
                                     putStrLn(snd (transition (linein, initialState)))
                                     helper(fst (transition (linein, initialState)))

--pure function to implement logic--translates
--input and current state to next state and
--output
transition :: (String, String) -> (String, String)
transition inpair = (nextState, nextState) where nextState = (snd inpair) ++ (fst inpair)  
[/php]

---

### Post by ceclauson on 2011-07-03
Perfect.  Thanks!

---

