---
title: "Backtrack / learning Linux"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by sunnypt on 2012-10-17
Hi all!
I am a real absolute beginner! just started using Ubuntu today. tried it with dual boot and i like it so i put a clean install and let windows go. I'm using Ubuntu 12.04 and now i have a question.
My goal is to learn all i can so later i move on to Backtrack. What should i focus on, and btw, is there a way to make 12.04 look more like Backtrack 5? i kinda like the drop down menus in BT5 =). 
Any help will be welcome! :D

---

### Post by Bashing-om on 2012-10-17
sunnypt; Hi ! Welcome to the forum;[INDENT]and the wonderful world of open source !
[/INDENT]Backtrack 5 => have not seen it-> cannot advise.

Advice:
1. look through the various "stickies" in the forums.
2. Learn bash:[INDENT][LEFT][http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)
[/LEFT]
[/INDENT]3. Learn linux:
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

Keep in mind ---it is your system to do with as you please, what you make of it is up to you!
ubuntu -> NO secrets.

4. Explore and follow your curiosity , Ask and thou shalt receive.
[INDENT]just my 2 bits worth ==> BDQ

[/INDENT][LEFT]
[/LEFT]

---

### Post by Cheesemill on 2012-10-17
BackTrack R5 is based on Ubuntu 10.04, you may want to install that instead.

Another option to make Ubuntu 12.04 look more like 10.04 is to use Gnome Fallback as your desktop instead of Unity, instructions can be found here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by sunnypt on 2012-10-17
Nice, gonna check that out! thx for the info. so for what i see Bash is the main "command line" right? kinda like DOS?

---

### Post by Bashing-om on 2012-10-17
Bash: yes and no -> no being that bash is much more powerful !

The manual will become indispensable.
```
man <command-name>
see:
man man

```[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by sunnypt on 2012-10-17
> **Bashing-om said:**
> Bash: yes and no -> no being that bash is much more powerful !

The manual will become indispensable.
```
man <command-name>
see:
man man

```[INDENT]just try'n to help <==BDQ

[/INDENT]


i see. gonna try that. getting the thirst for knowledge :D

---

### Post by Bashing-om on 2012-10-17
That is a great thing..... IMHO you are stepping into the greatest operating system the world has ever known -due in large part to the support and documentation.( be aware of context - evolving system..pre grub, pre plymouth, pre upstart, pre unity ect ect.... -> how documentation may apply to current operating system). ubuntu has evolved through lots of stages.

[INDENT]ubuntu ->no secrets <-BDQ

[/INDENT]

---

### Post by sunnypt on 2012-10-17
> **Bashing-om said:**
> That is a great thing..... IMHO you are stepping into the greatest operating system the world has ever known -due in large part to the support and documentation.( be aware of context - evolving system..pre grub, pre plymouth, pre upstart, pre unity ect ect.... -> how documentation may apply to current operating system). ubuntu has evolved through lots of stages.
[INDENT]ubuntu ->no secrets <-BDQ

[/INDENT]
  well, im trying to study [http://rute.2038bug.com/rute.html.gz](http://rute.2038bug.com/rute.html.gz) now , seems kinda complicated. can't seem to understand how i can apply it to the scripts i'll be trying. maybe cuz it's the first time i'm looking at this kind of stuff LOL :D

---

### Post by Bashing-om on 2012-10-17
It takes a while for it all to sink in, an old adage applies, the third read is for comprehension. //soon you will be able to put things together. Do keep this in mind -> ubuntu is not windows. Many of the concepts of windows does not apply. Take a bit of time to study the linux file hierarchy and a kernel concept. My experience was when I had this down, all the rest was just "add ons".

[INDENT]love'n ubuntu ==>BDQ

[/INDENT]

---

### Post by No1Mportnt on 2012-10-17
I am new to Ubuntu too.  I have found that there is a ton of resources but when I have something I want to do I do a quick search on that specific subject and then read/follow the procedures provided.  Be sure to read a few different posts to ensure you are on the right path.

---

### Post by Bashing-om on 2012-10-17
oh yeah ...script, no matter how complex a script seems, it is still just a series of commands put to the interpreter shell (bash in this case).. do not confuse with .bat files, way different..(am i miss-assuming your background is the windows environment ??)

[INDENT] 
a lot to sleep on, huh ? <==BDQ

[/INDENT]

---

### Post by sunnypt on 2012-10-18
> **Bashing-om said:**
> oh yeah ...script, no matter how complex a script seems, it is still just a series of commands put to the interpreter shell (bash in this case).. do not confuse with .bat files, way different..(am i miss-assuming your background is the windows environment ??)
[INDENT] 
a lot to sleep on, huh ? <==BDQ

[/INDENT]
 
yeah i've been on windows all my life, but i'm kinda tired of it, and i always wanted to learn some programming/scripting, don't really know how to call it. either way, always been curious about linux, but had never tried it before. but i'm glad i did! :D

---

### Post by Cheesemill on 2012-10-18
Unless you know exactly what you are doing then I would recommend against switching to BackTrack as a day to day OS (even people who use BackTrack professionally only boot it when needed).

The vast majority of the applications that come bundled with BackTrack are also available on a standard Ubuntu installation, they just need installing. For example:
```
sudo apt-get install nmap
```

As mentioned above learning the terminal is the way to go, 99% of the tools in BackTrack are command line tools with no graphical interface.

---

