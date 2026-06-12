---
title: "[SOLVED] Ubuntu will not shut down"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by satipera on 2008-07-31
hardy running on quad core 64 bit. I can log on and run no problems. I can get to the username input and shut down no problems. but when I log on and then try to shut down the desk top icons disapear and I am left with the desktop background ad infinitum, any ideas?

---

### Post by TBOL3 on 2008-07-31
HMM..  I had a similar problem when I installed KDE ontop of ubuntu.  Did you do anything like that?

---

### Post by satipera on 2008-07-31
no i am just running gnome

---

### Post by jualin on 2008-07-31
Try this > sudo shutdown -h now and check if your computer shutsdown.

---

### Post by satipera on 2008-07-31
sudo shutdown -h now works

---

### Post by jualin on 2008-07-31
I had a similar problem when I installed an old version of a theme for Gnome. Have you installed any themes for Gnome?

---

### Post by satipera on 2008-07-31
no it is ordinary gnome theme, I can't think of anything I have done apart from install a programme or two

---

### Post by Pconfig on 2008-07-31
Same problem here .. I do have some other theme for gnome but i had that a long time before this started happening. Also when booting, some parts load way slower. It takes like 3-4 minutes before the network, bluetooth and battery icon appear. That started happening at the same time (the computer is doing nothing in the meantime, not loading anything)

I think it's a gnome problem..

---

### Post by Pconfig on 2008-07-31
Alright, seems i've found my problem. After finally getting my guts together to try and fix the problem thinking i'd end up in alot of config files again the fix was pretty simple.

Seems like there was 0 bytes of free space on the disc ubuntu was installed on. Making some free space and then rebooting fixed the problem!

---

### Post by jualin on 2008-08-01
I dont know why you have the problem maybe you should check the kernel messages when the computer is shutting down or maybe installing a dock and checking if by clicking the Shutdown button in the dock your computer turns off. Maybe there is something wrong with your panel. For now at least you can shutdown by the terminal and you can make a launcher (shortcut) that you can click temporalily to shut down your system. Let me know if you need help creating the shortcut. Hope this helps!

---

### Post by satipera on 2008-08-04
Re: Ubuntu will not shut down
Alright, seems i've found my problem. After finally getting my guts together to try and fix the problem thinking i'd end up in alot of config files again the fix was pretty simple.

Seems like there was 0 bytes of free space on the disc ubuntu was installed on. Making some free space and then rebooting fixed the problem!


The ext 3 partition I have linux installed on is only 9% full so a full disc would not appear to be ther problem

---

### Post by jualin on 2008-08-05
I am glad everything worked fine! Having to shutdown your computer every time using the terminal can be a pain. Greetings from Miami, FL. ;)

---

### Post by satipera on 2008-08-13
To repeat my disc seems to be only 9 percent full so this does not seem to be the problem, could it be one of the parts of the disc that ubuntu  is installed on being full which could be the problem?  root or home or whatever?

---

### Post by E-mol on 2008-08-13
I'm in same situation.
I have 10 GB free on the partition i have Linux on.
It could be a problem with my panel, i have had a problem where the panel didn't load, then i tried installing it and that helped. But the shut down button only close programs, remove panels and icons on my desktop.
And yes, its really a pain shutting down in the terminal all the time.

---

### Post by satipera on 2008-08-20
seems to be a problem repeated on multiple systems can any clever person tell me how to shut my ubuntu system down without going to shutdown -h?

---

### Post by 4Orbs on 2008-08-20
I had a similar problem, where Ubuntu would shut down but not turn off the power. You might try the fix that worked for me on [THIS PAGE]("http://ubuntuforums.org/showthread.php?t=396418") near the bottom.

P.S. You gotta reboot once before this will work.

---

### Post by satipera on 2008-08-20
added this to the file rebooted and still no joy :-( but ty for suggestion more help is required please

---

### Post by linuxguymarshall on 2008-08-20
There is a magical thing called a power cable.....or a battery....

---

### Post by satipera on 2008-08-20
Please I am trying to sort a genuine problem if you have nothing constructive to say close your mouth and engage your brain

---

### Post by 4Orbs on 2008-08-20
If you suspect you may be running out of room, you can try cleaning out some junk. Try:

gksudo aptitude autoclean

after a few moments, you will see how much space was freed, if any.

---

### Post by satipera on 2008-08-20
Ty for the help I did as suggested 51 mb cleaned up ubuntu will still not shut down except for using  -h shutdown

---

