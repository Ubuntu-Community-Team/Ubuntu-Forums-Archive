---
title: "Hardy heroin Crash...."
date: 2008-05-03
forum: New to Ubuntu
---

### Post by yimmmy on 2008-05-03
ok heres my deal , 
i recently decided to upgrade to ubuntu 8.04 (from gusty)
the installation went perfectly fine , it finished and i was told to reboot so.. ,thats were it all went wrong after the system rebooted i got to the splash loading screen and it went threw then brought me to a black screen with no response at all no "three finger salute" no ALT-f-- any thing ,so i decided to restart again and go into the grub menu , what i did there was, 1 reconfigured my x server (thinking that was the problem) 2, restarted in a recovery  kernel 3 restarted in an older kernel 4, loged in threw the root shell... but.. no luck 

i would nt be making a huge fuss about it if i didnt just move (no back up s) 40 gigs of personal photos onto this boxx

right now after 4 hours of booting (dont ask why it took 4 hours im clueless to that ) im in the live cd and trying to get those photos back , yet again another problem .. when i go to copy my photos to my flash its telling me i have no permission to do this , if any one could post a cmd for granting permission to copy these files  my worries will be over


thanks

---

### Post by Moop on 2008-05-03
```
gksudo nautilus
``` should get you permission to copy your files.

---

### Post by WitchCraft on 2008-05-03
> **yimmmy said:**
> ok heres my deal , 
i recently decided to upgrade to ubuntu 8.04 (from gusty)
the installation went perfectly fine , it finished and i was told to reboot so.. ,thats were it all went wrong after the system rebooted i got to the splash loading screen and it went threw then brought me to a black screen with no response at all no "three finger salute" no ALT-f-- any thing ,so i decided to restart again and go into the grub menu , what i did there was, 1 reconfigured my x server (thinking that was the problem) 2, restarted in a recovery  kernel 3 restarted in an older kernel 4, loged in threw the root shell... but.. no luck 

i would nt be making a huge fuss about it if i didnt just move (no back up s) 40 gigs of personal photos onto this boxx

right now after 4 hours of booting (dont ask why it took 4 hours im clueless to that ) im in the live cd and trying to get those photos back , yet again another problem .. when i go to copy my photos to my flash its telling me i have no permission to do this , if any one could post a cmd for granting permission to copy these files  my worries will be over


thanks

That's exactly why you should do a backup BEFORE you update...

The command line way is this:
su root
<enter password>

change to your pictures directory.

type:
cp -R ./*  /media/<YOUR_FLASHDISKS_MOUNTNAME>

then check whether all data has been copied...
Especially check whether subdirectories have been copied, and whether not just the directories have been copied, but also the data...

---

### Post by yimmmy on 2008-05-03
> **Moop said:**
> ```
gksudo nautilus
``` should get you permission to copy your files.
this worked but my disk isnt mounted ,

> That's exactly why you should do a backup BEFORE you update...

The command line way is this:
su root
<enter password>

change to your pictures directory.

type:
cp -R ./* /media/<YOUR_FLASHDISKS_MOUNTNAME>

then check whether all data has been copied...
Especially check whether subdirectories have been copied, and whether not just the directories have been copied, but also the data...
im using the live cd i dont know what the password is for root

---

### Post by raul_ on 2008-05-03
> **yimmmy said:**
> this worked but my disk isnt mounted ,


im using the live cd i dont know what the password is for root

there is no password

---

### Post by yimmmy on 2008-05-03
its asking me for a password.?

---

### Post by WitchCraft on 2008-05-03
> **yimmmy said:**
> this worked but my disk isnt mounted ,


im using the live cd i dont know what the password is for root

Well, on the live CD, there is no root password...

To mount a file system:

1. Create a mount directory
mkdir –p /media/pen
mkdir –p /media/mydisk

2. Mount the Flash Pen using the mount command:
mount /dev/sda1 /media/pen

3. Mount your harddisk:
mount /dev/hda1 /media/mydisk

---

### Post by yimmmy on 2008-05-03
well yes the disks are already mounted its just it dosent give me permission to copy the files off the disk that previously had ubuntu on it

---

### Post by Moop on 2008-05-03
When it asks for the password just hit enter and it should work.

---

### Post by yimmmy on 2008-05-03
i tryed that its says " authentication faliure " tryed ubuntu tryed password tryed my old pass.
nuthing

---

### Post by Moop on 2008-05-03
If you're using the live cd then gksudo nautilus should work without a password. Does a  nautilus window open even though you get a error message? Close any open windows except the terminal and run ```
gksudo nautilus
```.

---

### Post by yimmmy on 2008-05-03
yes  the windows opens but the disks arent mounted in that window

---

### Post by yimmmy on 2008-05-03
Ok ok i restarted and did   
"sudo nautlis " and it worked fine ?? for some reason my files werent there last time i booted 
i can now R,I,P 
thanks for your help

---

### Post by fesk on 2008-08-21
but how can you !degrade! from hardy heroin down to 7.10 ? i dont want to formate and install 7.10 over again, i dont want all of my stuff to go away..

---

