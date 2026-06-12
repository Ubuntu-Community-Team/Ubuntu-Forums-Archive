---
title: "not privileged?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by T2manner on 2008-06-26
i just installed a lot of updates and when i restarted my computer, my NTFS hdd wasn't mounted.
so i checked the ntfs configuration tool, and it was all right.
then i tried mounting it and it said i didn't have the privileges to mount it!?

wtc

---

### Post by oldos2er on 2008-06-26
Use "sudo mount ..."

---

### Post by T2manner on 2008-06-26
yeah... nothing happened...

and i would like to be able to do SOME things without having to use the terminal.

---

### Post by oldos2er on 2008-06-26
> **T2manner said:**
> yeah... nothing happened...

 If you mean nothing happened when you entered "sudo mount /something /somewhere" in the terminal, that means the command completed successfully. If you mean something else, please say.

[quote=and i would like to be able to do SOME things without having to use the terminal.[/quote]

 You can do most things without the terminal.

---

### Post by T2manner on 2008-06-26
well.. i'm not exactly sure how to do the command.
so it's sudo mount then what?

---

### Post by bodhi.zazen on 2008-06-26
Well, the classic link on these forums is :

[uhelp]comminity/RootSudo[/uhelp]

But also permissions.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

ownership and permissions separate users from system files and each other and are a part of security on a *nix system. When you run an application such as firefox it can not alter (in theory) system files. If you were to open a virus, it would contain it to your /home.

---

### Post by oldos2er on 2008-06-27
Say you had a partiton you wanted to mount, /dev/sda7 . First you need to create a directory to mount it in:

 sudo mkdir /media/sda7

Then:

 sudo mount /dev/sda7 /media/sda7

 Also see [https://help.ubuntu.com/community/Mount?highlight=(mount](https://help.ubuntu.com/community/Mount?highlight=(mount))

---

### Post by Paqman on 2008-06-27
Install the package ntfs-config, it'll make setting your NTFS drives up a matter of a couple of mouse clicks.

---

### Post by T2manner on 2008-06-28
okay,
i already have ntfs config installed.
but i got ```
relyt@relyt-desktop:~$ sudo mount computer:/// ~/Desktop
[sudo] password for relyt: 
mount: wrong fs type, bad option, bad superblock on computer:///,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

idk what went wrong.
when i look at the location of the hdd i want to mount it is computer:///

---

### Post by Paqman on 2008-06-29
NTFS config is a GUI, it'll probably install into Applications > System Tools, or possibly into System > Admin. Just open it up and check the boxes for the drive you want to mount.

---

### Post by T2manner on 2008-06-29
obviously you didn't read this post..
i have had ntfs config installed for quite sometime now, it's not working now..

---

