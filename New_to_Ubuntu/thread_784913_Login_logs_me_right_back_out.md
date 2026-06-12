---
title: "Login logs me right back out"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Scott.Mattes on 2008-05-06
Windows XP SP1 Home
Ubuntu 8.04 kernel 2.6.24-16-generic

Memtest menu option reported lots of things, what I wrote down was
Athlon 64(0.09) 2189MHz

the Wubi install seemed to go thru with no problems. I rebooted and the Ubuntu install seemed togo thru with no problems. Rebooted and selected Ubuntu and startup seemed to go with no problems. Typed in my user and password, hear the welcome sound, a couple of seconds later I hear the goodbye sound and the prompt for user is displayed again.

I did click on Options and select a safe boot, sorry, can't remember wording, and I am now on Ubuntu, but that isn't the way that I want to logon each time, is it?

I'd like to try Ubuntu out, but this is kind of a show stopper.

Thank you.

---

### Post by girishv on 2008-05-06
Hi,

Can you post the output of .xsession-errors which might give an idea of what is happening.
Type ctrl+alt+F1 to open a virtual terminal, login with your id and check the above said file (.xsession-errors). 
If this is the first time you are trying to login and the login is failed, that might be because of the stale files left in /tmp directory. You can also try to delete all the files/directories in /tmp and try to login again using GDM.

Girish

---

### Post by jperson on 2008-05-15
Hey i'm still a bit new at this i am having the same problem i typed in ctrl+alt+f1 and got a terminal i logged in and typed in .xsession-errors to the command line. as far as clearing /tmp i'm unsure of what temporary folder ur speaking of. just was well i did a search and found only one folder called tmp and cleared it's contents despite this still not getting anything.

I'm runing windows xp, this is my first experience with wubi and i've tried uninstalling and reinstalling it countless time. A few times the reinstalation process has been buggy otherwise (at least for this current install) things ran smoothly.  A friend suggested i make sure to install the 32 bit version of ubuntu since i have an amd processor, this is the last install i'm working with. I appreciate any help you can give me about this. 

-Jerry

---

### Post by jperson on 2008-05-15
btw it would seem the original poster and i both have AMD anthlon 64 processors and about the same processing speed. Not sure if that's useful

---

### Post by markbuntu on 2008-05-15
This happened to me when I first installed 8.04 but I could go to the icon on the bottom left corner and change session to Gnome safe mode and get into gnome. If this works for you go click on System /Administration/ System Log in the menu on the top left. Click on kern.log and look for an error or missing file or process message. 

I found one at (pam) that told me that security/lib/pam_smbpass.so was missing so login authentication failed or something like that. I then went to System/Administration/Synaptic Package Manager. searched for pam_smbpass.so and installed it. rebooted and I could log in. You could have a similar problem but with another file but the procedure would be the same.

You could also do this from the terminal using apt but I am not familiar with that procedure.

What is weird is that when I used the same installation disk a second time this did not happen on the same machine. I also have an Athlon64 processor but a 3800+

---

### Post by jperson on 2008-05-16
Hey thanx for the reply, i got as far as loging into safe mode. When i checked Kern.log there were no errors there that i could see that pertained to the login issue. the auth.log did show the pam_smbpass.so error but doesn't cite it as a reason for the problems. Just as well i tried to install it but i'm still pretty new and don't appreciate hwo to use to package manager. I reinstalled samba and libpam... to no avail. Any more help you could provide would be greatly appreciated.

---

### Post by markbuntu on 2008-05-17
Open Synaptic, it will ask for you password but you probably have that figured out already and use the search to find pam_smbpass.so then mark it for installation and click the apply button. then use nautilus and do a search for it to check if it is actually installed. Then use ctrl alt backspace to reboot and see if you can log in. If you still can't then look for another message about a missing file in the logs.

I do not think that libpam or samba includes pam_smbpass.so so you need to get it separately. That is what I had to do. There was also another file missing and I had to get that package too but I don't remember what it was.

Interestingly, when I did a new clean install with the same cd, I had no problem with this at all.

---

### Post by jperson on 2008-05-17
i very much appreciate your help sir, i just fixed it and logged in to tell you so when i got ur last post. I downloaded an 8.04 iso and moved it to the windows side of things, i uninstalled wubi, and tried the instal from a virtual drive mount of the iso. I alocated about 15 gb the first time, when i srestarted the instlalation either hung on some process with the partitions or maybe i didn't wait long enough, eithe ways i did ctrl alt backspace, and tried to log in, predictably it would let me. One more attempt at an install yielded the same result. tried the install one more time with a 4 gb alocation and that worked (further suggesting i was impatient). It still woudlnt' let me log in but there was a message asking for me to update software and some hardware (ATI...) i did, and upon restart everything worked beautifuly.

I can't tell you how much i've appreciated you working with me. If i didn't know how to get to safe mode i would've been hoplessless switching back and forth to try all my supposed fixes. 

Thank You!

---

### Post by markbuntu on 2008-05-18
No problem. I am pretty new to this myself and people helped me so it is good that someone as new as me to this could help another noob over the hump.

---

### Post by Xiong Chiamiov on 2008-05-18
I don't have any solutions to your current problem, but I'd like to say a few things.

First, read [how to install things in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").  It's a great guide, and I recommend it to people all the time.

Second, the file system in Linux is a bit different than what you are used to in Windows.  Everything branches off of the root directory (indicated by a /).  Anything that begins with a / starts off there.  So then, if I'm in a terminal and I use cd (change directory) like this
```

cd /tmp

```
then I am saying "go to the highest point on the file system, then down into the folder named tmp".  That contrasts from 
```

cd tmp

```
which moves into the directory named tmp that's in the folder I'm currently in.

I realize that was perhaps a bit confusing, but hopefully you understand a little bit more.

---

### Post by markbuntu on 2008-05-18
anyway, what you want to search for in Synaptic is libpam_smbpass, not pam_smbpass and install it if you have this problem. Sorry for the earlier misinformation but if you get a message like this in your auth.log you will not be able to log in except for in Gnome failsafe without the libpam_smbpass.so package installed.

May 18 00:01:27 mark-desktop sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

---

