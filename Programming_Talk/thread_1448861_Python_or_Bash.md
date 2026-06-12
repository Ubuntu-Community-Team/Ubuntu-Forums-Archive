---
title: "Python or Bash?"
date: 2010-04-07
forum: Programming Talk
---

### Post by @rizz on 2010-04-07
Hi everyone,

  Sorry to bug you all with a silly question(not to me though.....)
I have some experience in JavaScript programming.(HTML and CSS as well). But now i want to learn some language that can help me make tiny applications for myself.(Lost interest in web designing).

 So i decided to go for python!!! But a friend of mine tell me that i should learn bash first as i work on linux. Now dont get me wrong i like the shell and i do most of my work from the terminal (i even browse this forum with lynx at times).

But is it possible to learn python and pick up bits bash along the way 

or 

should i postpone my python plans for a few weeks and introduce my self with the bash first.

Plz its a question that i am really stuck on.

plus i have python v2.6

apt-cache says its the most current. now i read i an article that 3.01 is the latest

i tried to install 3.01 but it says that i already have the latest.

---

### Post by matmatmat on 2010-04-07
The python you have installed is the latest in 2.x series, to install the latest 3.x release do:
```

sudo apt-get install python3.1 # maybe python3

```

To your question, if you choose Bash, see [this]("http://tldp.org/LDP/abs/html/") guide. Why not pick up the basics from the guide and then move onto python...

---

### Post by ahmatti on 2010-04-07
I don't think there is a real reason why you should learn bash instead of python. I'd recommend going straight with Python and if you do need bash then it is easy to pick up. A lot of Python packages haven't been ported to Python 3.x so it is maybe safer to start with Python 2.6.

Note also that Bash itself can't do very much, but you usually use shell scripts to call the [coreutils]("http://www.gnu.org/software/coreutils/") or awk or sed to do what you wan't, which is also entirely possible to from Python and also Python gives you a lot more options. 

I'm not saying that bash is useless, but I think you'll benefit more from Python and can learn bash after it if you feel the need.

---

### Post by timvoet on 2010-04-07
if you're looking to learn python, and run linux, possibly even Ubuntu being on these forums

take a look at this

[http://aciresnippets.wordpress.com/](http://aciresnippets.wordpress.com/)

---

### Post by Cracauer on 2010-04-07
> **@rizz said:**
> But a friend of mine tell me that i should learn bash first as i work on linux.


That doesn't make any sense.

> 
 Now dont get me wrong i like the shell and i do most of my work from the terminal (i even browse this forum with lynx at times).


It is indeed useful to start out with interactive commands, make them longer at the commandline, then using them as a start for a shell script. Very handy, I do that all the time.

But that doesn't change the fact that effectively shell scripts are not "real" programming, they are too fragile in a number of ways. I do the above because I can easily switch to a "real" programming language, and - more importantly - I know *when* to do so.

If you don't know a real language yet and you have an interest in Python anyway, learn Python.

> 
plus i have python v2.6

apt-cache says its the most current. now i read i an article that 3.01 is the latest

i tried to install 3.01 but it says that i already have the latest.

Use Python 2.x. Many of use still have hope that Python 3.x completely fails and even if not, you don't want to be around for the battle.

Python is not about the language. Python is about the libraries that others wrote that you re-use. Almost none of the libraries are available for 3.x.

---

### Post by nvteighen on 2010-04-07
As the people above already said, you better go with Python. Bash is a shell scripting language, very useful of course (and I should learn it too...), but shell scripting in general is a somewhat limited programming area devoted for controlling processes in a system. 

There are amazing things done in bash of course and general programming is in theory possible in bash, the issue is that as a shell scripting language, it lacks libraries and bindings that other languages do have. For example, you can't use a GUI toolkit with bash unless using very specific stuff like zenity, which makes it possible to show some predefined GTK+ dialog boxes... but that doesn't make it possible to use GTK+ at its 100%.

---

### Post by tgalati4 on 2010-04-07
It depends on the kind of programs that you want to write.

You will want to know both eventually.

Start with basic bash.

Then learn basic python.

Then learn advanced bash.  Then tackle advanced python.

---

### Post by GeoMX on 2010-04-07
What kind of applications are you willing to program?

I recommend going with Python, it's a "real" programming language. And as a side project, learn some bash (it'd come useful every now and then).

---

### Post by soltanis on 2010-04-07
> **Cracauer said:**
> 
Use Python 2.x. Many of use still have hope that Python 3.x completely fails and even if not, you don't want to be around for the battle.

Oh God we can only hope...

[QUOTE=GeoMX]
I recommend going with Python, it's a "real" programming language. And as a side project, learn some bash (it'd come useful every now and then).
[/QUOTE]

Bash (or more generally, POSIX sh) is totally a real programming language. It has one hell of a weird syntax (some guy thought ALGOL was a great programming language and modeled the syntax on that, now several decades later we're stuck with it), but indeed it was intended to function not as an interactive shell but as an environment to write real programs in.

Here's the thing, Python is just more of an, I guess, orthodox approach to doing programs. The way it teaches you to program is the way a majority of people tend to program -- monolithically. That's not the UNIX way, which is the way sh and awk (the two languages I guarantee you will find on any POSIX compliant system, even hostile ones like Mac OS X) do things, where data is represented in files and programs act as filters.

I used to write a lot of time with Python but recently I've started to realize just how brilliant the UNIX way is (and how productive you can get with it).

---

### Post by GeoMX on 2010-04-07
> **soltanis said:**
> Oh God we can only hope...

Bash (or more generally, POSIX sh) is totally a real programming language. It has one hell of a weird syntax (some guy thought ALGOL was a great programming language and modeled the syntax on that, now several decades later we're stuck with it), but indeed it was intended to function not as an interactive shell but as an environment to write real programs in.

Here's the thing, Python is just more of an, I guess, orthodox approach to doing programs. The way it teaches you to program is the way a majority of people tend to program -- monolithically. That's not the UNIX way, which is the way sh and awk (the two languages I guarantee you will find on any POSIX compliant system, even hostile ones like Mac OS X) do things, where data is represented in files and programs act as filters.

I used to write a lot of time with Python but recently I've started to realize just how brilliant the UNIX way is (and how productive you can get with it).

That sounds like a better way to express the difference between bash/shell and other "common" programming languages :).

---

### Post by @rizz on 2010-04-07
hey guys,

 Thanks for all the advice. I will Go with the majority and start with python( but i will still keep my friend's request and do a bit of bash as well).

Now then here is the deal. thanks for guiding me to the language but now please suggest a pdf or two or web tutorials

but remember yous are trying to teach a non programmer here, so please be merciful.

 thanks again for all the replies......:)

---

### Post by Cracauer on 2010-04-07
The major reason why shell scripts are bad to learn programming is that they don't have direct facilities to hold composite data structures in memory. Trying to stuff complex data structures into strings usually leads to delimiter/quoting hell and putting everything into a file gets old and slow real quick.

---

### Post by tgalati4 on 2010-04-07
Follow Jono Bacon's Opportunistic programming:

[https://wiki.ubuntu.com/UbuntuOpportunisticDeveloperWeek](https://wiki.ubuntu.com/UbuntuOpportunisticDeveloperWeek)

Then install acire (available in karmic and lucid)

sudo apt-get install acire
acire

It has python snippets that you can look at and run to see what they do.

Then go through some of the more advanced topics on the link above.

A simple google search will give you plenty of on-line python tutorials.

---

### Post by bdemarest on 2010-04-07
Free Python-based intro to programming textbook here:
[http://www.greenteapress.com/thinkpython/thinkpython.html](http://www.greenteapress.com/thinkpython/thinkpython.html)

---

### Post by geirha on 2010-04-08
When you do want to learn shell scripting with bash, I recommend that you stay away from the bash guides at tldp.org. They are out-dated, doesn't teach good practice, and in some cases just plain wrong. Read this guide instead: [http://mywiki.wooledge.org/BashGuide/](http://mywiki.wooledge.org/BashGuide/) and the FAQ at that site is very useful too; [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

---

