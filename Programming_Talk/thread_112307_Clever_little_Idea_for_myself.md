---
title: "Clever little Idea for myself"
date: 2006-01-04
forum: Programming Talk
---

### Post by noob_Lance on 2006-01-04
Hey im not sure how many ppl reading this actually Use fluxbox... but youll know where im going with this. Like Gnome and KDE that will make desktop icons automatically... fluxbox.. being the way it is... dosnt have this luxury.. until you get fbdesk.. but even then you have to edit them manually.. Which is your a fbdesk user... can be a little annoying. What i would like to go... is make a small python script. that i can set on a cron job to run every so often... that will run the program.. and update the ~/.fluxbox/fbdesk.icons file... leaving you from doing the dirty work. 

Now... since im not good with python... and have learned laitly from my last thread i posted here... 
i can import the os and use os.system() to exec a system command... such as ls -a ~/Desktop, altho... since it Is a programming language.. i take it that it has its own built in functions to read a dir.. 
My problem... is determining if the file being read is a file... or a folder. i dont for-see any problems
once i get that figured out.. if anyone can help.. or wants it once its done.. whats mine is yours =)

Any help would be Greatly appreciated. 

~Lance

---

### Post by noob_Lance on 2006-01-04
anyone got any ideas?

---

### Post by sapo on 2006-01-04
Why dont we join us? i liked your idea :)

[http://ubuntuforums.org/showthread.php?t=111990](http://ubuntuforums.org/showthread.php?t=111990)

btw, try this in the python console:

```
import os
help(os)
```

it have a lot of functions to do what you are trying to do ;)

---

### Post by noob_Lance on 2006-01-04
sure ill join... i suck ass at programming tho... well... with python and C... yet Java(wrote an entire blackjack game in under a week for my final assignment in gr11... after 3 weeks of dev went out the window because of a stupid floppy :@) and PHP... ahh php... how i love thee lol. AHH i see your a php dev yourself :D sweet! the most work ive done on something was my first site in full php, a cms.. all flat file :D then my friend hacked me and i jsut threw it all away lol. Then.. about a year ago now... for 3 months.. wrote a shopping cart.. still didnt finish it.. but its still on the web ([www.xmgscripts.com](www.xmgscripts.com)) great little systems i had going in that... sad i never got to see them go into action lol.. but anyways...

Sure ill join the team... who knows... if someone wants to hack firefox download manager and have it run this script (once made) when something is downloaded to the desktop. that could work too :p

Heres a problem that i see as of right now tho... the icons dont update until you log out and log in again... wait no nevermind... dumy me... use the sys functions :D get the one for fbdesk and kill it then restart it again.

~Lance

---

### Post by sapo on 2006-01-04
I dont use fluxbox so i dont know exactly whats your problem and what would be the perfect solution, but we can try to find it out ;)

And i code a lot of stuff in php, but currently just commercial stuff.. nothing like websites and stuff (i suk at design), but php/xhtml/css in the way ;)

but coding php all day long is tiring and i m trying to learn python :D

---

### Post by noob_Lance on 2006-01-04
python... good language.. alot like C.. in the fact that you use C modules in python... lol. im jsut learning C in college now... first semester sucked for teaching... i hardly every went to any classes lol. but now i have a class for Only programming in C :D and php... i can code it all day long and stay up till 5am trying to get one thing to work... oddly enuff... im going to college for web dev.. and im stuck in a second semester programming course (all the same classes as a programmer) but oh well... i might switch to programming instead of web... i like web for fun... maybe not as a job lol :D. as for using fluxbox... i think about 5% of ppl on this board actually use it haha but oh well.. :D

---

### Post by sapo on 2006-01-04
Yes, i work with php and its too boring... you just make forms, submit those forms, and make insert updates and deletes.. everyday the same stuff :(

---

### Post by noob_Lance on 2006-01-04
same stuff everyday... are you NUTS... enable the GD library and go have some damn fun man  lol... i LOVE the gd library.. you can make some pretty nice things in you take the time to write the massive code behind it.. like a hit counter (childs play).... but write the code to generate reports in the form of a graph. have it auto scale (oh boy that was a pain in the ass to do haha) so it scales everything correctly and generates the numbers for the side of the graph aswell...automatically generates the image with the right width so you dont have to scale erything within a set width... makes it alot easier to read :p while keeping them even.. thats what happens when you dont go to class and your stuck there for 7 hours :D haha


ok i got the listdir part working... how do i tell if its a file or dir.. i cant see anything for that using the help(os) thing..

---

### Post by sapo on 2006-01-04
i use phplot for graphics :p

btw
```

>>> if os.path.isdir("Desktop"):
...     print "dir"
... else:
...     print "not dir"
...
dir
>>> if os.path.isdir("index.php"):
...     print "dir"
... else:
...     print "no dir"
...
no dir

```

this is how you find if it is a dir or not ;)

---

### Post by noob_Lance on 2006-01-04
sweet... so all i have to do is throw it in a loop and use the variable i set the output of os.listdir to and im almost set lol :)

---

### Post by noob_Lance on 2006-01-04
hm... ok now im tryin it using a while loop to go thru all the values... but i get this error everytime i try to run it..
Traceback (most recent call last):
  File "updater.py", line 8, in ?
    while (list[count] != ""):
IndexError: list index out of range

Got any ideas as to what that means... count is set to 0 to start off at the first element..

---

