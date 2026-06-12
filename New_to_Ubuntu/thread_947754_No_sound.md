---
title: "No sound"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by NoL618 on 2008-10-14
When I installed with the live cd I initially had sound when booting up and all that good stuff, now a week later, I have no sound for anything...

I see all these posts with "no sound" and then a bunch of codes.  

what do you do with these codes? and how do I get sound?

thanks!:KS

---

### Post by bobnutfield on 2008-10-14
Follow this guide, and post back if you run into difficulty:

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

### Post by NoL618 on 2008-10-14
ok, now what is a "shell"? and where do I go to get it? 

go ahead, you can laugh....lol

:lolflag:

---

### Post by bobnutfield on 2008-10-14
No laughing here....I was new once and didn't know my a... from a shell..

A shell is the terminal.  Applications>Accessories>Terminal.  This where all the commands are run, in other words, this is the command line.  Do not fear it!

---

### Post by NoL618 on 2008-10-14
ok, so I followed the link, entered the codes in the order the website said to, found the name of my chipset, but it is not on the list under "Intel" (the site that the first link told me to go to).  

If its not listed, the site said they cant help me now, but stay tuned...lol

What now?  I think I am reading in right...but not sure..

---

### Post by bobnutfield on 2008-10-15
OK, lets see if we can get sound going for you.  First, are you using a laptop or a desktop?  Open a terminal (the shell) and type:

> lspci | grep Audio

Just want to know what your sound card is so that I can recommend a solution.

---

