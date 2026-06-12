---
title: "[SOLVED] accessing ubuntu from an xp box"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by SusiBiker on 2008-08-12
Hi all.
I wouldn't normally bother you guys, but I've hit a brick wall and can't go any further.
I've installed samba onto hardy. I've set up shares that are visible with write permissions and with access by everyone. I've setup users, and then given them passwords using sudo smbpasswd -a <username>.
I've given access to windows boxes by setting up their ip addresses with the smb option in firestarter.

I can browse the windows shares using my hardy box, but cannot browse the hardy machine's shares using xp boxes.
I can ping the hardy box, and can connect to its ip address using a browser on a windows box - I get a web page that says "It works!"

I have just reinstalled samba, and tried setting up a network share from windows using the ip address of the hardy box and the path to the share. nothing.

I have been struggling with this for three days now and am at a total loss.

Please, can some kind soul point me in the right direction as I am getting to the point where I'm wondering if Linux is worth all the effort?

Thank you,
Susi

PS I've spent days searching the net and the forum and still non the wiser....

---

### Post by Dr Small on 2008-08-12
On the WindowsXP box, in Windows Explorer, have you tried typing into the address bar?
```
\\*ipaddress*
```

Also, on the Hardy box with samba, you may have to setup a Samba password for your user, like:
```
sudo smbpasswd *username*
```

Dr Small

---

### Post by sydbat on 2008-08-12
My stupid question is, does the Ubuntu box have a fat32 or ntfs partition for sharing? If not, the xp box won't be able to access things without [this]("http://www.fs-driver.org/")...as far as I know.

---

### Post by SusiBiker on 2008-08-12
Hi Dr Small,
Thanks for replying.
I get that the ip address is not accessible. You might not have permision.... Contact the administrator....The account is not authorized to login from this station

I set up the passwords using smbpasswd -a <username>

---

### Post by SusiBiker on 2008-08-12
Hi sydbat,
Thanks for replying.

I believe you only need that when Linux and Windows were on the same machine. It is not needed if you are accessing a share by smb as the server sorts out the local file system.

---

### Post by Iowan on 2008-08-12
Not running Hardy here, but remember reading *something* about unlocking being in a different place - maybe that'll trigger someone else's memory.

---

### Post by SusiBiker on 2008-08-14
Thanks Iowan, stuff has moved since previous releases, but I had unlocked the files all over the place.
Please read on...


Hi all,

Thanks for your help.

Solved it, well sort of.

My problems were-
1. Unable to access Ubuntu hardy box from windows on several machines
2. Unable to install nVidia restricted drivers
3. Keyboard resetting to US format from GB after every reboot
4. Probably a few others I hadn't noticed. A noob after all...

These problems had been present since a clean install on virgin hard disks.

A total reinstall cured all the problems. I think I must have done something wrong...
Reinstalled, just like the original install though, but this time it all works fine. Apparently... :)

Thanks for taking the time to reply.
Much appreciated.
Susi.

---

