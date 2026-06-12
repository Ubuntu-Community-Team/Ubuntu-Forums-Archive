---
title: "Adept problem? Maybe?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by aridattebayo on 2008-06-12
Okay, I'm new here, and I hope I'm posting this in the right place. Forgive me, I'm just getting the hang of this. Totally new to the forums, totally new to anything Linux, not new to computers.

I'm having an issue with Adept. Well, last night, Adept is telling me it has 100+packages that need updated/installed/whatever, so I was talking to my (also using kubuntu) friend, who said, "Yeah, updating when it tells you to isn't going to hurt." So I went ahead and told Adept to go ahead. (Another linux using friend told me that always updating will break your OS, I hope its a myth... I don't want my OS to be broke!!) 

Adept gets stuck at 81% ... "Compiling Samba preferences" or something. It didn't respond to anything, so I just chose quit from the menu (it had been stuck for 12+ hours! And when I typed "top" in the command line there was no sign of Adept running that I could see. (Or maybe I wasn't reading it right, I am not sure.)

So I rebooted my computer (Misa), and booted up as usual. I go to run Adept again, to see if I can pick up where I left off and it's telling me that something it needs is still in use.... But I have no clue what or how and I hope to G-d that it logged out of root. (no signs of anything!)

So how do I fix this? I wish I knew more about this stuff. I know little or NOTHING about how the nuts and bolts of this works. :( I'm also a nervous wreck about breaking the computer. And I'm pretty linux clueless... I know one or two commands, but alot of 'em I don't know how to really read well, I just have watched others use 'em. (I need Linux for dummies or something...)

Thanks in advance!

Edit: Problem solved! Thanks to all!

---

### Post by Absolute-Zero on 2008-06-12
Try killing the all process or force kill the adept when it gets stuck then restart ur compt and try it again, if same erros comes up, this could be becouse of some corrupt application or something is missing or incorrectly installed. 

Updating should be easy, but i had trouble before with adept, thats why i went back to gnome instead of kde

---

### Post by aridattebayo on 2008-06-12
> **Absolute-Zero said:**
> Try killing the all process or force kill the adept when it gets stuck then restart ur compt and try it again, if same erros comes up, this could be becouse of some corrupt application or something is missing or incorrectly installed. 

Updating should be easy, but i had trouble before with adept, thats why i went back to gnome instead of kde

Thanks for the suggestion! I also did some googling, and was able to do the apt-get stuff in command line and I think it's all better (adept is running as usual, but no longer sits in my toolbar). I'll keep that in mind if I run into the problem again though. 

Thank you again! :)

---

### Post by Absolute-Zero on 2008-06-12
Its ok mate, and i forgot to tell you about update with terminal, silly me haha
yeh you right 

sudo apt-get update
sudo apt-get install update 

these commands will update and install updates on your computer (forgot to tell you this lol ) sorry

---

### Post by Kevbert on 2008-06-12
You may also want to run 
```
sudo apt-get install -f
```
in terminal (in case there are any damaged packages).

---

