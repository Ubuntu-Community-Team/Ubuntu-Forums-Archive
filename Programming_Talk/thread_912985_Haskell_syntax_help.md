---
title: "Haskell syntax help?"
date: 2008-09-07
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-09-07
so i decided to pick up a functional language (still deciding between OCaml and Haskell) for making a parser like i was advised in my C++ Math Help thread

i though a good way to decide would be to do Programming Challenge 5 in each language (this is probably an illogical and irrational way but its how ill get an idea on whose syntax i like better)

so to start i just want to build the random number generator heres the code

[PHP]import System.Random

main =
 do r <- randomRIO (1,100 :: Int)
    print (r + 1 :: Int)[/PHP]

i get a syntax error about my do statement...but i cant figure out what im doing wrong??

edit: i figuered out how to generate the random number but i would like to know what the syntax error here is

---

### Post by rogeriopvl on 2008-09-07
Maybe this book helps you out:

[http://book.realworldhaskell.org/read/](http://book.realworldhaskell.org/read/)

---

### Post by Jessehk on 2008-09-07
Haskell is whitespace sensitive. What that means is that you have to have a consistent indenting style composed of either tabs or spaces. If you mix them or if the code is improperly formatted, you can get syntax errors. When I typed your example in to a Haskell-aware editor (like haskell-mode for Emacs), I got no such error.

---

### Post by jimi_hendrix on 2008-09-07
thanks...maybe i should use emacs instead of gedit but i never figuered out how to do anything other then split windows and move my pointer around really quicly

---

### Post by jimi_hendrix on 2008-09-07
one more problem...it says im doing something wrong with input on my checkAnswer method...but i cant figure out what

[PHP]module Main
	where

import System.Random
import IO

main = do
	hSetBuffering stdin LineBuffering  putStrLn "what is the highest number you want the answer to be?"
	cap <- getLine
	x <- randomRIO (1, read cap :: Int)
	checkAnswer x

checkAnswer answer = do
	putStrLn "what is your guess?"
	guess <- getLine
	if read guess > answer
		then do putStrLn "Too High"
		checkAnswer answer
	else if read guess < answer
		then do putStrLn"Too Low"
		checkAnswer answer
	else do putStrLn "You got it!"[/PHP]

---

### Post by CptPicard on 2008-09-07
Hmm... you know... I really am not all that sure that you want to learn parsing while learning Haskell *and* its monads which you're running into already in that random number generator example. Combinator parsers also make use of monads AFAIK, and it's one of those things that I for example still haven't really grasped yet. :)

A recursive descent parser is easy enough to implement in a more traditional language that you are more familiar with...

---

### Post by jimi_hendrix on 2008-09-07
*sigh*
do you know if OCaml is any better?

in the last few posts of the C++ Math Help thread i had i was refered to functional languages for this

and it seems that if i learn a functional language i can make a parser with less code

see [here]("http://en.wikipedia.org/wiki/Recursive_descent#Implementation_in_functional_languages")

---

### Post by CptPicard on 2008-09-07
> **jimi_hendrix said:**
> 
do you know if OCaml is any better?

If you want an honest opinion, you should just learn how *the recursive descent parser works* and implement it in any language you feel comfortable and most productive in.

To jump around languages in the hope that they would make the algorithm itself more understandable or whatever is in vain.

> 
in the last few posts of the C++ Math Help thread i had i was refered to functional languages for this

IMO they were getting ahead of themselves in your case although the basic idea is perhaps OK.

> 
and it seems that if i learn a functional language i can make a parser with less code

Sure, in terms of conciseness, but you have to learn the functional way of thinking about things in the process...

---

### Post by mssever on 2008-09-07
As a follow-on to what CptPicard just said, you seem to jump between languages before you really learn one. I think you need to pick a language and learn it well. After that, you'll be in a better position to start learning other languages.

---

### Post by jimi_hendrix on 2008-09-07
i also have a nice pdf file that will tell me how to parse a language in haskell

but you're probably like

i like the language of haskell though the code for the guessing game that i have up there will meet all the requirements in probably less then half the lines of my C++ version

---

### Post by CptPicard on 2008-09-07
And when you get the abstract syntax tree by following that pdf, what then? Do you know Haskell well enough to write an evaluator function?

---

### Post by jimi_hendrix on 2008-09-07
tell me what one is and i will tell you if i do :)

---

### Post by CptPicard on 2008-09-07
Right... :rolleyes:

;)

---

### Post by mssever on 2008-09-07
> **jimi_hendrix said:**
> tell me what one is and i will tell you if i do :)
The point is, you're in over your head. Tutorials can be useful, but only if you discipline yourself to understand the *why*'s behind what they're doing. That task is easier if the tutorial writer explains everything well. Unfortunately, many tutorials authors don't.

---

### Post by jimi_hendrix on 2008-09-07
no really tell me

---

### Post by CptPicard on 2008-09-07
If your long term goal is writing your own language, which is a nontrivial exercise in itself... in a typical language interpreter, there are two parts -- language parser that parses the source into internal representation, and then the evaluator function that walks the resulting syntax tree and does whatever the language is supposed to do.

In Haskell in particular you'll be fighting the pure-functionality of the language, and I have the feeling that in your own language you would assume the ability to have mutable state. My own feeling is that implementing a language with side-effects in Haskell probably requires the usage of some kind of state-transformation monads, which are a tough topic... to be honest I couldn't explain them to you yet if I tried, so I have this hunch that you just may not be able to handle them either :)

---

### Post by Alasdair on 2008-09-07
[Here]("http://www.defmacro.org/ramblings/lisp-in-haskell.html") is a decent tutorial that covers writing a simple interpreter for a lisp like language. It doesn't assume a very high knowledge of Haskell - I found it easy enough to follow, plus the author shows what some of the code would look like in Java (mostly to mock Java, but you may find it helpful). There is another Haskell tutorial called 'make yourself a scheme in 48 hours' that is probably quite similar, but I haven't read it. And of course for writing a language, you will want to get familiar with [Parsec]("http://legacy.cs.uu.nl/daan/download/parsec/parsec.html"). However you would probably be best starting of on something small and simple while you are still learning the basics of Haskell and pure functional programming.

---

### Post by jimi_hendrix on 2008-09-07
*shrug*

i like the language haskell anyway and will continue to look into it

---

### Post by CptPicard on 2008-09-07
Mind you, I am not saying that you shouldn't -- I am a fan of functional programming myself -- but just suggesting that learning two things at once is not necessarily the most efficient path to take... :)

---

### Post by Kadrus on 2008-09-07
Well I do not want to sound negative or any of this sort..But it seems like you're only learning programming to implement a language(weird,eh).And you are considerably a beginner(from your posts)trying to switch from one language to another without  **knowing one**,and this is not a good thing,because along the way,you will not learn a language well,instead you will move from one to another thinking that it might **do the job** for you.
> do you know if OCaml is any better?
Well you cannot compare Haskell to OCaml,like a replacement for it.
You can say OCaml vs SML or OCaml vs Alice ML or OCaml vs Scala or OCaml vs F#.
Haskell is a purely functional programming languages that differs from OCaml.
It's true that they are both functional languages,but Haskell is purely functional and modular language while OCaml is a functional language that has Object Orientation.

---

### Post by jimi_hendrix on 2008-09-07
> **Kadrus said:**
> Well I do not want to sound negative or any of this sort..But it seems like you're only learning programming to implement a language(weird,eh).And you are considerably a beginner(from your posts)trying to switch from one language to another without  **knowing one**,and this is not a good thing,because along the way,you will not learn a language well,instead you will move from one to another thinking that it might **do the job** for you.


yes i have the bad habit of jumping into something head first when i enjoy it...also i likke exploring the different languages

> 
Well you cannot compare Haskell to OCaml,like a replacement for it.
You can say OCaml vs SML or OCaml vs Alice ML or OCaml vs Scala or OCaml vs F#.
Haskell is a purely functional programming languages that differs from OCaml.
It's true that they are both functional languages,but Haskell is purely functional and modular language while OCaml is a functional language that has Object Orientation.

thanks for the clearification

---

