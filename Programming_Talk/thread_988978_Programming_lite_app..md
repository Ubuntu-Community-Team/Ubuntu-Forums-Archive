---
title: "Programming lite app."
date: 2008-11-21
forum: Programming Talk
---

### Post by backinthecity on 2008-11-21
Ok I work in the Machine (CNC) world and I'm looking into creating a program for myself, but the problem is that I was learning some Python and Ruby a while back but since have kind of forgot a lot. I was hoping someone could give me a good direction in which language to use 

What I want: 

I want to create a program where its a basic "checklist" type program.
I'm going to be dealing with something like 30 something check boxes prob. 
I want to where if I create a new document it would keep track of my previous documents. 
It could save the documents in this way (for ex. 011408rtp.txt where it would stand for " Jan 14, 2008 Reset Tool Post" all of the dates and "rtp" would be a field that would need to be filled during new file creation. 
The reason for the naming would be reasons in a way where when i look up a stat i could search how many times i have to reset tool post and search in the way of  " *rtp.txt (# of files) 

I know this may seem kind of hazy but its the best way I can describe it without getting into much boring detail. 

I just want to figure out which language I should try so i can close my computer and keep my status of the program after shutdown and so forth until a new document is created and my old documents would be kept in a specific folder (assigned by myself) for status lookups .

if you have any advice please send my way. 
-thanks

---

### Post by pmasiar on 2008-11-21
Python is good choice, but you likely get bogged down with GUI - GUI **always** complicates programming. Try to avoid GUI, instead thing about handling menu in text mode (print many options, input selected one), or something like that.

If your GUI needs are simple, try EasyGUI for Python, it is as easy GUI as you can get anywhere.

---

### Post by backinthecity on 2008-11-21
if a gui is needed its really going to be a checkbox type gui something really simple... and thanks for the advice.

---

### Post by backinthecity on 2008-11-23
Mr pmasiar and Anyone who reads this, 

I must admit I did admire your advice but I got my hands on realBasic (thanks to a friend) and I watched maybe... 3 tutorial videos from realbasic.tv and i must say... WOW.

don't know if you'd be interested but here is what i have so far [Checklist Program]("http://www.ghostteeth.net/myapps/mashburnlinux.zip"). You can kinda see where i was going with this idea. Any input would be amazing 

in advance thanks again

---

