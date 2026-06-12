---
title: "Accessing a dual boot Linux drive over a network when windows is running..."
date: 2008-07-21
forum: New to Ubuntu
---

### Post by magburner on 2008-07-21
Hi there, I am new to Ubuntu and Linux, and I am having some problems trying to access a hard drive. 

Here is my setup, PC1 is set to dual boot, and has three hard drives - two 160gb Windows hard drives, and one 320gb Linux hard drive. PC2 has one 40gb Linux hard drive. 

I have managed to mount the two 160gb Windows hard drives on PC2, but I cannot seem to find the 320gb hard drive when Windows is running on PC1. Is there any way for me to access the 320gb hard drive when Windows is running?

Thanks.

---

### Post by louieb on 2008-07-21
Do you have [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html") installed?

---

### Post by magburner on 2008-07-22
no I haven't, thanks for the link, i will have a go at it! :)

Superb! It works like a charm! I wonder if you can help with another related quandry...

I have to remount the windows shares each time i log onto Ubuntu, is there any way for this to happen automatically every time Ubuntu loads up?

Thanks.

---

### Post by jordanmthomas on 2008-07-22
You can use smbmount to mount them, and then put those mount commands in /etc/rc.local

---

### Post by magburner on 2008-07-22
Thanks for the info Jordan, how do I do smbmount, through terminal? I've looked in /etc/, and there are plenty of rc. folders, but no rc.local.

I'm sorry if I sound like an idiot, I'm a Linux virgin, so everything you say to me sounds like simplified Chinese! Any chance of a pre-school level walk through? ;)

---

### Post by jordanmthomas on 2008-07-22
No problem.
Yes, smbmount is run in a terminal.  First, you need to create a mountpoint for the share.  I'll use /home/yourname/share for this example.

First, make the directory for the mount:
```
mkdir ~/share
```
Then, mount with smbmount
```
sudo smbmount //windowscomputername/sharename ~/share -o username=user,password=passwd
```
You can use the name of the windows computer or its IP, either way will work.
Be sure to replace user and passwd with appropriate values.
After you verify the share is mounted (take a look in the folder), you can add it to /etc/rc.local

This isn't a folder, but just a file.
```
gksudo gedit /etc/rc.local
```
In this file, put the command you used to mount (the smbmount //...)
When you reboot, /etc/rc.local is run as if it's a bash script, so anything in it will be run.

Hope this helps.

---

### Post by magburner on 2008-07-22
Thanks pal, that's a great help! :)

---

### Post by bodhi.zazen on 2008-07-22
You can also add the shares to /etc/fstab (probably the preferred method).

//Server/share /mnt/samba cifs users,auto,credentials=/path/credentials_file,noexec  0 0                                 
[LIST]
[*]Server = Name (if in /etc/hosts) or IP Address of samba server.
[*]share = Name of shared directory (folder).
[*]/mnt/samba = your desired mount point.
[*]/path/credentials_file = full path to your credentials file. A credentials file should be owned by root (permissions 400) and contain two lines :
     Quote:
                                                 username = samba_user[FONT=monospace]
[/FONT]password = samba_user_password
[/LIST]
[INDENT][INDENT]samba_user = samba user (on server).[/INDENT][INDENT] samba_user_password = samba user password (on server).[/INDENT][/INDENT]
[LIST]
[*]noexec for security (it can be bypassed ...).
[/LIST]

---

### Post by magburner on 2008-07-23
Thanks for the additional information bodhi, I will try that too. :D

Can I be cheeky enough to ask a couple more questions?

Now that I have access to the second hard drive on PC1 (in the dual boot setup), can I run Linux programs from it on PC2 that has only Linux setup on it? How does PC2 that only has linux on it treat that hard drive? Is it as if it is apart of its own setup, or not?

Also, this might sound like science fiction too, but is there some program that will allow me to remotely run Linux on a dual boot PC whilst Windows is running and allow me to access it from another computer? 

So for instance I could run Linux in Windows, but control that copy of Linux from within another Linux distribution on a separate computer? I would also like to know if it is possible for that copy of Linux running inside windows to act as though it was another computer on my LAN (eg. PC3) even thought it is not physically there?

Any help will be greatly appreciated. Thanks.

---

