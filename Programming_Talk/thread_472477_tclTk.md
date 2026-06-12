---
title: "tcl/Tk"
date: 2007-06-13
forum: Programming Talk
---

### Post by cra65 on 2007-06-13
Hi.

I am a very newbie on Linux and programming; I need Tcl/Tk  to do  particular scripts.
I'm having a trouble with tcl shell  (tclsh).

In tclsh I can't use cursor keys:
```
paolo@paolo-laptop:~$ tclsh
% set x [expr {2+1}]^[[D^[[D
```


When I digit  "<-" (left arrow)  appear ```
^[[D
``` instead; 
the right cursor arrow produces ```
^[[C
```
the CANC key ```
^[[3~
```.


I'm using Ubuntu linux 7.10 on laptop (HP Compaq nx6310). 

My locale seems correct:

```
paolo@paolo-laptop:~$ locale
LANG=it_IT.UTF-8
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC="it_IT.UTF-8"
LC_TIME="it_IT.UTF-8"
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY="it_IT.UTF-8"
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER="it_IT.UTF-8"
LC_NAME="it_IT.UTF-8"
LC_ADDRESS="it_IT.UTF-8"
LC_TELEPHONE="it_IT.UTF-8"
LC_MEASUREMENT="it_IT.UTF-8"
LC_IDENTIFICATION="it_IT.UTF-8"
LC_ALL=

```

and I haven't problems with "normal" shell.

Any suggestions?

---

### Post by Toxe on 2007-06-13
Yes, that means that tclsh is not using the readline library. Try running it like:

$ rlfe tclsh

The rlfe tool (you may have to install it first) "intercepts" your cursor keys and wraps a readline environment around your input prompt. A very handy tool. :-)

You can try rlwrap as well, does the same thing. Dont know which one is better.

---

### Post by cra65 on 2007-06-14
Many thanks for  your answer!

rlfe works perfectly!

:D

---

### Post by Vox754 on 2007-06-14
Yep, that happens normally when you run "tclsh" or "wish" from the terminal.
You can try the "Tk Console".
```

sudo aptitude install tkcon
tkcon &

```

It includes variable and command highlighting. It lets you load the packages you want.
Many options. Very handy, even if you are only doing scripting and no graphical interfaces.

In Linux you can use the terminal, but tkcon is a must in Windows.
Also, you can try ActiveTcl, a free distribution from ActiveState with lots of packages. Easy to use, with complete documentation.
It can be installed anywhere, like /home/username or /opt and it won't collide with the default tcl8.4 installation, just make sure you set the PATH variable correctly.

If you decide to use tkcon, just remember, do not destroy the toplevel window "." after calling Tk; it won't allow you to create another one, so you'll have to close tkcon and open it again.

---

### Post by cra65 on 2007-06-15
Perfect!

I've just  installed tkcon and Active Tcl according to your  hints and everything seems working well.

Now, I have to learn Tcl/Tk with a good tutorial !

Many thanks.

---

### Post by Vox754 on 2007-06-15
[quote=cra65]
Now, I have to learn Tcl/Tk with a good tutorial !
[/quote]

I don't think you can find a "really good tutorial" for Tcl/Tk the way you can with, say, Python.
The way I learned Tcl, was simply with "any tutorial". It doesn't have to be particularly good; it only needs to teach you the fundamentals so you can use the included html documentation in ActiveTcl.

You just need to know, (1) everything is a string, (2) the "expr" command lets you use mathematical, boolean expressions with strings, (3) everything is treated as strings separated by space, (4) in the documentation the percent sign indicates optional arguments, (5) you group things with double quotes (allowing substitution of variables) or with braces (without substitution), (6) you evaluate expression with brackets, (7) continue lines and escape certain characters with the backslash "\".

```

command word1 word2 word3
command option value ?option2 value2 option3 value3?
puts [expr {$a+$b} ]
array get array_name_here ?pattern?

```

For instance, the for expression needs all of its arguments separated by space.
```

for {set a 1} {$a <= $end} {incr a} {
  puts "the body of the loop goes here"
  puts "continue in the next line \
        leave proper indentation \
        to make the code readable"
}

```

You may need to experiment for a while, specially substitutions, when to use brackets, braces, and double quotes.
------------------
I just noticed that in your first post you said you were using Ubuntu 7.10,... hilarious.

---

### Post by cra65 on 2007-06-18
7.04 of course!

I'm attending this tutorial

[http://www.bin-co.com/tcl/tutorial/contents.php]("http://www.bin-co.com/tcl/tutorial/contents.php")

what do you think about it?

I'm a very newbie and... not a great mind! Anyway your guggests are clarifying. Thanks.

---

### Post by Vox754 on 2007-06-19
> **cra65 said:**
> 
I'm attending this tutorial
[http://www.bin-co.com/tcl/tutorial/contents.php]("http://www.bin-co.com/tcl/tutorial/contents.php")


Na. Seems like a crappy tutorial.

I hate things like this,
> 
Before beginning I would like to scare you a little. If you see the following code and run away scared, well, there would be one less Tcl programmer and thus, less competition for good Tcl programmers like me. If you are still brave or pretending to be brave, good for you.


They think they are so damn smart.

I suggest you to take any tutorial you like, but always go back to read the documentation to see what they are not telling you.

---

