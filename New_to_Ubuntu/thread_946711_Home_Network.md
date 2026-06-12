---
title: "Home Network"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by dmsellers on 2008-10-13
I have two computers connected to a Linksys network hub so they can both use the dsl modem. One computer is using Windows XP the other Xubuntu. Can I browse the files on the Windows computer from the Xubuntu, and if so how difficult is it to do?

---

### Post by Nxion on 2008-10-13
No its not to complicated and it can be done! :)

I used this guide to get what you described to work.

[http://www.go2linux.org/how-to-install-samba-on-linux-with-swat](http://www.go2linux.org/how-to-install-samba-on-linux-with-swat)

Also you might want to look over this one as well.

[http://ge.ubuntuforums.com/showthread.php?p=5161121](http://ge.ubuntuforums.com/showthread.php?p=5161121)

Hope this helps.

EDIT: Here is another one to [try]("http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=accessWindowsFilesFromLinuxWithSamba")

---

### Post by OffAxis on 2008-10-13
you don't have to install a samba server installed (unless you want windows to access your xubuntu install), you just need the smbfs client.

Here's the community docs:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

and

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by dmsellers on 2008-10-13
I can now browse my Linux machine from the Windows machine; however, I do not know how to do it in reverse.

David

---

### Post by Nxion on 2008-10-13
Try this in a terminal

```
mkdir /mnt/winxp
```THEN

```
sudo mount -t smbfs -o username="windows username" //"ip-of-xp-machine"/"share_name" /mnt/winxp
```Did that work?

replace

"windows username" with what you use to log on to Windows XP WITHOUT the quotes
"ip-of-xp-machine" with the address to your XP machine WITHOUT the quotes
"share_name" with what ever folder you have shared on Windows XP WITHOUT the quotes

---

### Post by dmsellers on 2008-10-13
How do you find the ip of the windows machine?

---

### Post by Nxion on 2008-10-13
Click Start >Run

type cmd in the run command

A black box should come up; There type this

```
ipconfig
```

There it will give you the IP address of your XP machine.

---

### Post by Nxion on 2008-10-14
Where you able to get it working?

---

### Post by gn2 on 2008-10-14
Xubuntu's file browser Thunar does not have network browsing capability by default, but the link in my sig might help get you fixed.

---

