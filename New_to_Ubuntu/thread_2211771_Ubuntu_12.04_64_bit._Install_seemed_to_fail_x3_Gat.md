---
title: "Ubuntu 12.04 64 bit. Install seemed to fail x3 Gateway dx4822-01"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by bostoncab2 on 2014-03-17
Ubuntu 12.04 64 bit. Install seemed to fail x3 Gateway dx4822-01

I installed everything seemed to go find made it to the reboot and remove disk part and I get no boot. Just a blinking curser. Tried to boot HD from boot menu.. still no boot. 

Running on live disk now. 

Tried multiple times to reinstall and no luck. 

Looking for advice on how to troubleshoot here.. not sure if I am having a software issue or some type of hardware needs to be replaced. Any help is appreciated. 

I even tried turning it off and then on again.

---

### Post by rollingthunderb on 2014-03-17
Hi and welcome. Yes that is frustrating. Sounds graphics related to me, but that's just a hunch. Been there thinking it all went well and probably did.

Do me a favor... make sure the cd/dvd disk is removed and reboot. As soon as the reboot starts hold down the shift key and keep holding it for what will seem like way too long. Keep holding it down until you see a boot menu. If you didn't start holding it down from the beginning, just power off and start it again.

What I want to see is if you see the grub boot loader.

It'll be a black and white text screen with a few things in a list in the top left of your screen.

*right when/if you see this, press the "down arrow" key to move the selection and stop the timer.

If you get this far we're in good shape. I'll respond with more later.

---

### Post by bostoncab2 on 2014-03-17
ok i tried that a bunch of times and no luck.. takes forever to boot back into the live cd. Is there a way I can check from the live cd to see if the files are on the hd and installed as they should be?

---

### Post by rollingthunderb on 2014-03-18
Hi,

I'm sorry that isn't working. Yes you can see the files if they are there. In fact, I'm replying to this thread via a live "try" of 12.04 LTS x64. Not sure if it is the original or one of the early rollups. I didn't date the disk I made, but I know it is not current.
Initially Live took a while, and never gave me a gui, just a blinking cursor. The I remembered I may need a nomodeset option. rebooted my PC, and then at the menu where you choose try, I selected F6 for options and selected "nomodeset", escaped out of that tiny submenu and hit enter to boot the new boot string, and here I am.

[IMG]http://ubuntuone.com/4aH8gdjTgRZw8rVrZWd0uL[/IMG]

So over on the left hand dock, you should see a file folder. That is your file manager like windows explorer. Under devices you should see your partition(s). One of those should have a similar look to mine selected in the screen shot.

I'd recommend doing a new install and selecting nomodeset as described to see if you get a different outcome.

What I was going to post after you saw the boot menu was a post on how to make it perminant until you can get your updates done. But since you can't get seem to get to the boot menu, what's the point?

You can also do a reboot with the live cd removed and when you see the blinking cursor for a while, try pressing Cntrl + Alt + F1. See if that takes you to a text login screen. if it does, at least you know you have the install working, and we can begin working to get grub to enable nomodeset. 

I hope this gets you on the right track.

---

### Post by bostoncab2 on 2014-03-18
All of that was more or less way over my head. Perhaps there is something wrong with the live disk I burned? Is it at all possible to burn another live disk from within a live disk?

---

### Post by rollingthunderb on 2014-03-18
I'm not sure. I'm away from the machine that I used for the live install. 

I recommend you begin the install process again.

reboot the machine with the live CD loaded. 

watch the screen - early you should see at the bottom of your screen for a short time a set of small pictures "a figure in a circle and a keyboard". Press the space bar on your keyboard while this is showing to get a menu.

if you get there, you should see a list of 6 options at the bottom. to the right is press f6 for options, and select nomodeset with your arrow keys, and enter.

Let me know if you can make it this far.

---

### Post by bostoncab2 on 2014-03-18
Anyone else can tell me something here? This is a total failure.

---

### Post by oldfred on 2014-03-18
This outputs a ton of detail, post the link for us to review to see your install.
You have to copy and paste (one at a time) a couple of lines into terminal to install it after you reboot to DVD or flash drive. Or you can download as a full repair ISO.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by bostoncab2 on 2014-03-18
[http://paste.ubuntu.com/7117031/](http://paste.ubuntu.com/7117031/)

about to reboot.. wish me luck.

---

### Post by bostoncab2 on 2014-03-18
So the good news is that seems to have worjed and the install is now booting. The bad news is either the boot repair somehow changed my password or I forgot it ... im trying all my standard choices and no luck so far. Is there a way in without the password?

---

### Post by bostoncab2 on 2014-03-18
It seems to have worked but now im either getting the username and password wrong or idk... is there another way back in or am I doing another install?

---

### Post by rollingthunderb on 2014-03-18
Glad you're moving forward. This will require shift key again. Since holding it down didn't work, try tapping it over and over quickly.

[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by bostoncab2 on 2014-03-20
thanks all in now

---

### Post by rollingthunderb on 2014-03-20
Awesome news. Have fun.

---

