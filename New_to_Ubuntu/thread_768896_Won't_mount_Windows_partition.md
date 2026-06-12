---
title: "Won't mount Windows partition"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by belovedmonster on 2008-04-26
After doing a clean install of 8.04 Xubuntu (I used to have 7.10) I now find that it wont mount my windows partition. I get the following error message:

org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result).

What does it mean?

---

### Post by Joeb454 on 2008-04-26
Strange, I'm sure that it should work. 2 things worth checking.

1) Do you have ntfs-3g installed? if not that might be a slight issue ;)
2) Did you cleanly shutdown Windows? If you didn't then I know that Ubuntu can't mount the partitions until it has been cleanly shutdown :)

---

### Post by JGT on 2008-04-26
I'm in the same situation. Under 7.10, I had immediate r/w access to the Windows partition. Under (X)ubuntu 8.04, it just doesn't see it. I have ntse-3g installed - it's a clean install rather than an update.

---

### Post by belovedmonster on 2008-04-26
I have ntfs-3g installed. Windows was shut down cleanly. :(

Also of note perhaps, when I mount external drives all the files have padlocks on them.

---

### Post by artships on 2008-04-26
In a terminal execute:

sudo mount -a

When I do it, for every ntfs drive I see:

/sbin/mount.ntfs-3g: /usr/local/lib/libfuse.so.2: version `FUSE_2.7' not found (required by /sbin/mount.ntfs-3g)

Do you have that problem, too?

---

### Post by belovedmonster on 2008-04-26
I dont get anything when I put that command in, just another line to type from.

---

### Post by kansasnoob on 2008-04-26
[http://ubuntuforums.org/showthread.php?p=4759429#post4759429](http://ubuntuforums.org/showthread.php?p=4759429#post4759429)

I hope that link and the suggestions help.

---

### Post by belovedmonster on 2008-04-26
One of the first things I did was change the grub to make Windows XP the default boot up, so I'm pretty sure the grub is working fine.

---

### Post by belovedmonster on 2008-04-26
I've been googling the subject and one solution was to 

in /etc/PolicyKit/PolicyKit.conf insert into section <config> permission for all users to mount all disks

```

<match action="org.freedesktop.hal.storage.*">
    <return result="yes"/>
</match>

```

I think I need to open the file in the terminal because it wont let me save changes otherwise.

What would be the command to open /etc/PolicyKit/PolicyKit.conf with my password engaged?

---

### Post by Beatnikboy on 2008-04-26
Try Add/Remove and install Storage Device Manager. 

Worked for me.

---

### Post by belovedmonster on 2008-04-27
Nope Storage Device Manager didn't work for me.

I'm finding this morning I'm also getting the problem that it wont mount my USB thumbdrive. It says...

Unable to mount "1G Removable Volume":

mount: only root can mount /dev/sdb1 on /media/sdb1

I just get the impression that mounting drives is in general screwed up at the moment.

---

### Post by Beatnikboy on 2008-04-27
Did you use Storage Device Manager to select the required partition and create a mount point?

I selected sda5 from the drop down menu and created a mount point /media/sda5 and told it to mount at boot time by marking that option in the dialogue box.

---

### Post by belovedmonster on 2008-04-27
I'm not at my Linux machine right now, but unless I'm very much mistaken all that info was already filled in when I looked at the partition in Storage Device Manager. The only setting I changed was to make mount available to all users.

---

### Post by Beatnikboy on 2008-04-27
If that is the case, double check first, then the only other thing I can suggest (which kinda worked too) is to have a look at this post:
[https://answers.launchpad.net/ubuntu/+question/29602](https://answers.launchpad.net/ubuntu/+question/29602)
Good luck!

---

### Post by JGT on 2008-05-02
Bump!

I tried a few things advised on the forum but i still can't see my Windows partition like i could in 7.04 and 7.10. The update didn't fix it. I might reinstall 7.10 from scratch if I can't r/w the Windows partition as I really need it. Is it a known bug?

---

### Post by raonyguimaraes on 2009-04-12
Worked for me .. Storage Manager for XUBUNTU 8.10 thanks a lot :D

---

### Post by neriman on 2010-03-14
Install PCMan File Manager!

---

