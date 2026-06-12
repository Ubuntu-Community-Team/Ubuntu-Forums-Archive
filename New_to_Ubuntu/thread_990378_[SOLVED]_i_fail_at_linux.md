---
title: "[SOLVED] i fail at linux"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by jayfisher on 2008-11-22
do i need to know how to script to use ubuntu?
i cant even download stuff because u have to script them together
i mainly use my pc for browsing watching movies msn ect.
i have looked at some tutorials for bash scripting but i dont understand them i just want to be able to use ubuntu but i dont know half the stuff thats there or the keywords that people use, i think i might have to go back to win xp

---

### Post by DGortze380 on 2008-11-22
> **jayfisher said:**
> do i need to know how to script to use ubuntu?
i cant even download stuff because u have to script them together
i mainly use my pc for browsing watching movies msn ect.
i have looked at some tutorials for bash scripting but i dont understand them i just want to be able to use ubuntu but i dont know half the stuff thats there or the keywords that people use, i think i might have to go back to win xp

What are you trying to do? Maybe we can help.

You shouldn't NEED to script anything. A script is just a bunch of BASH command.

---

### Post by oldos2er on 2008-11-22
"i cant even download stuff because u have to script them together"

 Script what together? I'm not even sure what you mean by script.

 Use Synaptic Package Manager or Add/Remove to install and remove applications.

---

### Post by jimmy the saint on 2008-11-22
I have been using Ubuntu for close to two years and have yet to employ a single script to do anything related to normal use.  Certainly not to download anything. I hate to sound  repeat what was already said, but if you tell us what you are trying to do, we can probably tell you how to do it without a script!

---

### Post by jayfisher on 2008-11-22
there are loads of programs i have seen, but its not like "next next finish" lol. which is what i am used to u have to download the code or script and make it yourself yeah? am probably takling crap here but im so confused

---

### Post by DGortze380 on 2008-11-22
> **jayfisher said:**
> there are loads of programs i have seen, but its not like "next next finish" lol. which is what i am used to u have to download the code or script and make it yourself yeah? am probably takling crap here but im so confused

You're making things too complicated.

apt-get is a great package manager. No need for the normal user to download and compile source code.

Use "Synaptic Package Manager" in the System->Administration menu to install software.

If there is a particular program you want to install that is not in synaptic, start a thread with a title like: How To Install XYZ Program on 8.10. We can walk you through it.

Simple explanation. Download source, extract it with tar, ./configure, sudo make, sudo make install.  
The configure script is already written, you just run it, create a make file, and install the make file.

---

### Post by Irihapeti on 2008-11-22
If you want to learn more about the basics of Ubuntu, go here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by cmay on 2008-11-22
if you go to the add/remove in the menu you have to enter your password and then click ok then install the programs you want from there. i have gotten used to bash scripts for installing a bunch of programs i know i want so it is more easy but it is not something you need as such. it took me about a year before i started to use the the terminal at all i think.

---

### Post by ikisham on 2008-11-22
To add wichever program you need, go to Applications>Add/Remove... and your done! Just search and install what you want or need. To update ubuntu: System>Administration>Update Manager, but actually it updates automatically so it's even better!
Look, I'm using ubuntu for 1(one) whole week now and really know almost nothing of programming. This system is REALLY user friendly, just don't bother. Go and do the tasks you need, if the system or the program you're using asks to install something (like codecs) just do it. For MSN, go to Applications>Internet>Pidgin Internet Messenger and put your username and password, wait it load and you're there. Now, if something you're trying to do isn't working, come to the forum and people will help you.:)

---

### Post by jayfisher on 2008-11-22
> **DGortze380 said:**
> Simple explanation. Download source, extract it with tar, ./configure, sudo make, sudo make install.  
The configure script is already written, you just run it, create a make file, and install the make file.
Thats where u lost me, tar = ? sudo = ? i think i will just use the add/remove feature for now but not every programs is there is it? btw thanks for the post's guys appreciate it

---

### Post by laurielegit on 2008-11-22
For any terminal/bash things just use this tutorial: [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php). It helped me a lot.

Good luck,

Laurie

---

### Post by cmay on 2008-11-22
in case you have not found a way yet to install the restricted codecs you can find them under others in the menu . i posted a screenshot so you can see how it works. after installing it then the movie player should work. and there is a package for flash also in that section. 
good luck

---

### Post by jimmy the saint on 2008-11-22
A fundamental concept to understand here is the software repository.  Unlike other OSs, Ubuntu (and other distributions) maintain software repositories filled with software that has been tested to work with your installation.  With other OSs, you find a piece of software you want, search for it, Pay for it, download it, install it and hope it does what you want and not what you don't.

With Ubuntu, you simply need to go to add/remove, or synaptic, search for it, set it to install and let the package manager do everything for you.  This is nice because you know that the packages are tested and safe. (so long as you stick to the official repositories)

Ubuntu is built on Debian and uses most of its packages.  This means that you will be hard-pressed to find software that is not available to you through the repositories.  I think I have had to compile one piece of software in two years (RealPlayer) and that has since been added to the repositories.

---

