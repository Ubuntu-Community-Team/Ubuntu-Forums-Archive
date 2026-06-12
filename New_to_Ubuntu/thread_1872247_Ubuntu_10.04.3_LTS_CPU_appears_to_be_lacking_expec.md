---
title: "Ubuntu 10.04.3 LTS CPU appears to be lacking expected security protections"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by deadlytackler on 2011-10-30
Iam trying to dig into this to be able to boot into my ubuntu desktop. 

When i run: /usr/bin/check-bios-nx --verbose , i get this:
'This CPU is family 15, model 4, and has NX capabilities but is unable to use these protective features because the BIOS is configured to disable the capability. Please enable this in your BIOS. For more details, see: [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures) 

It seems to be a simple problem but i can't identify this feature in my BIOS, and alas, i am completely stuck, unable to boot into my desktop.

How to boot into desktop?

---

### Post by gandaran on 2011-10-30
> **deadlytackler said:**
> Iam trying to dig into this to be able to boot into my ubuntu desktop. 

When i run: /usr/bin/check-bios-nx --verbose , i get this:
'This CPU is family 15, model 4, and has NX capabilities but is unable to use these protective features because the BIOS is configured to disable the capability. Please enable this in your BIOS. For more details, see: [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures) 

It seems to be a simple problem but i can't identify this feature in my BIOS, and alas, i am completely stuck, unable to boot into my desktop.

How to boot into desktop?
are you sure it's not just a video driver problem?
what happens when you choose to boot Ubuntu from grub?

---

### Post by deadlytackler on 2011-10-30
> **gandaran said:**
> are you sure it's not just a video driver problem?
what happens when you choose to boot Ubuntu from grub?

How to do that?

---

### Post by deadlytackler on 2011-10-30
Let me explain, how this happened-
4days back i installed thunderbird and removed evolution and files ending with evolution (don't know exactly how many and which one).
Today when i tried to start my computer log in window appeared and after logging in terminal window appeared. when in tried to close it, it again directed me to login window and again this terminal. I tried to login in terminal and came to know about this security protection things. 
Now I want to get pass this thing and to get my desktop. I don't think video is a problem....

---

### Post by oldfred on 2011-10-30
I believe evolution (right or wrong) is part of the standard desktop in 10.04. So you may have uninstalled the entire desktop. When I install Thunderbird, I do not uninstall evolution.

If you can get to command line. # are comments, do not type or copy.

sudo -i
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by gandaran on 2011-10-30
> **deadlytackler said:**
> Let me explain, how this happened-
4days back i installed thunderbird and removed evolution and files ending with evolution (don't know exactly how many and which one).
Today when i tried to start my computer log in window appeared and after logging in terminal window appeared. when in tried to close it, it again directed me to login window and again this terminal. I tried to login in terminal and came to know about this security protection things. 
Now I want to get pass this thing and to get my desktop. I don't think video is a problem....
I believe when you removed evolution you also removed the ubuntu desktop as evolution is linked to ubuntu desktop
try booting to recovery mode (root) and run the install command
apt-get install ubuntu-desktop
that should fix the problem.

---

### Post by deadlytackler on 2011-10-31
> **oldfred said:**
> I believe evolution (right or wrong) is part of the standard desktop in 10.04. So you may have uninstalled the entire desktop. When I install Thunderbird, I do not uninstall evolution.

If you can get to command line. # are comments, do not type or copy.

sudo -i
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

Thanks got my desktop.

---

### Post by Grumblebum on 2012-07-19
I have the same problem as that listed here.  I run an old HP Compaq P4 2.8Ghz. dual booting with Windows 7.  Booted to Ubuntu two days ago and got the same message deadlytackler got.  Can't find the feature in BIOS, upgraded the BIOS and still can't find the feature.  Tried all the suggestions at [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures), to no avail.  Also tried the suggestion by oldfred.  Everything went smoothly, but still have no desktop, only a command prompt.  This was always a smooth running system and I only lost the desktop when I got the security message any assistance given would be much appreciated.  Distro is 10.04 if I remember correctly....

---

