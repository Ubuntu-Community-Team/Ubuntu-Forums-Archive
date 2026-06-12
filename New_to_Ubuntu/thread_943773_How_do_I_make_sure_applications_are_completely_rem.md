---
title: "How do I make sure applications are completely removed when I remove them?"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by thadiusdean on 2008-10-10
This is what is essentially keeping me from the complete switch. I don't mind fooling around with things, making it work my way. What I can't stand is that I can't keep track of what exactly I am putting on my computer or doing to my computer when I install certain applications. For instance, I just installed conky. I am having trouble getting it to work, so I want to completely remove the application and start over--trial and error.
On Windows, pretty much everything is put into Program Files. If I mess it up, I can uninstall the program, delete the folder and if I'm feeling industrious clean up using CCleaner or similar program. With GNU/Linux I feel as though if I install one program, files are being sent all over the computer and I can't track them down. Sure, I can use .deb packages and the Synaptic Package Manager, which makes install and uninstall a snap. But for sudo aptitudes or apt-gets I feel like I can only really get rid of what I have installed by doing a complete wipe. Is there something I'm missing? Because I feel as though when I am messing around I am just making my computer a mess, and I don't like that feeling.

---

### Post by namegame on 2008-10-10
sudo apt-get remove WhateverYouInstalled

---

### Post by SunnyRabbiera on 2008-10-10
well there are ways to be rid of un neeeded packages and such in ubuntu.
The commands sudo apt-get autoremove, apt-get clean and apt-get autoclean.
These commands get rid of un needed dependencies and packages.

---

### Post by oldos2er on 2008-10-10
Synaptic Package Manager is only a GUI front-end to apt.

---

### Post by mdsmedia on 2008-10-10
Synaptic Package Manager etc as you say are a snap for installing and uninstalling.

Synaptic is a GUI front-end for apt-get as I understand it, so if you're apt-getting and aptituding you're essentially doing exactly the same thing as Synaptic, but on the command line.

Also, I believe that Linux does a much nicer job of keeping your system clean than Windows does. While Windows might install MOST things in c:\program files it's also creating .dlls and so on and placing those in different places.

Uninstalling in Windows is hardly ever a clean process.

---

### Post by aysiu on 2008-10-10
```
sudo apt-get autoremove
``` is pretty good, but if you ever want to try out a program and want to make sure it's completely gone when you remove it, keep track of the packages that get installed along with *packagename* when you ```
sudo apt-get install *packagename*
``` and then paste them into a text document you can use later to ```
sudo apt-get remove *packagename1* *packagename2* *packagename3andsoon*
```

---

### Post by Primefalcon on 2008-10-10
```
sudo apt-get autoremove
``` will also get rid of any junk packages you are no longer needing

---

### Post by thadiusdean on 2008-10-10
> **aysiu said:**
> ```
sudo apt-get autoremove
``` is pretty good, but if you ever want to try out a program and want to make sure it's completely gone when you remove it, keep track of the packages that get installed along with *packagename* when you ```
sudo apt-get install *packagename*
``` and then paste them into a text document you can use later to ```
sudo apt-get remove *packagename1* *packagename2* *packagename3andsoon*
```
That is a good idea. I think I will try that.
> **Primefalcon said:**
> ```
sudo apt-get autoremove
``` will also get rid of any junk packages you are no longer needing
So how does the computer know that I want to get rid of conky, or any other program for that matter? Do I need to just keep track of what I have installed?

---

### Post by thadiusdean on 2008-10-10
Okay, I see how SPM works. It even shows me what is installed by default on Ubuntu so I should be able to just uncheck everything that doesn't have an Ubuntu logo next to it. How about tar files? how do I keep track of those?

---

