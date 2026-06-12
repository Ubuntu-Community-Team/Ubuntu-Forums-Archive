---
title: "how do I share /home"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by lance bermudez on 2008-05-13
Hi I have been trying to share my /home/lance folder where /lance is the name of the user for ubuntu hardy. Last time i loged in it errored out and said i needed to chage the folder back to 644 so i sudo chmod 644 /home/lance now it does not work it just says tried to enter a safe login and then freezes. Also Is their a command that will let me see what my chmod settings is? Do i just need to rebuil my computer? attached are my fstab file and smb.conf i copyed off using an old live cd.

---

### Post by kirios on 2008-05-13
If you're without a graphical login, press *Ctrl-Alt-F1* to get a console login, then type **ls -l /home/lance** and post the output here.

> **lance bermudez said:**
> Hi I have been trying to share my /home/lance folder where /lance is the name of the user for ubuntu hardy. Last time i loged in it errored out and said i needed to chage the folder back to 644 so i sudo chmod 644 /home/lance now it does not work it just says tried to enter a safe login and then freezes. Also Is their a command that will let me see what my chmod settings is? Do i just need to rebuil my computer? attached are my fstab file and smb.conf i copyed off using an old live cd.

---

### Post by lance bermudez on 2008-05-13
ctrl+alt+f1 gave me a black screen with now command line. so i used the recover tool from grub to get a command line. the command *ls -l /home/lance*  errored out so I used cd /home to get into the /home dir and then ls -l and then I used cd /lance to get into the /home/lance dir and then used ls -l againe. do not know if this is what you wanted.

---

### Post by lance bermudez on 2008-05-13
i dont think i said this be fore but i did have the computer set to auto login with out haveing to enter a user name and password. is that why the ctrl+alt+F1 did not work?

---

### Post by kirios on 2008-05-14
You have indeed changed the permissions on /home/lance to 644. Can you post the output of **dmesg | tail**? 

> **lance bermudez said:**
> ctrl+alt+f1 gave me a black screen with now command line. so i used the recover tool from grub to get a command line. the command *ls -l /home/lance*  errored out so I used cd /home to get into the /home dir and then ls -l and then I used cd /lance to get into the /home/lance dir and then used ls -l againe. do not know if this is what you wanted.

---

### Post by lance bermudez on 2008-05-15
Well I have used chmod 755 to set the home folder back to the right permissions. The 644 was to the gnome-session setting for the .dmrc file in the /home folder. I now have a gui. How do i mount the /home share on my other linux box also running hardy? I use the Places>Network>linuxwin2k where the other /home is seen but can not get to the home folder but i can get to the other harddrive at linuxwin2k. It says home will not mount with the error "Unable to mount location Failed to mount Windows share" this I find strange becuse last I check i could get to it from windows 2000 after i enter a user name and password. But it never ask for a user name and password. I have the same user name for both computers but different passwords. attached is both smb.conf for both computers and the dsm|tail

---

### Post by kirios on 2008-05-15
This may be useful:

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

EDIT - Read this first: 

[http://ubuntuforums.org/showthread.php?t=772706]("http://ubuntuforums.org/showthread.php?t=772706")

> **lance bermudez said:**
> Well I have used chmod 755 to set the home folder back to the right permissions. The 644 was to the gnome-session setting for the .dmrc file in the /home folder. I now have a gui. How do i mount the /home share on my other linux box also running hardy? I use the Places>Network>linuxwin2k where the other /home is seen but can not get to the home folder but i can get to the other harddrive at linuxwin2k. It says home will not mount with the error "Unable to mount location Failed to mount Windows share" this I find strange becuse last I check i could get to it from windows 2000 after i enter a user name and password. But it never ask for a user name and password. I have the same user name for both computers but different passwords. attached is both smb.conf for both computers and the dsm|tail

---

