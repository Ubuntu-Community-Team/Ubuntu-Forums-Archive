---
title: "How to auto mount a truecrypt encrypted volume on logon?"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by Anakunda on 2012-01-07
Hello, can't find a solution how to make this process fully unattended. What I'm struggling with is how to get rid of entering admin password for each volume.

So far I have managed the commands which do the whole job as I expect:

truecrypt --protect-hidden=no --keyfiles=/home/Anakunda/Documents/TC.key /dev/sda7 /media/sda7
truecrypt --protect-hidden=no --keyfiles=/home/Anakunda/Documents/TC.key /dev/sda8 /media/sda8
truecrypt --protect-hidden=no --keyfiles=/home/Anakunda/Documents/TC.key /dev/sda9 /media/sda9

It works fine just with the problem I have to enter admin password for each mounted container.
Any chance to "bless" truecrypt as trusted application, or to make it mount the volumes without requesting admin password each time? I don't mean the password to encrypted containers but password for administration tasks of Ubuntu.

---

### Post by Anakunda on 2012-01-07
Update - adding 
anakunda ALL=NOPASSWD: ALL into sudoers also doesnot seem to fix the problem.
I'm still asked for password.

Changing the command to 

sudo truecrypt --protect-hidden=no --keyfiles=/home/Anakunda/Documents/TC.key /dev/sdaX /media/sdaX

even does nothing at all

---

### Post by Anakunda on 2012-01-18
Really nobody can't help? I'm pretty sure it must be possible.  This is where I stuck at:

having these commands in ~/.profile works but requires extra admin password for each mounted container:
```
truecrypt --protect-hidden=no --keyfiles=~/Dokumenty/TC3.key /dev/sda7 /media/sd7
truecrypt --protect-hidden=no --keyfiles=~/Dokumenty/TC3.key /dev/sda8 /media/sd8
truecrypt --protect-hidden=no --keyfiles=~/Dokumenty/TC3.key /dev/sda9 /media/sd9
```

---

### Post by ubudog on 2012-01-18
This might help you:
[https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

---

### Post by Anakunda on 2012-01-18
Bad luck, the essay only deals with general TrueCrypt usage but not how to start Linux with containers automounted.

---

### Post by mikaelcrocker on 2012-01-18
Have you tried using /etc/fstab file to enter in the command line? I dont' know if you want it at boot, but  this is a great way to go.

---

### Post by Anakunda on 2012-01-19
Yep I'm using fstab successfully for mounting conventional file-systems, but I'm afraid encrypted volume needs 3rd party handler for it, would you have an idea what syntax to use for fstab?

---

### Post by FFabian on 2012-01-19
Please excuse my ignorance and missing help but I'm curious. Why do you automount an encrypted volume?  It seems to defeat the purpose of encrypting something when you never ask for a password.

---

### Post by Anakunda on 2012-01-19
> **FFabian said:**
> Please excuse my ignorance and missing help but I'm curious. Why do you automount an encrypted volume?  It seems to defeat the purpose of encrypting something when you never ask for a password.
Using a key file from my home dir which is encrypted (I believe so) is ok.

---

