---
title: "[Beginner] Programming Challenge: 6"
date: 2008-09-24
forum: Programming Talk
---

### Post by LaRoza on 2008-09-24
Sorry for the delay, but you get what you pay for :-)

This new challenge with be something special. I decided to not go with the algorithm suggestions I have been getting and try something new (yet not hard).

Hopefully, you will learn something.

[size=+1]The Challenge[/size]
Do any of the [previous challenges](http://ubuntuforums.org/showpost.php?p=5499486&postcount=1), but in Scheme, Common Lisp, or Haskell. If you know one of those languages, you can use it, but I prefer one uses a new language.

[size=+1]The Reasons[/size]
The other challanges weren't hard. In particular, the first and second ones would be ideal candidates for this. The whole point of this is to expose new programmers to another syntax. C syntax will show its true colours; BASIC syntax will be revealed for the monstrosity that it is.

My wiki would be a good place to learn the basics of these languages. Scheme would be the simplist. 

[size=+1]How it will be graded[/size]
It won't be. You'll get feedback (hopefully) from those who can give it. You should focus on learning and trying to use new concepts.

---

### Post by Reiger on 2008-09-24
It might be a good idea to link to the (older) Beginner Challenges. Some of them got a couple of pages behind, I think. ;)

---

### Post by LaRoza on 2008-09-24
> **Reiger said:**
> It might be a good idea to link to the (older) Beginner Challenges. Some of them got a couple of pages behind, I think. ;)

Index link: [http://ubuntuforums.org/showpost.php?p=5499486&postcount=1](http://ubuntuforums.org/showpost.php?p=5499486&postcount=1)

---

### Post by slavik on 2008-09-24
is Perl6 allowed?

---

### Post by MacUntu on 2008-09-24
Never used or liked Lisp, so I did challenge 1 with Lisp:

```
(defun drink (n)
  (loop for i from n downto 1 do 
    (if (>= i 2)
      (format t "~a bottles of beer on the wall, ~a bottles of beer.~%~
        Take one down and pass it around, ~a ~a of beer on the wall.~%~%" i i (- i 1) (format nil "bottle~p" (- i 1)))
      (format t "~a bottle of beer on the wall, ~a bottle of beer.~%~
        Take one down and pass it around, no more bottles of beer on the wall~%~%~
        No more bottles of beer on the wall, no more bottles of beer.~%~
        Go to the store and buy some more, ~a bottles of beer on the wall." i i n))))
```

I tried a recursive version but it looked bad compared to the above.

---

### Post by jimi_hendrix on 2008-09-24
was already working on this...awesome idea

---

### Post by jimi_hendrix on 2008-09-25
are we aloud other functional languages like OCaml or other non C like syntax languages like assembler?

---

### Post by SteelDragon on 2008-09-25
I don't even know what any of those are. This should prove to be very informative.

---

### Post by LaRoza on 2008-09-26
> **slavik said:**
> is Perl6 allowed?

```

if "Perl6" in ("Scheme", "Common Lisp", "Haskell"):
    print "Yes"
else:
    print "Get some sleep and realise how silly that question is"

```

> **SteelDragon said:**
> I don't even know what any of those are. This should prove to be very informative.

Yes, it should be informative :-)

Eric Raymond in "How to Become a Hacker":
[quote=ESR]
Lisp is worth learning for the profound enlightenment experience you will have when you finally get it; that experience will make you a better programmer for the rest of your days, even if you never actually use Lisp itself a lot.
[/quote]

---

### Post by Reiger on 2008-09-26
Yes, well that can be said about Haskell also. ;)

---

### Post by LaRoza on 2008-09-26
> **Reiger said:**
> Yes, well that can be said for Haskell also. ;)

Not quite, but Haskell is a pure functional language (Lisp isn't), so I included it.

---

### Post by slavik on 2008-09-26
> **LaRoza said:**
> ```

if "Perl6" in ("Scheme", "Common Lisp", "Haskell"):
    print "Yes"
else:
    print "Get some sleep and realise how silly that question is"

```



Yes, it should be informative :-)

Eric Raymond in "How to Become a Hacker":
pugs is a perl6 interpreter written in haskell, so technically, I would be writing haskell code. :)

---

### Post by nvteighen on 2008-09-26
IIRC I did one of the challenges in Scheme...

---

### Post by LaRoza on 2008-09-26
> **slavik said:**
> pugs is a perl6 interpreter written in haskell, so technically, I would be writing haskell code. :)

So writing Python code is writing C code? C is translated into GAS, but that doesn't count for writing assembly code. IronPython is written in C#, Jython in Java, therefore, writing Python is writing C#, C and Java at the same time.

Maybe you need some sleep? ;)

> **nvteighen said:**
> IIRC I did one of the challenges in Scheme...

You aren't a beginner, and anyone copying your submission will be forced to write Java code.

---

### Post by jimi_hendrix on 2008-09-26
im am assuming i cannot use assembler like i asked and that it was a stupid question too :)

but is OCaml valid?

---

### Post by LaRoza on 2008-09-26
> **jimi_hendrix said:**
> 
but is OCaml valid?

If you give instructions on how to use it and it is available in the standard Ubuntu repos.

---

### Post by Kadrus on 2008-09-26
> but is OCaml valid?
It can be considered valid if you do not use an imperative style,and if you use tail recursion.

---

### Post by NovaAesa on 2008-09-27
I only started learning scheme about half an hour ago, but here is my attempt that I have come up with in that time. Constructive criticism is required, as I'm sure I have done a few silly things in there.

```

;99 bottles of beer song in Scheme

(begin
  (define beer
    (lambda (bottlesLeft)
      (if (>= bottlesLeft 1)
        (begin
          (display bottlesLeft)
          (display " bottle(s) of beer on the wall, ")
          (display bottlesLeft)
          (display " bottle(s) of beer, take one down, pass it around, ")
          (display (- bottlesLeft 1))
          (display " bottle(s) of beer on the wall.")
          (newline)
          (newline)
          (beer (- bottlesLeft 1)))
        (begin
          (display "Go to the store, buy some more, lots of ")
          (display "bottles of beer on the wall")))))
  (beer 100))
```

---

### Post by nvteighen on 2008-09-27
> **LaRoza said:**
> 
You aren't a beginner, and anyone copying your submission will be forced to write Java code.

Hmm... I really would like to see it translated into Java... :D ([http://ubuntuforums.org/showthread.php?p=5688998#post5688998](http://ubuntuforums.org/showthread.php?p=5688998#post5688998))

---

### Post by nvteighen on 2008-09-27
> **NovaAesa said:**
> I only started learning scheme about half an hour ago, but here is my attempt that I have come up with in that time. Constructive criticism is required, as I'm sure I have done a few silly things in there.

```

;99 bottles of beer song in Scheme

(begin
  (define beer
    (lambda (bottlesLeft)
      (if (>= bottlesLeft 1)
        (begin
          (display bottlesLeft)
          (display " bottle(s) of beer on the wall, ")
          (display bottlesLeft)
          (display " bottle(s) of beer, take one down, pass it around, ")
          (display (- bottlesLeft 1))
          (display " bottle(s) of beer on the wall.")
          (newline)
          (newline)
          (beer (- bottlesLeft 1)))
        (begin
          (display "Go to the store, buy some more, lots of ")
          (display "bottles of beer on the wall")))))
  (beer 100))
```

OK, let's see; it is good, but not too "Schemic".

0. (define xx (lambda (yy) ...)) is usually shorthanded as (define (xx yy) (...)). Tutorials emphasize the first form to make you see that code = data, and that defining a function is just give a name to a lambda. But once you know that, you can use the syntactic sugar form, which is more widespread.

1. In MIT/GNU Scheme, there's an procedure called (format) that allows you to print formatted output. Look at your implementation's documentation if there's something like that available for you.

2. (begin) is evil. First, it breaks functional programming, as the return value of a (begin ...) is undefined; also, because usually it's a sign that your code should be broken into procedures. Of course, sometimes it simplifies stuff, but at the costs described above. Also, notice that the first (begin) is unnecessary: your interpreter will execute sequentially whatever you give to it... be it 100 procedures or a single one.

3. Now, a philosophical observation. When developing in Lisp, you usually just define procedures that afterwards are executed by a user in the interpreter... in other words, in Lisp you program by creating a new language built "on Lisp" (in contrast to "built in Lisp") and therefore, it transforms itself into a new Lisp dialect specific to your task (Do you want to write a programming language? With Lisp, just do it!). And the Lisp interpreter you use will "automagically" be an interpreter for your language, and also the interface where the user, using your language, can perform some task (or write a script for it).

Of course, as you've experienced, Lisp also allows you to write stuff in a "conventional way"... Notice that Lisp's power is not related with functional programming, but to the "code = data = code" principle.

I *highly* recommend you to watch the MIT SICP videos at: [http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/) And, of course, also look at the book (it's available free in the web). Even if the videos were recorded in 1986, they're pretty good to learn Scheme (and also some other CompSci cool stuff).

---

### Post by maximinus_uk on 2008-09-27
Writing in Scheme or Lisp isn't a challenge... it's a bonus.

Now, writing all those bits of code in brainfuck... that would be a programing challenge!

---

### Post by LaRoza on 2008-09-27
> **maximinus_uk said:**
> Writing in Scheme or Lisp isn't a challenge... it's a bonus.

Now, writing all those bits of code in brainfuck... that would be a programing challenge!

Brainfuck isn't hard. It is TDS, but not hard.

---

### Post by SteelDragon on 2008-09-28
OK then. I take it by the dearth of responses that everybody else finds Lisp as confusing as I do. However, since I've spent the whole weekend trying to figure it out, I will submit my first attempt now before Sunday ends (depending where you are). I've gotta say that I had fun with this and I plan to continue learning more scheme, though all the sources I've found say it's only good for learning. Learning is what I want to do:D.

Feedback is desired, encouraged, requested and welcomed. Thanks for the challenge LaRoza, this is something I definitely wouldn't have thought of on my own.

Using PLT Scheme:
```

#lang scheme

(define (part1 n)
   (cond 
     ((not (= n 1)) (string-append (number->string n) " bottles of beer on the wall. "))
     (else "1 more bottle of beer on the wall. ")))

(define (part4 n) (part1 (- n 1)))
  
(define (part2 n)
  (cond 
      ((> n 9) (string-append (substring (part1 n) 0 18) "."))
      ((or (> n 1) (= 0 n)) (string-append (substring (part1 n) 0 17) "."))
      (else "1 more bottle of beer.")))

(define (part3 n)
  (cond
    ((> n 1) "Take one down, pass it around, ")
    ((= n 1) "Take it down, pass it around, ")
    ((= n 0) "Go to the store, buy some more, ")))
  
(define (sing n)
    (when (>= n 0)
      (printf "~a~a ~n ~a~a ~n~n"
              (part1 n)
              (part2 n)
              (part3 n)
              (part4 n))
      (sing (- n 1))))

(sing 99)

```

Edit: And I've already found an error.:rolleyes:

I'll have to fix the procedure (part4 n) so that it prints 99 instead of -1 in the last verse. I'm getting on it now.

---

### Post by jimi_hendrix on 2008-09-28
question to help me with one of the challenges: in scheme does anyone remember the funtion that returns what type a paramter is...i thought it was like (? 1) would return integer...i read about this long ago but i cant find the tutorial now :(

---

### Post by nvteighen on 2008-09-29
> **SteelDragon said:**
> (...) I've gotta say that I had fun with this and I plan to continue learning more scheme, though all the sources I've found say it's only good for learning. Learning is what I want to do:D.

(...)


Ah, you'll be surprised with what you can do with Scheme. Just play some more around.

And congratulations, it's a nice Scheme code. And you clearly have looked at your implementation's features to find your way... That's good.

---

### Post by jimi_hendrix on 2008-09-30
this language isnt in the rules but i think i want to post my answer for answer 1 in a non C/BASIC syntax anyway...

[PHP]9[/PHP]

this answer is written in HQ9+

---

### Post by JupiterV2 on 2008-10-02
**EDIT:

Whoops! I misread the challenge! I thought you were to do the challenge in a language you didn't know LIKE the ones listed (as if they were examples) rather than you MUST use one of the listed languages. My bad!

**END

I am learning how to use Bash scripting. I am VERY much a newbie at it so forgive me! Here is my first attempt at a script that solves Beginner Programming Challenge #2 (which I would have normally solved in either C or C++). I plan on attempting to fix the code using something like sed to qualify if a user has entered a number for their name and a string for an age or uid. The user name causes no error but the uid and age will throw an un-handled exception.

[PHP]#!/bin/sh

# A bash script which takes prompts for a user's name, age, and UID then
# outputs the result in a meaningful manner after qualifying the supplied
# data.

menu_choice=""
username=""
userage=0
userid=0

get_return() {
	printf "Press return"
	read x
	return 0
}

get_confirm() {
	printf "Are you sure? (y/n)"
	while true
	do
		read x
		case "$x" in
			y | yes | Y | Yes | YES )
				return 0;;
			n | no | N | No | NO )
				echo
				echo "Cancelled"
				return 1;;
			*) echo "Sorry, choice not recognized";;
		esac
	done
}

show_menu() {
    echo
    echo
	echo "Options :-"
	echo
	echo "	e) Enter Data"
	echo "	q) Quit"
	echo
	printf "Please enter choice then press return: "
	read menu_choice
	
	return
}

get_username() {
    printf "Please enter your name: "
    read username
    
    if [ "$username" = "" ]; then
        echo "You didn't enter a name!"
        get_username
    fi
    
    return
}

get_userage() {
    printf "Please enter your age: "
    read userage
    
    if [ "$userage" -lt 1 ]; then
        userage=1
    fi
    if [ "$userage" -gt 100 ]; then
        userage=100
    fi
    
    return
}

get_userid() {
    printf "Please enter you user ID (1-999999)"
    read userid
    
    if [ "$userid" -lt 1 ]; then
        userid=1 
    fi
    if [ "$userid" -gt 999999 ]; then
        userid=999999 
    fi
    
    return
}

enter_data() {
    clear
    get_username
    get_userage
    get_userid
    
    if get_confirm ; then
        echo
        echo
        echo "You are $username, aged $userage."
        echo "Next year you will be $(($userage + 1)), with user id $userid. "
        echo "The next user is $(($userid + 1))."
        echo
        get_return
    else
        sleep 1
    fi
}

# application proper (main())

quit=n
while [ "$quit" != "y" ];
do    
    clear
    echo "Ubuntu Challenge 6 Script v0.1!"
    echo
    echo
    echo "Enter your user name, age and ID for some Ubuntu challenge fun!"
    show_menu
	case "$menu_choice" in
	    e | E ) enter_data;;
		q | Q ) quit="y";;
		*) echo "Sorry, choice not recognized";;
	esac
done

echo "Finished!"

exit 0[/PHP]

---

### Post by nvteighen on 2008-10-02
> **jimi_hendrix said:**
> this language isnt in the rules but i think i want to post my answer for answer 1 in a non c/basic syntax anyway...

[php]9[/php]

this answer is written in hq9+
lol!

---

### Post by Kadrus on 2008-10-02
> **jimi_hendrix said:**
> this language isnt in the rules but i think i want to post my answer for answer 1 in a non C/BASIC syntax anyway...

[PHP]9[/PHP]

this answer is written in HQ9+
mm..it would be better to write a code,than to copy one ^^
[http://99-bottles-of-beer.net/language-hq9+-1334.html](http://99-bottles-of-beer.net/language-hq9+-1334.html)

---

### Post by jimi_hendrix on 2008-10-02
> **Kadrus said:**
> mm..it would be better to write a code,than to copy one ^^
[http://99-bottles-of-beer.net/language-hq9+-1334.html](http://99-bottles-of-beer.net/language-hq9+-1334.html)

i could add a few +'s in there...

[PHP]++++++++++++++++++++++++++9++++++++++++++++++++++++++++++++[/PHP]

now its my own code :)

---

### Post by wsonar on 2009-05-08
How can you subscribe to the new challenges that come out so your notified?

---

### Post by wsonar on 2009-05-08
I think I will go through the other's without looking at what everyone else did to get caught up

first one's  pretty easy

---

### Post by jacksaff on 2009-06-10
Late to the party but I'll post 'em anyway.

I found the bottle song hard to do in a 'nice' way. First you have to learn lisp and then you have to learn the language format uses as well. 

```
(defun pre-format (number)
  (if (= 0 number) "no more bottles" (format nil "~r bottle~:p" number)))

(loop :for numbottles :from 99 :downto 0 :do
   (format t "~@(~a~) of beer on the wall, ~:*~a of beer.~%" (pre-format numbottles))
   (if (< 0 numbottles)(format t "Take one down, pass it around, ~a of beer on the wall. ~2%"  (pre-format (1- numbottles)))
       (format t "Go to the store and buy some more, ninety-nine bottles of beer on the wall.~2%")))

```

Can a lisper please tell me how I can use ~r for the numbers except for 0 where I want "no more" instead of "zero"? I got pissed off in the end and used a function outside of format. At least I have all the words of the song typed just once. 
Also couldn't work out how to do the condition for the last line of the song inside the format call and used two formats where I guess only one is needed.

Also had a go at the number guessing game. 

```
(defun make-em-guess (tellemwottodo)
  (format t "~a: " tellemwottodo)
  (or (parse-integer (read-line) :junk-allowed t)
      (make-em-guess "Not an integer. Try again")));If input is not an integer, re-call make-em-guess with error message.

(do ((secretnumber (+ 1 (random 100)))
     (numberofgoes 1 (1+ numberofgoes))  
     (wotdidtheysay (make-em-guess "Pick a number between 1 and 100")	;Set'wotdidtheysay' by calling make-em-guess with the initial instruction.
		    (make-em-guess (if (< wotdidtheysay secretnumber) "Too low, pick a higher number" "Too high, try something lower")))) ;Each loop 'wotdidtheysay' is reset by calling make-em-guess with appropriate instruction.
    ((= wotdidtheysay secretnumber);End test for 'do' loop.
     (format t "You won in ~a goes!" numberofgoes)))
```

It was a much uglier beast using 'loop' before I saw a previous effort which showed that 'do' has all the control needed for this game, including getting all the variable scope right. Feel like I cheated after that, but once you see a nice idea you just can't get it out of your head...

---

### Post by CuracaoThe on 2011-07-11
My first Lisp program ever:
[PHP]
(setf *random-state* (make-random-state t))

(format t "Guess the secret number (from 1 to 100):")
(defvar secret_number (+ (random 100) 1))
(loop for i do
  (setq prediction (read))
  (if (> prediction secret_number)
    (format t "Secret lower.~%"))
  (if (< prediction secret_number)
    (format t "Secret higher.~%"))
  (if (= prediction secret_number)
      (progn (format t "You win! Yes, it was ~D.~%It took you only ~D attempts!"
      secret_number i)
      (return 0)))
)
[/PHP]

---

