---
title: "Basic Network Mouting: Ubuntu 12.10 Mounting Windows Shares cifs"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by WilliamMiller54 on 2012-12-22
I will start with noting that I am a semi-linux-noob, but a 20+ year IT professional. I have used Linux as a server, and dabbled in the desktop, but have always been turned off by how difficult it is to maintain as a productivity desktop. My goal for 2013 is to switch to Linux for a year. My initial experience may make me re-think that. 

I have installed Ubuntu 12.10 x64 in a windows environment with a primary Windows Server as a file and media host. 

After several failed installation attempts I was finally able to get Ubuntu to install. However, it took multiple tries, several USB burns, and a couple of system reformats for it to install completely. I don't know what made it finally work, but installation took over 3 hours.

Once installed, and using everything stock, I opened the Nautilus File browser and was able to navigate through my network, authenticate to my Windows server, and see my files. Some files I could open, others I could not. Media would not all play, and I could not open or save Open Office files to the server.  (Come on folks, this is 2012, data should not be locked to a platform. This is basic functionality)

**Issue**: I can browse to Windows Server and see my office and media files, but can not use them without coping them down, modifying them locally, and saving them back up. 

**Issue**: I can not play media stored on a Windows Share

**Resolution**: 
Install through Ubuntu Software Center: cifs-utils
Install through Ubuntu Software Center: smbnetfs  
I don't know if I need this because cifs proceeds Samba, but this was part of what I did. 

At this point I still could not access my data correctly so I began to track it down to an improper mount. I thought I would have map through the dreaded terminal and nested configuration. 

I began tracking down fstab file
located at /etc/fstab 
used by the mount command on load to mount devices

To edit the fstab file: Open a terminal window and type ```
sudo gedit /etc/fstab
```
this will launch the fstab file in a gedit editor 

At the bottom of the file add your cifs connection string: 
```
//WinServerIP192.168.123.000/WinServerShareName /home/LinuxHomeDir/MountFolderName cifs uid=LinuxUserName,user=WinServiceAccountName,password=WinServiceAccountPassword 0	0
```

**I had multiple issues with this. **
[LIST=1]
[*]1. Although I can browse to my server through Nautilus by machine name cifs can not find the server by name
[LIST]
[*]1. Luckily my server has a static IP and I could use that. 
[/LIST]
[*]2. I had to create a mount point to mount to.
[LIST]
[*]1. I created a mount point in my home directory through the terminal window, but that did not work because of the access granted 
[*]2. I ended up creating the mount point through Nautilus and granting the following access: 755
[LIST]
[*]1. To see the permissions of a folder use: stat -c %a [filename]
[*]2. To change permission use: chmod
[*]3. I want to mount to several shared so I created them in my home folder
[LIST]
[*]1. Create Folder: WinServer Name permissions: 755
[*]1. create sub-folders: Share Name, permissions: 755
[/LIST]
[/LIST]
[/LIST]
[*]3. My windows account user name and password has a space in them
[LIST]
[*]1. I attempted to use quotes in the string: “User Name”, but this did not work
[*]2. I attempted to use %20 in the string: User%20Name, but this did not work
[*]3. I ended up creating a new system account and password on the windows server with out any spaces, and granting it the appropriate access[/LIST]
[/LIST]
After editing the fstab file you can force a remount by using: sudo mount -a

I tested several times through a full reboot

This did mount my Windows shares to my Ubuntu 12.10 desktop, and I was able to edit and save directly to the file shares.  

However, I could not play all my MP3. Installing Ubuntu Restricted Extras from the Ubuntu Software Center fixed that. 

What a pain for basic user desktop functionality! 

**_Useful Links: _**
Cifs "mount error 13 = Permission denied"
[http://vijayk.blogspot.com/2008/09/cifs-mount-error-13-permission-denied.html](http://vijayk.blogspot.com/2008/09/cifs-mount-error-13-permission-denied.html)

Cifs "mount error 13 = Permission denied" CIFS SUCKS
[http://www.linuxquestions.org/questions/linux-networking-3/cifs-mount-error-13-%3D-permission-denied-cifs-sucks-463271/](http://www.linuxquestions.org/questions/linux-networking-3/cifs-mount-error-13-%3D-permission-denied-cifs-sucks-463271/)

Mounting a share with spaces in FreeBSD fstab
[http://serverfault.com/questions/85900/mounting-a-share-with-spaces-in-freebsd-fstab](http://serverfault.com/questions/85900/mounting-a-share-with-spaces-in-freebsd-fstab)

Samba Shares, Spaces and fstab (With a bit of Octal thrown*in)
[http://raetsel.wordpress.com/2008/02/02/samba-shares-spaces-and-fstab-with-a-bit-of-octal-thrown-in/](http://raetsel.wordpress.com/2008/02/02/samba-shares-spaces-and-fstab-with-a-bit-of-octal-thrown-in/)

12.10 cifs shares not mounting after modifying /etc/fstab
[http://askubuntu.com/questions/199142/12-10-cifs-shares-not-mounting-after-modifying-etc-fstab](http://askubuntu.com/questions/199142/12-10-cifs-shares-not-mounting-after-modifying-etc-fstab)

---

### Post by PieterJ6 on 2013-01-11
WOW!! Your cifs connection string really helped me to get my xUbuntu shared folder to mount after trying for an extensive period of time.

If I'm correct then you can use a / or \ to escape a space character in some commands - I found this to work in most path references.

---

### Post by WilliamMiller54 on 2013-01-25
> **PieterJ6 said:**
> WOW!! Your cifs connection string really helped me to get my xUbuntu shared folder to mount after trying for an extensive period of time.

If I'm correct then you can use a / or \ to escape a space character in some commands - I found this to work in most path references.

Pieter, I tried the escape slash, but it did not work. Maybe I will try again

---

### Post by mcmalach on 2013-02-18
i realize this is a little late but for anybody else that may read this forum looking for an answer

try using \040 instead of  a space

so if your name was "ubuntu server"

it would now be "ubuntu\040server"

see if that works

---

### Post by kepz on 2013-02-24
2013, I've decided to run with Linux and start getting use to it.  I've dabbled with it for such a long time but I think it's now time to start using it full time.  I do like it, but it restricts me and keep having to run back to Windows.

Now that I'm running 12.10 I'm reminded once again why I keep going back to Windows, but I've decided.  I'm here to stay.

Can someone remind me how to mount a Windows Server again please. lol

---

