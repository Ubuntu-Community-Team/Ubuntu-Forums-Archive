---
title: "And I hit CTRL ALT DEL..."
date: 2021-07-11
forum: New to Ubuntu
---

### Post by Innernet on 2021-07-11
Greetings.
Trying Chrome browser on Lubuntu 20.04 for a couple of days now...  Started to freeze, resumed, then again very slow, then seemed frozen.

Hit CTRL ALT DEL... picked anything on the list as I do not know what am doing nor what they mean;  and... ---> no privileges to kill !    Had to waaaait for the screenshot to work and to save, but somehow it did.
Is this a Chrome thing, a Lubuntu thing, an old fart operator goof ?   I thought I was the only superuser and owner from day one.  Now am not.  :(

---

### Post by Impavidus on 2021-07-11
The error message tells you that only the superuser (=root) and the owner of a process can send a signal to it. You are not the superuser. You are the admin, so you belong to the sudo group and can use sudo to act as the superuser, but this process manager or how is it called is not running as root.

Instead, your user ID is 1000, so you can only kill processes with UID 1000. Chrome must be one of them. The processes with UID 0 are owned by root. You can also see a UID 7 in that list, that's another system user.

---

### Post by Innernet on 2021-07-11
Thank you, impavidus.
That is even more interesting.  Assuming the reports from CTRL ALT DEL correspond since the last powerup of the compfuser;  I just hit CTRL ALT DEL again to see what shows up and found several UIDs.  

If am 1000, The others have to be ghosts as _nobody has touched_ my compfuser in one year and power cycled at least a dozen times this week.  :(  Can the dethroning of me as superuser+owner be recovered ?  how ?


[ATTACH=CONFIG]288807[/ATTACH]

---

### Post by grahammechanical on 2021-07-11
If you was the only user on the operating system you would have to give permission for every system process to start and stop. So, certain system processes are given user ID's and certain levels of authority. This happens automatically from the moment the bootloader starts Linux and even before we login.

In order to prevent anyone with physical access to your machine from stopping important processes or changing important system configuration files you, when you login, are only a standard user. You are limited in what you can do. But prefix a command with the word "sudo" and enter your normal user password and you become the administrator with the power to completely and easily break the operating system.

As it is normal procedure on Ubuntu to work as a standard user anybody who gains physical access to the machine can only work as a standard user also. Of course, there is nothing stopping you from putting a post-it note on the monitor with your password written on it. :) 

This may help you to understand the use of the "sudo" prefix in Ubuntu. But please take note of the warnings given in this wiki page.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards

---

### Post by Impavidus on 2021-07-11
The other users aren't ghosts; they run various processes that were started automatically to do things in the background. I've seen no evidence for anything being wrong, except that chrome is a bit sluggish. How much memory and swap do you have, and how many tabs do you open in chrome? This smells like low memory, but poor graphics hardware or drivers could cause this too.

---

### Post by GhX6GZMB on 2021-07-11
Or it smells like a basic failed install followed by mucking around and making things worse...

---

### Post by guiverc on 2021-07-11
What box are using?

If it's got limited RAM like boxes I use, I can find browsers *lag* due to lack of memory, and for sure benefit with the use of swap.  Do you have swap enabled?

I'll provide the following link which applies to 20.04 - [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

Lubuntu installs from 18.10 to 20.10 did not automatically create *swap*, though they let you manually create it, and will use it if it was created before hand.  [Swap is now created by default from 21.04 and up]("https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591").

This may *not* be your issue, but I'd for sure check you are using *swap*, esp. if you've <6GB of RAM and even then likely create some anyway (if 6GB, 8GB..).

---

### Post by mastablasta on 2021-07-12
> **Impavidus said:**
> The other users aren't ghosts; they run various processes that were started automatically to do things in the background.

they are not ghosts but daemons.  

always there always watching, massing arround with computers... [CENTER][COLOR=#000000]:evil:  [/COLOR][COLOR=#000000]:-D[/COLOR][COLOR=#000000]
[/COLOR][/CENTER]
seriously, more about d**[COLOR=#ff0000]a[/COLOR]**emons here:
[https://en.wikipedia.org/wiki/Daemon_(computing)](https://en.wikipedia.org/wiki/Daemon_(computing))

>  I've seen no evidence for anything being wrong, except that chrome is a bit sluggish. How much memory and swap do you have, and how many tabs do you open in chrome? This smells like low memory, but poor graphics hardware or drivers could cause this too.


i had this 13" netbook thing. we split the kids into two rooms, so they could get some work done during school at home. and while it worked much faster under linux than it ever did on windows 7 starter, it was still slow when you opened firefox and libre office. it was driving him crazy. the laptop had 2 GB ram of which 512 MB is taken by the GPU. ofcourse the browser was using hard disk like crazy with 2 tabs open. so you could only do one thing on it. libre office or firefox with one tab. while it kind of worked it was far from ideal- 
so i saved up some money, did some research and upgraded the RAM with 2x 4GB sticks. now windows starter still uses only 2 GB as this is a software limit (wish that guy that hacked & patched the PAE kernel so it could use up to 128GB would do it one last time). but i use windows very rare, maybe to do a disk check on one of the external ntfs drives or to sign specific docs that need some elaborate widnows only application to do it.
 Kubuntu (64bit) on the other hand is flying on it. firefox can have more tabs open, i can work with 2 apps or even more at the same time. CPU is still very low end and slow but i've noticed it no longer goes up to 100% as often. so a small, cheap and worthy upgrade. ii am not sure why i haven't done this before. i bet it could go even faster if i upgraded with SSD, but at this point it seems like a big investment into a laptop that is not used much and that at the time of purchase cost me around 250 USD.

also i hate MS for having these artificial restrictions or at least not offering the home version which supported up to 8GB on this model. they could have at least unlocked the RAM restriction when this OS went EOL. but no let's everyone move to windows 10 and you will never have to upgrade again (until windows 11 comes and you can't upgrade).

---

