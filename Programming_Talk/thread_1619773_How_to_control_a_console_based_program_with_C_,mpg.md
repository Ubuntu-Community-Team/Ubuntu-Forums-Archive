---
title: "How to control a console based program with C ,mpg123"
date: 2010-11-12
forum: Programming Talk
---

### Post by hyetik on 2010-11-12
I am trying to write a simple mp3 audio player with C and using Gtk and mpg123. At first I tried to use libmpg123, but its poor documentation pushed me to play mp3s with mpg123.

I am able to start playing mp3 files with system() func. in C, but whenever I call system(), I think it does commands,I give with different terminal session. 

ex:
when play button clicked;
system("mpg123 -q -C *.mp3 &);  // start playing

but when stop button clicked;
system("fg");  // bash: fg: current: no such job
system("s");   // s: command not found , music play till I kill process.

Is there anyone used libmpg123? 

What I really need is pipe between mpg123 and my mp3 player gui, but how?

---

### Post by Arndt on 2010-11-12
> **hyetik said:**
> I am trying to write a simple mp3 audio player with C and using Gtk and mpg123. At first I tried to use libmpg123, but its poor documentation pushed me to play mp3s with mpg123.

I am able to start playing mp3 files with system() func. in C, but whenever I call system(), I think it does commands,I give with different terminal session. 

ex:
when play button clicked;
system("mpg123 -q -C *.mp3 &);  // start playing

but when stop button clicked;
system("fg");  // bash: fg: current: no such job
system("s");   // s: command not found , music play till I kill process.

Is there anyone used libmpg123? 

What I really need is pipe between mpg123 and my mp3 player gui, but how?

The 'system' call starts one new shell each time, so system("fg") is useless - there is nothing to put into the foreground under that shell.

Maybe the function 'popen' suffices for you. Otherwise, look at the package 'expect'.

Do you really mean "gui"? Graphical user interface. You cannot pipe commands to one of those. There do exist programs which let you automate interaction with graphical programs, but I don't know the name of any.

---

### Post by hakermania on 2010-11-12
Why don't kill the mpg123 ?
killall -v mpg123  :)

---

### Post by hyetik on 2010-11-22
> **hakermania said:**
> Why don't kill the mpg123 ?
killall -v mpg123  :)

Now I can play audio with mpg123 and to stop I am killing mpg123 process :) But this does not solves my problem cause I want mpg123 also pause the audio :(

and 

@Arndt

I have tried popen, and it looks like it'll work, thanks:popcorn:

---

