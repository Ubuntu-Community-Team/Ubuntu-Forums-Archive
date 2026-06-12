---
title: "Launching a terminal results in computer meltdown"
date: 2017-12-20
forum: New to Ubuntu
---

### Post by sterator on 2017-12-20
I'm trying about as hard as I humanly can to just have a functional linux installation.

I launched a terminal to see what it was like and it turned the whole screen into a terminal, didn't let me escape out of it or quit it. I powered down and rebooted to masses of screens of shooting code

rebooted again and I have a screenful of comments each beginning with 

[   [COLOR=#00cc33]OK[/COLOR]   ]

I swear to Zeus I'll never ever EVER launch that whack terminal ever again. Can I get my computer back from this insanity or must I re-install ubuntu?

again?

I didn't *do* anything except launch a terminal which is made available by pressing the super key and typing t-e-r

I get 3 choices - the first one is a well-behaved terminal where one can type commands. The other two have different sort of cartooney icons.

rebooted again and I saw a brief line about not being able to find the boot order then back to screenfuls of type

so much for exploring the OS

Thanks for any clues.

---

### Post by Darth4212 on 2017-12-21
Wait so what exactly is your issue? I am confused. Are you able to successfully boot into the GUI if so then are you wanting to boot into a terminal? If so press Ctrl+Alt+F1 and you will go to a terminal and if you want to go back to the GUI just press Ctrl+Alt+F1 again. Or are you booting into a terminal and wanting to boot into a GUI if so when your computer fully starts run ```
startx
``` and if that command returns ```
command not found
``` then run ```
sudo apt-get install ubuntu-desktop
```

---

### Post by oldos2er on 2017-12-21
> **sterator said:**
> I launched a terminal to see what it was like and it turned the whole screen into a terminal, didn't let me escape out of it or quit it. I powered down and rebooted to masses of screens of shooting code

Sounds like you launched a tty (or full-screen terminal). To get back to your graphical desktop hit Ctrl-Alt-F7.

To open a terminal on your desktop, Ctrl-Alt-t should work.

---

### Post by VMC on 2017-12-21
Yes, as Oldos2er stated, **Ctrl-Alt-t **is the correct bash terminal. The other is a virtual terminal. I'm unsure what cartoon'y characters you saw unless you outputted some binary file.

---

### Post by poorguy on 2017-12-21
Interesting when I pressed ***Ctrl+Alt+F1*** it also took me into a command line screen and how I got out was to go into ***su*** and entered my*** root password*** and then entered ***reboot ***and pressed ***enter*** and it rebooted to normal again.

I'm using ***Antix 17 Heather Heyer.***

---

### Post by yetimon_64 on 2017-12-21
> **poorguy said:**
> Interesting when I pressed ***Ctrl+Alt+F1*** it also took me into a command line screen and how I got out was to go into ***su*** and entered my*** root password*** and then entered ***reboot ***and pressed ***enter*** and it rebooted to normal again.

I'm using ***Antix 17 Heather Heyer.***

In Ubutnu, to get back to the GUI from the tty terminal that ***Ctrl+Alt+F1*** puts you in you can just press ***Ctrl+Alt+F7.***

Ubuntu does NOT enable the root account as your distro does.

Regards, yeti.

---

### Post by leunam12 on 2017-12-22
The normal user can reboot without root, at least in Ubuntu all you have to do is type reboot and press enter.

---

### Post by leunam12 on 2017-12-22
Going back to the original post: If you want help please provide more information about your hardware, also 
what distribution are you running, and what are the error messages that you are getting. 
We understand that it is pretty frustrating to try a new operating systems and encounter problems, 
but there is no way somebody can help you without specific information.

---

