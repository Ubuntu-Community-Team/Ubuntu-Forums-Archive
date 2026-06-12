---
title: "Distro randomly breaks"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by DenyingProduct on 2013-10-20
I recently (about half a year) started using Linux and I love it, it is truly amazing and I would like to thank everyone who made it possible but recently I ran into an issue i've had in the past. The distro just broke randomly!! no update no major change just one day boom it wont boot. this has happen to me 3 times now on 2 different machines while running ubuntu. It is a real pain in the *** to have to reformat everything and have to get it back to the way i had it and re install everything every few months because it breaks. I have tried being extremely careful and not working with anything i directly understood, I didn't understand and i didn't even have that many programs installed besides a few basics one. However here we are it freeze.

I am currently running Ubuntu 13.04 x64 on a Lenovo s405 
I have two kernels from the looks of things; 3.8.0-31 and 3.8.0-19.
Everything was working perfectly fine before it just wont boot one day
the only thing was i did get a notification about the new version of Ubuntu but i didn't get a chance to start the download or the install.
it gets stuck on the Ubuntu loading circles[INDENT]Note: i have changed the config files to show me what ist actually doing in attempt to fix this and it gets stuck at a random point in the start up
Sometimes it gets stuck at "starting network connection manager"
Sometimes it gets stuck at "CUPS printing spooler/server"
Sometimes it get stuck at "battery state..."
from the looks of it it is completely random.[/INDENT]
I am looking to fix this because i truly do love Ubuntu and linux but i cant be reformatting every few months. I am more than willing to provide any information you ask for and i will try anything as i am on my last attempt.

Backgroung: novice computer programmer and linux user || Am very confident using terminal so feel free to help by leaving any code to troubleshoot or anything

Thanks a ton you guys are great and i love the ubuntu community and being a part of it.

---

### Post by fantab on 2013-10-20
Check the /var/log directory, it is a good place to start.
[http://askubuntu.com/questions/244387/how-to-diagnose-random-freezes?lq=1](http://askubuntu.com/questions/244387/how-to-diagnose-random-freezes?lq=1)
[http://www.thegeekstuff.com/2010/10/dmesg-command-examples/](http://www.thegeekstuff.com/2010/10/dmesg-command-examples/)
[http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/)
These should get you started. I suspect some hardware problem though... check the lenovo service center.

meanwhile post the output of:
```
dmesg | less
``` 

Good Luck...

---

### Post by DenyingProduct on 2013-10-20
Thank you i'm reading up on the post you provided now and will try something. I did notice something last night while tinkering with it, Only kernal 3.8.0-31 freezes but kernal 3.8.0.19 will do a full boot but the gui will not load i would get an error no mouse then dropped into command shell, From there i can log in as me and look at my files and i was even able to open some with emacs -nw

-ps i highlydont think it's hardware issues as it is a new machine and ive had this problem before on diffrent machines. Also I've worked at a repair shop for a while and everything seems fine on this machine. I think it is much more likely i didn't do an update correct or some file got corrupt as like i mentioned i am still new to linux

I did install AMD graphic drivers from their website but that was a while a go before the issue occurred but maybe with the kernal update they didn't work anymore? (I don't actually know how to check just ideas i'm tossing around)

---

### Post by QIII on 2013-10-20
Hello!

If you installed the proprietary driver directly from the AMD website, then I would say it is likely that that is your problem.

If the driver is not installed from the repo, your package management system does not know it exists and does not roll it back into the kernel, but some configuration is still in place.  If you install directly from AMD, you should uninstall the driver before executing any updates involving the kernel and reinstall it when done.

If you can get to recovery mode and use the terminal, you can try to completely uninstall it.

First, rename your xorg.conf file if it exists

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```

and then use the ATI tool for removing the driver

```
sudo amdconfig --uninstall
```

Let us know if you get anywhere with that.

---

### Post by DenyingProduct on 2013-10-20
do you want me to make a cp? or do you want me to mv so that the existing xorg.conf is no longer there but is replaced with .bak one

also following what the first link suggested i copied my Xorg.0.log and syslog files to a usb, Would uploading them help at all? also im not sure how to (still new to forums)

---

### Post by DenyingProduct on 2013-10-20
PROBLEM SOLVED! thank you so much guys 


> [COLOR=#000000]you should uninstall the driver before executing any updates involving the kernel and re install it when done. - QIII[/COLOR] 

Was more than likely the cause of this error in the past! You guys are awesome and responded so fast! if there's anything i can do to for you guys feel free to ask.

Again for clarification and future use what i did to resolve the issue was remove the proprietary AMD drivers that caused an issue when something (probably the kernel) updated. I did this by running the commands provided by QIII, After a reboot the computer turned on perfectly fine!

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
sudo amdconfig --uninstall
sudo reboot
```

---

### Post by QIII on 2013-10-20
Actually, I did mean ***mv*** (but as you have found out it worked anyway) and I edited my post.  

It is best not to have an xorg.conf when using the default driver (which is installed with Ubuntu) and create one with amdconfig after installing fglrx.

So, if you uninstall the driver, you should rename xorg.conf.  I don't like to tell people to remove it right off, because in some cases you may want to have it later.

---

### Post by DenyingProduct on 2013-10-20
Thanks that's really helpful I understand now and that was probably the issue that has been plaguing my Linux experience :) 

you guys are great btw and inspired me to give back to the forum so i posted this:
[URL="http://ubuntuforums.org/showthread.php?t=2182227&p=12822215#post12822215"]
http://ubuntuforums.org/showthread.php?t=2182227&p=12822215#post12822215[/URL]

i'm sure someone will find it useful

---

