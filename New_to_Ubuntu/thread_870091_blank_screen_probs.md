---
title: "blank screen probs"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by pinbrook on 2008-07-25
i am running ubuntu - my partner was messing with some desktop options and now he gets a blankscreen after booting - we hear the little drum roll andthen get left on a blank screen

i can do ctrl alt f1 and login

but am not sure what to do next, i have the prompt xxx@xxx:~$

i've read that sudo dpkg-reconfigure xserver-xorg might help, but can i run this command at the prompt i'm at

please excuse my caution, it just that he has just downloaded all images from his camera cardto the laptop and we don't want to do anything that will get us into worse strife. We were cosidering a simple reinstall, but that will kill our pics
TIA

---

### Post by DGortze380 on 2008-07-25
> **pinbrook said:**
> i am running ubuntu - my partner was messing with some desktop options and now he gets a blankscreen after booting - we hear the little drum roll andthen get left on a blank screen

i can do ctrl alt f1 and login

but am not sure what to do next, i have the prompt xxx@xxx:~$

i've read that sudo dpkg-reconfigure xserver-xorg might help, but can i run this command at the prompt i'm at

please excuse my caution, it just that he has just downloaded all images from his camera cardto the laptop and we don't want to do anything that will get us into worse strife. We were cosidering a simple reinstall, but that will kill our pics
TIA

I would recommend backing up your data losing it is a concern. you can do this with an external drive from the command line or by booting the live cd

---

### Post by pinbrook on 2008-07-25
sadly our knowledge is zero at the command line.  I had considered booting from a live CD but was relunctant to do this as i needed to be sure i wouldn't end up reinstalling by mistske

i guess i could download another CD as my only cd is the one we installed ubuntu to the disk with

---

### Post by DGortze380 on 2008-07-25
> **pinbrook said:**
> sadly our knowledge is zero at the command line.  I had considered booting from a live CD but was relunctant to do this as i needed to be sure i wouldn't end up reinstalling by mistske

i guess i could download another CD as my only cd is the one we installed ubuntu to the disk with

it's pretty difficult to install by mistake from a live cd. Just DONT double click the install icon. don't format anything. Just boot and copy the files you need.

or from the command line.

"ls" shows everything int he folder you're in
"cd" is change directory
"cp" is the copy command
"cp -r" for recursive
"sudo" gives you root privledges

where are the files you need to backup located? maybe we can give you specific commands to run if you're really that uncomfortable with the live cd.

---

### Post by ajgreeny on 2008-07-25
Before you do anything drastic or reinstall, which is most probably not necessary, and assuming you are on Hardy, reboot and hit esc when it gets to "starting grub", if you don't normally see the grub menu.  At the grub menu choose the second option, Recovery mode, wait for it to start and when you get to the option to do three things (I think there are three) use the cursor keys if needed to choose xfix.  This will go through the same procedures as when you first installed and should detect your graphics card etc etc.

I have never needed to use this system, but did in the past use the ```
sudo dpkg-reconfigure xserver-xorg
```with success.  Sadly, (or perhaps not, I can't say, never having used the new system), the dpkg route does not work now in the new version of xorg.  I hope this is useful to you and that it all works out OK.

---

### Post by pinbrook on 2008-07-25
thanks guys, i'll try those ideas and report back.  I'm off on hols for a week so it will be after that

---

### Post by pinbrook on 2008-07-26
ok this is how i resolved it

I tested my install CD on another PC and was confident i wouldn't reinstall by mistake, so i put the unbuntu disk in the rogue laptop and ran live CD - this allowed me to copy my photos to flash.

I then rebooted the laptop whilst i had a 2nd monitor attached, this then displayed properly on the 2nd monitor, and there was an error  saying there was a graphics driver conflict, it also offered the option to disable the driver.

Did that, disconnected 2nd monitor, rebooted, all ok!

---

### Post by Troll_the_Great on 2008-07-26
Glad the problem is solved.Please mark your thread as "solved" using thread tools.
Cheers!

---

