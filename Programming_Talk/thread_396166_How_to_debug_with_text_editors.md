---
title: "How to debug with text editors?"
date: 2007-03-29
forum: Programming Talk
---

### Post by kinson on 2007-03-29
Hi guys,

I usually program using an IDE(VS2005, or whatever). What I'm curious here is that many people just use Gedit, or VIM to code their programs. If thats the case, how to you do some debugging like "stepping through" "step in" "step out" in the program?

Cause I'm starting to learn python, and I'm coding it in Gedit(might try VIM) to start off, so I'm curious how you guys'd debug your programs. Thought it might be handy to learn as well :)

Cheers,
Kinson.

...I sound so noob asking this :p

---

### Post by supirman on 2007-03-29
Naturally, if you want to debug, you use a debugger.  I don't do python, but a google for "python debugger" yields this:
[http://docs.python.org/lib/module-pdb.html](http://docs.python.org/lib/module-pdb.html)

---

### Post by pmasiar on 2007-03-29
> **kinson said:**
> ...I sound so noob asking this :p

Not at all. The only stupid question is the one you should ask (to learn more) but you did not. 

I program mostly web apps, so my code often runs on different server and step on-step out debugging might be... complicated, to say mildly :-) And you cannot just print in random moments of your program - it will mess output badly. What I do is to have couple of config settings to manage collecting debug output to some lists, and then printing them in convenient moments (and with some decorations). I usually have couple debug collections, which I can turn on and off separately: for data access, overall progress, and detailed data in loops. Most of my data are lists of hashes, sometimes dirt-prining whole hash (=dictionary = map) in loops is simpler than pretty-printing it in nice format.

Some important statistics I may even print as HTML comment, so they are there for me, invisible to others :-)

And of course comment in/out individual statements. When program works, I often keep some debug statements (commented out) - if value has text label, it helps as documentation, and you never know when you may need them again. :-)

And limit on loops: when smoke-testing, I may want limit looping to 3-5-10 loops, so there is less output to analyze.

It also helps that Python has such unobtrusive and powerfull syntax. And Kid templating is great also: using list comprehension, it's trivial to print out your data structures nicely.

---

### Post by johnnymac on 2007-03-29
What are you writing in?  I still use good ole print statements and log files - and I do most my development in vim.  Something else (if your doing C-based stuff) is use a coverage analysis tool like bcov or gcov to help in your debugging.

---

### Post by lnostdal on 2007-03-29
For C: GDB, DDD, KDBG, valgrind .. etc.

I don't use Python much, but it is basically the same as in Lisp. The interactive nature of these languages/environments with REPLs is debugging in itself. It is "built in".

---

### Post by xtacocorex on 2007-03-29
I usually dump out text to the terminal, for some reason that's faster for me than using gdb (which I haven't fully learned yet).
 
My setup usually involves 3 terminal tabs:
1 - Coding in VI
2 - Compile/Run
3 - Free to be able to quickly go to another directory and find a file for reference.

---

### Post by lnostdal on 2007-03-29
Yes, bombarding the code with preprocessor-depending printfs (or equivalent based on language) is usually more than enough. In some cases using a logging-scheme like that is more powerful than doing "traditional"(#1) debugging as it can reveal surprising hidden things that might have 
lead to bugs later on. :)

The `print' function(s) in Common Lisp returns whatever object it has printed, so you can just put it in the middle of code _anywhere_ without actually changing the behaviour of the code. With a little macro one can make it stop printing:

```

(defparameter *debug* t)

(defmacro dprint (obj)
  (if *debug*
      `(print ,obj)
      obj))


cl-user> (+ (dprint (* 2 3))
            2)
6 
8


;; The macro-call (dprint (* 2 3)) will be replaced by (print (* 2 3))
;; which first prints the result of (* 2 3) to STDOUT then returns that
;; result as the first argument to the + function.
;; Thus 6 is first printed, then (+ 6 2) is evaluated and 8 is returned.


(defparameter *debug* nil)


;; ..now (dprint (* 2 3)) will be replaced by simply (* 2 3), resulting in:


cl-user> (+ (dprint (* 2 3))
            2)
8


;; ..so what the compiler sees now with *debug* set to nil (false) is simply this:


(+ (* 2 3)
   2)

```

..very handy.


#1: maybe doing the printf-thing is more traditional? :)

---

### Post by kinson on 2007-03-29
I've seen some suggestions that I dump the output into a text file, or output the progress into the terminal, and quite a few technical suggestions that I don't really understand :oops: 

But I suppose nothing would be like debugging in an IDE? I know I'm not really going anywhere with this, I'm just trying to clarify how things are done without an IDE. Cause to be honest, I'm realli quite fond of being able to hover my cursor over a variable and see its current value (e.g. x = 10), as well as switching between files easily (e.g. robot.py, fighter.py). I suppose I sound like I'm still suited to an IDE :(

I guess my point also is, how can using a text editor be more beneficial (in terms of debugging an app) to using an IDE? (I'm not trying to turn this into a holy war :p ).

I'm fairly used to finding bugs in my program by stepping through the code until I hit the error, then I search for the cause from there. I'm guessing I might find it kinda cumbersome to have to specially insert debug statements(i.e. printing my text out) into my code, and then having to take it out when I'm done :/

Maybe I've got the wrong concept here, or I'm missing something? :(

Cheers,
Kinson

---

### Post by ssam on 2007-03-29
if you run your python program with
```
python -i progname.py
```
then if it crashes you end up in the python interpreter and can do things like querying the values of variables.

---

### Post by kinson on 2007-03-29
> **ssam said:**
> if you run your python program with
```
python -i progname.py
```
then if it crashes you end up in the python interpreter and can do things like querying the values of variables.

Cool. Interesting :) But I still wont be able to go through my code through that interactive thing (as far as I can see). I'm going through my "Dive into python" thingy again now :D They teach through using the Interactive debugger I think. Heheh :)

Cheers,
Kinson

---

### Post by pmasiar on 2007-03-29
SPE is integrated with debugger, you may want to try it. I just never used it (reasons mentioned in my previous post).

In related news, I just found that [Pylons web framework integrates interactive debugger](http://pylonshq.com/docs/interactive_debugger.html), which is activated when app crashes. Magic! This is seriously cool magic! Debugging web app on remote server!

---

### Post by lnostdal on 2007-03-29
> **kinson said:**
> 
I guess my point also is, how can using a text editor be more beneficial (in terms of debugging an app) to using an IDE? (I'm not trying to turn this into a holy war :p ).


If we're thinking C here I use the editor for editing, and the debugger for debugging. All the features you describe in a debugger in an IDE exist in an "external" debugger.

Again: KDBG, DDD ..etc.. google it.

For Python similar things exist.

---

### Post by kinson on 2007-03-29
> **lnostdal said:**
> If we're thinking C here I use the editor for editing, and the debugger for debugging. All the features you describe in a debugger in an IDE exist in an "external" debugger.

Again: KDBG, DDD ..etc.. google it.

For Python similar things exist.

thanks. DDD says it works for python. I've installed it. Will read the manual soon :)

Cheers,
Kinson

---

### Post by 23meg on 2007-03-31
Gedit has a terminal plugin, and Geany has a built-in terminal.

---

### Post by Wybiral on 2007-03-31
> **23meg said:**
> Gedit has a terminal plugin, and Geany has a built-in terminal.

Gedits terminal plugin is actually part of my religion :)

With C code, most of the time, GCC outputs enough error and warning messages for me to debug.

---

### Post by lnostdal on 2007-04-01
Hm, I think the OP is talking about runtime debugging. Compile-time messages from GCC will not help with that.

edit:
btw. .. i do not know, but there might be debuggers out there more suitable/specialized for python than DDD .. i did say "If we're thinking C.."

---

