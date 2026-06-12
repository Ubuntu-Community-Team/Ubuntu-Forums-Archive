---
title: "[SOLVED] firefox profile manager?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by h4nn4h on 2008-10-27
Hey everyone!

I'm very new to ubuntu, I recently installed it and have been running it alongside windows for the last couple of weeks. I've just been looking around, really, doing most of my real work in windows. But I like ubuntu a lot, the idea of open source, and the look of it too. So I want to start using it for real, but it is confusing for someone who has only used windows before. For instance, the first thing I want to do is import all my settings from my firefox in windows. I use the FEBE extension to backup my firefox profile regularly, and it has saved me before when I had to reinstall windows, so I'm guessing I can use that now, too. The only problem is, you have to create a new user profile for firefox to get it to work, and I'm so new to linux that I don't understand the explanation for linux users that is given:

"Close the application completely and make sure that it is not running in the background. Open the terminal and execute cd (program directory) then execute: 
(Firefox) ./firefox -profilemanager 
(Mozilla Suite) ./mozilla -profilemanager 
(SeaMonkey) ./seamonkey -profilemanager 
(Thunderbird) ./thunderbird -profilemanager 
Alternately, in a terminal type path/to/application -profilemanager"

I know where the terminal is, but other than that I have no idea what to do. Where is the program directory? I hope someone here can help me out with this, and in the mean time I'm going to look for a guide to ubuntu for absolute beginners, so I can get started for real :-) (any tips for a good one are welcome, of course!)

---

### Post by GumboLinux on 2008-10-27
terminal is  under applications > accessories > terminal
then you just type in the command for the one you want =]

---

### Post by h4nn4h on 2008-10-27
Yes, but what is the command? I'm in the terminal but I have no idea what to type. Just copying what it says there obviously doesn't work, and I have no other ideas...

---

### Post by GumboLinux on 2008-10-27
./firefox -profilemanager

---

### Post by GumboLinux on 2008-10-27
Also an amazing ubuntu book is the official ubuntu book [second edition] from the company prentice hall. the authors are Benjamin Mako Hill and Jono Bacon. Ivan Krstic. David J. Murphy. Jonathan Jesse. Peter Savage. Corey Burger. I would suggest buying the book but if you really need advice with something I got the book right next to me so ask away. Also I am not saying pirate the book at all but you may be able to torrent it until you get an actual copy.

---

### Post by h4nn4h on 2008-10-27
Thanks for the help!

That's what I typed, but it said that that folder or file didn't exist. Maybe it's because my ubuntu installation is in Dutch? English commands always worked in my Dutch-language windows, but is that true for ubuntu, too? In that case, where do I find the correct command?

ps: Even though I sound like it, I'm not stupid...just and ABSOLUTE beginner :)

---

### Post by GumboLinux on 2008-10-27
I have no clue what the command is in dutch but i am pretty sure that you could find it out easily. the english word is configure so maybe use a translator to change the word to dutch? Other than that I cannot help you and I understand too. I am a beginner too I just happen to have google and the official ubuntu book next to me and a linux book over a thousand pages long as guides. Keep trying and you will learn =]

---

### Post by h4nn4h on 2008-10-27
Alright, after a lot of googling I found the right command (or so I think), but when I use it, firefox just opens. Very strange! I'll google some more, but if someone knows a solution, please tell me!

---

### Post by eder.apt-get on 2008-10-27
I´ve been working on a Portuguese hardy 8.04, and the shell commands don´t change at all, I mean, Gnome/KDE is in portuguese, but not the commands.
H4hh4h, maybe you were in the wrong directory, back there when you got 
"folder or file didn't exist" message. Your firefox profile should be in something like /home/username/desktop.

---

### Post by reg4c on 2008-10-27
> **h4nn4h said:**
> Hey everyone!

I'm very new to ubuntu, I recently installed it and have been running it alongside windows for the last couple of weeks. I've just been looking around, really, doing most of my real work in windows. But I like ubuntu a lot, the idea of open source, and the look of it too. So I want to start using it for real, but it is confusing for someone who has only used windows before. For instance, the first thing I want to do is import all my settings from my firefox in windows. I use the FEBE extension to ....

Hey, 

the command is actually 

```
firefox --profile-manager
```
and not the single hyphen. I am assuming that you took this from a WordPress blog since WordPress changes '--' to a longer '-'.

Give it a try
Cheers

---

### Post by h4nn4h on 2008-10-27
Thanks for the help everyone, I tried all kinds of different combinations with and without the double hyphen, and at last it worked!

---

### Post by reg4c on 2008-10-27
> **h4nn4h said:**
> Thanks for the help everyone, I tried all kinds of different combinations with and without the double hyphen, and at last it worked!

Mind telling us what worked so that we know what was the error?

Cheers

---

### Post by h4nn4h on 2008-10-28
I found the following instruction on the dutch translation of a mozilla help site:

/usr/bin/firefox -profielmanager

That didn't work, so I tried it with -profilemanager instead, and that did work. So I'm guessing everything is normal and I just didn't know what to type instead of the .?

---

### Post by philinux on 2008-10-28
Close firefox then

firefox -profilemanager

---

