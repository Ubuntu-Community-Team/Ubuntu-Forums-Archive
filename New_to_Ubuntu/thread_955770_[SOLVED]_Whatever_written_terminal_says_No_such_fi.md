---
title: "[SOLVED] Whatever written terminal says: No such file or directory"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by amelie on 2008-10-22
Hi there!
I'm trying to install ndiswrapper in order to handle the windows drivers for my D-Link wireless usb adapter. I downloaded the tar.gz package and extracted it (it didn't happen the way it was pointed in the INSTALL file, because the package was in the home directory and the answer of the terminal No such file or directory anooyed me...) So i extracted it the regular way -> on the Desktop and when trying to change to the folder: ndiswrapper-1.53 by the command: cd /Desktop/ndiswrapper-1.53, it keeps telling me: NO such file or directory... 
Thanks for reading my complaints, i'm just too upset being unable to run my internet :)

---

### Post by MrWES on 2008-10-22
try cd ~/Desktop/ndiswrapper-1.53

which is the same thing as cd /home/Desktop/ndiswrapper-1.53

Bill

---

### Post by sisco311 on 2008-10-22
type:
```
cd
```press space and drag and drop the folder in the terminal window, then press enter.

---

### Post by amelie on 2008-10-22
Bill: No change...
sisco311: i always copy the filename right from the folder on my desktop if you think i just make spelling mistake ;) But when i did this it just opened a file browser, it didn't make my way to the directory

---

### Post by oldos2er on 2008-10-22
> **amelie said:**
> Hi there!
I'm trying to install ndiswrapper in order to handle the windows drivers for my D-Link wireless usb adapter. I downloaded the tar.gz package and extracted it (it didn't happen the way it was pointed in the INSTALL file, because the package was in the home directory and the answer of the terminal No such file or directory anooyed me...) So i extracted it the regular way -> on the Desktop and when trying to change to the folder: ndiswrapper-1.53 by the command: cd /Desktop/ndiswrapper-1.53, it keeps telling me: NO such file or directory... 
Thanks for reading my complaints, i'm just too upset being unable to run my internet :)

 Your command "cd /Desktop/ndiswrapper-1.53" is incorrect, because the leading "/" tells bash to start looking from the root directory. The proper command would be "cd /home/[username]/Desktop/ndiswrapper-1.53". Replace [username] with your user name.

---

### Post by northern lights on 2008-10-22
You neglected "*/home/USER/*, where USER is your username, before *Desktop/...*

further get acquainted with the TAB key's function to the bash shell. It's autocompletion helps a lot when trying to avoid this exact error.

---

### Post by amelie on 2008-10-22
I think I did it guys! Thank you very much :)!!!

---

### Post by jerome1232 on 2008-10-22
edit: yeah I was a bit late :)

As oldos2er stated the leading slash makes it incorrect. should be one of these three (assuming your pwd is your home directory). ~/ means /home/currentusersnamehere

```
cd Desktop/ndiswrapper-1.53
cd ~/Desktop/ndiswrapper-1.53
cd /home/*usernamehere*/Desktop/ndiswrapper-1.53
```

---

### Post by sadimus on 2010-02-23
Ok here's my problem. I'm trying to install windows 7 unto my netbook. The problem is I've hit a roadblock, I'm using an intel mac to prepare my flash drive so it can be bootable. I unmounted it using diskutil unmountDisk /dev/disk2
Unmount of all volumes on disk2 was successful 

Which you can see was succesful. Now im trying to mount the windows7.iso image unto the flash drive and i keep getting this error. The image is on my desktop. Am I not specifying the path properly?

sudo dd if=/home/sadiq/windows7222.iso of=/dev/disk2 bs=1m
dd: /home/sadiq/windows7222.iso: No such file or directory



Can someone point me in the right direction please???

---

### Post by anjilslaire on 2010-02-23
list the content of your home directory:
<code>ls</code>

Also, remember: Linux is case-sensitive. If the file is Windows7222.iso, its not windows7222.iso

---

### Post by TheDolt on 2010-10-22
> **oldos2er said:**
> Your command "cd /Desktop/ndiswrapper-1.53" is incorrect, because the leading "/" tells bash to start looking from the root directory. The proper command would be "cd /home/[username]/Desktop/ndiswrapper-1.53". Replace [username] with your user name.

I was doing something different but this worked like a charm! Thanks!!:)

---

