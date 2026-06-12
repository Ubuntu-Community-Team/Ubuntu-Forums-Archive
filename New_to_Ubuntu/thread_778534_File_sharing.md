---
title: "File sharing"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by paul.lav on 2008-05-02
Hi have just installed ver 8.04 desktop version but want to be able to share the files and printers on this computer.

i have tried installing samba using 
"sudo apt-get install samba"
but i just got the message "samba package is not available but is reffered to by another package. This may mean that the package is missing, has been deleted, or is only available from another source
however the following packages replacec it:
smbclient samba-common
E: Package samba has no installation candidate"

Help what do i do now

---

### Post by muteXe on 2008-05-02
I'm not at my home machine at the moment, but trying looking for samba in the package manager.  If you install it from here, it should automatically download all the dependancies that go with it as well.

---

### Post by mlentink on 2008-05-02
> **muteXe said:**
> but trying looking for samba in the package manager.  

System > Administration> Synaptic Package Manager
Click on 'Search', and enter 'samba'.
Scroll down until you see samba, and see if it's already installed. If not, tick the samba box and execute. Synaptic will take care of any dependencies for you.

---

### Post by Healey on 2008-05-02
Hi

You could try this method instead of Samba

I have have used it in Feisty, but have not tried it in Hardy yet

May be worth a read

Regards

Healey

---

### Post by njparton on 2008-05-02
You may have to configure your repositories via synaptic to ensure that they're all turned on and available.
 
Turn on the standard ubuntu repos, plus multiverse and universe.

---

### Post by paul.lav on 2008-05-02
> **mlentink said:**
> System > Administration> Synaptic Package Manager
Click on 'Search', and enter 'samba'.
Scroll down until you see samba, and see if it's already installed. If not, tick the samba box and execute. Synaptic will take care of any dependencies for you.

samba wasn't in the list there was samba-common but it was already installed.

now i'm really stuck

---

### Post by paul.lav on 2008-05-02
> **Healey said:**
> Hi

You could try this method instead of Samba

I have have used it in Feisty, but have not tried it in Hardy yet

May be worth a read

Regards

Healey

what method :confused:

---

### Post by paul.lav on 2008-05-02
> **njparton said:**
> You may have to configure your repositories via synaptic to ensure that they're all turned on an available.
 
Turn on the standard ubuntu repos, plus multiverse and universe.

:confused::confused::confused:
I'm a noob at this.
what does that mean in english or how do i do it.

---

### Post by Healey on 2008-05-02
Hi

I did post a link - not sure what happened !!!

Try this :

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

Regards

Healey

---

### Post by njparton on 2008-05-02
> **paul.lav said:**
> :confused::confused::confused:
I'm a noob at this.
what does that mean in english or how do i do it.
 
Open synaptic, in the options at the top go to the repositories screen, and tick all the repository entries on the 1st screen and make sure the CD-ROM option is turned off.

---

### Post by paul.lav on 2008-05-02
Did that and it appeared :)

---

