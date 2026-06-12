---
title: "What is the best way to access Windows XP share?"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by dixcuxx on 2011-11-19
I am using the 11.10 ubuntu. I google and find out a way to do so, but seem like it is not a good way. Honestly I don't even remember how I set this up, but now I had created 3 access in mnt folder, but only 1 with correct setup, but I have no idea how to delete the other twos. Anyway what is the best way and how do I delete the 2 not useful access folders link?

Can think link to the problem I always need 20 minutes in the shut down loading screen of ubuntu?

---

### Post by WasMeHere on 2011-11-19
Hi dixcuxx,

In order to help I would like to ask a few questions.
- What do you mean by Windows XP share? Is it on the same computer or on another one in the local network? And what kind of share: files, printer?
- Which way do you want to share it? To or from the Ubuntu computer, or both ways?
- What tool did you use for sharing? Samba, SSH ...?
- Please post the content of the file ***/etc/fstab***

Have fun finding out about Ubuntu :-)
Olle

---

### Post by papibe on 2011-11-19
Are you trying to access your Windows files in the same computer while running Ubuntu? or files from other machine running XP?

Regards.

---

### Post by dixcuxx on 2011-11-19
> **Olle Wiklund said:**
> Hi dixcuxx,

In order to help I would like to ask a few questions.
- What do you mean by Windows XP share? Is it on the same computer or on another one in the local network? And what kind of share: files, printer?
- Which way do you want to share it? To or from the Ubuntu computer, or both ways?
- What tool did you use for sharing? Samba, SSH ...?
- Please post the content of the file ***/etc/fstab***

Have fun finding out about Ubuntu :-)
Olle

Sure! I have a local network setup with wireless/lan. So there is another computer at home running XP professional. I set it up to share out files but it requires correct user and password to access it.

Well one additional question. For share like this, is that I cannot use windows home to access the files? Because I also have a windows home XP and the only way I find out is that I setup with that user name in windows home and that password to access files in another computer...very not convenient.

---

### Post by JRV on 2011-11-19
You can select Connect to server from the desktop global menus, and fill in the blanks.

Or from the command line:
```
nautilus smb://XP_NAME/SHARE_NAME
```

---

### Post by dixcuxx on 2011-11-19
> **JRV said:**
> You can select Connect to server from the desktop global menus, and fill in the blanks.

Or from the command line:
```
nautilus smb://XP_NAME/SHARE_NAME
```

I cannot save it and use it everyday after I start a computer with "Connect to server". I need to type everything again with "Connect to server". Since I have user name and password in sharing, that really take a lot of time to type in everything again after reboot everyday...

---

### Post by Morbius1 on 2011-11-19
That's why the gods created Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by JRV on 2011-11-19
Create a blank file on your desktop and copy this template into it.
Name it what you want it to be called.

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=administration
Name[en_US]=XP Share
Exec=nautilus smb://XP_NAME/SHARE_NAME
Name=XP Share
Icon=administration

```
Both name fields should be edited to the same thing you named the file.

When you are finished editing save the file, add ".desktop" to the name and make it executable.

Now you can right click the icon, select properties,  and change the icon and the Exec.

Test it, move it to ~/.local/share/applications.
Then drag it to the launcher bar.

For more information on .desktop files read my tutorial and the threads listed at the bottom.

[http://ubuntuforums.org/showthread.php?t=1857589](http://ubuntuforums.org/showthread.php?t=1857589)
___

---

### Post by dixcuxx on 2011-11-20
Which is better? Gigolo or the desktop executable file way?

---

### Post by dixcuxx on 2011-11-20
I think I followed this page to do that:
[http://askubuntu.com/questions/72471/changing-permissions-of-a-mounted-windows-share](http://askubuntu.com/questions/72471/changing-permissions-of-a-mounted-windows-share)
but then there are two folders which I had wrong login information but the access folder is still there.

---

### Post by Morbius1 on 2011-11-20
> **dixcuxx said:**
> Which is better? Gigolo or the desktop executable file way?
Gigolo and Exec=nautilus smb://XP_NAME/SHARE_NAME both use the same underlying method which is gvfs so one is not inherently better than the other.

Gigolo has 3 advantages though:

* It mounts the remote share automatically at boot with a stored locally encrypted password if the remote share requires one.
* It waits until the remote server is on line before it mounts ( in case you haven't turned on the remote server yet ).
* It doesn't hang at shutdown like the traditional method in fstab.

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> Gigolo and Exec=nautilus smb://XP_NAME/SHARE_NAME both use the same underlying method which is gvfs so one is not inherently better than the other.

Gigolo has 3 advantages though:

* It mounts the remote share automatically at boot with a stored locally encrypted password if the remote share requires one.
* It waits until the remote server is on line before it mounts ( in case you haven't turned on the remote server yet ).
* It doesn't hang at shutdown like the traditional method in fstab.

cool!! Any idea how to unmount what I did?
I did this:
[http://askubuntu.com/questions/72471/changing-permissions-of-a-mounted-windows-share](http://askubuntu.com/questions/72471/changing-permissions-of-a-mounted-windows-share)

---

### Post by Morbius1 on 2011-11-20
If you did something like this is fstab:
> //server/share /mnt/mountname cifs username=server_user,password=user_password,iocharset=utf8,mode=0777,dir_mode=07*&#8203;77 0 0* unmount the remote share:
```
sudo umount /mnt/mountname
```* Put  a # sifn in front of that line in fstab like this:
> #//server/share /mnt/mountname cifs username=server_user,password=user_password,iocharset=utf8,mode=0777,dir_mode=07*&#8203;77 0 0Then save fstab and run the following command:
```
sudo mount -a
```

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> If you did something like this is fstab:
* unmount the remote share:
```
sudo umount /mnt/mountname
```* Put  a # sifn in front of that line in fstab like this:
Then save fstab and run the following command:
```
sudo mount -a
```

How do you know all of these so deeply? Are you a server administrator or something like that?

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> If you did something like this is fstab:
* unmount the remote share:
```
sudo umount /mnt/mountname
```* Put  a # sifn in front of that line in fstab like this:
Then save fstab and run the following command:
```
sudo mount -a
```

I tried what you just said then I get this:
umount: /mnt/foldername: not mounted

then I think it is just a normal folder, but I cannot find a delete option in the file explorer in ubuntu.

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> If you did something like this is fstab:
* unmount the remote share:
```
sudo umount /mnt/mountname
```* Put  a # sifn in front of that line in fstab like this:
Then save fstab and run the following command:
```
sudo mount -a
```

I can unmount the one which I successfully mount before, then now include this one and two not success cases, having 3 empty folders in mnt.

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> If you did something like this is fstab:
* unmount the remote share:
```
sudo umount /mnt/mountname
```* Put  a # sifn in front of that line in fstab like this:
Then save fstab and run the following command:
```
sudo mount -a
```

After I unmount it, it is ok. However, once after reboot, the mount is there again to have slow shut down again.

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> If you did something like this is fstab:
* unmount the remote share:
```
sudo umount /mnt/mountname
```* Put  a # sifn in front of that line in fstab like this:
Then save fstab and run the following command:
```
sudo mount -a
```

I just try and confirm, even I rmdir after unmount the mounted share folder with your command, it will appear again after rebound.

---

### Post by Morbius1 on 2011-11-20
Please post the output of the following command:
```
cat /etc/fstab
```

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> Please post the output of the following command:
```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=506bcd29-53a6-4ef4-8c5d-12185aa82e91 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
#UUID=5de9fd85-6e5a-493c-a120-1f1a12b8e994 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

//192.168.1.9/good /mnt/good cifs username=kickerB,password=1234ABCD&,iocharset=utf8,mode=0777,dir_mode=07*&#8203;77 0 0

---

### Post by Morbius1 on 2011-11-20
You didn't add the # sign.

Change this:
> //192.168.1.9/good /mnt/good cifs username=kickerB,password=1234ABCD&,iocharset=utf8  ,mode=0777,dir_mode=07*&#8203;77 0 0     To this:
> [COLOR=Blue]**#**[/COLOR]//192.168.1.9/good /mnt/good cifs username=kickerB,password=1234ABCD&,iocharset=utf8  ,mode=0777,dir_mode=07*&#8203;77 0 0     Save the file. If /mnt/good is currently mounted unmount it:
```
sudo umount /mnt/good
```BTW, "dir_mode=07*77" could have been the source of may problems since the * makes no sense in this context.

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> You didn't add the # sign.

Change this:
To this:
Save the file. If /mnt/good is currently mounted unmount it:
```
sudo umount /mnt/good
```BTW, "dir_mode=07*77" could have been the source of may problems since the * makes no sense in this context.

what does the # do? I want to use the way you mentioned before, should I totally clear what I did now, then install that?

---

### Post by Morbius1 on 2011-11-20
The "#" comments out the line so the system will ignore it.

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> The "#" comments out the line so the system will ignore it.

I just wake up and haven't applied your suggestion yet. Well somehow the wireless has been slowed down and I think it is because of the share connection. Watching video online or seeing shared video from another computer would be slow down...even the online flash kind of video would have sound quality decrease. Any idea and make sense?

---

### Post by dixcuxx on 2011-11-20
> **Morbius1 said:**
> The "#" comments out the line so the system will ignore it.

The first time for me using # as comment line:popcorn:

---

### Post by dixcuxx on 2011-11-21
> **Morbius1 said:**
> You didn't add the # sign.

Change this:
To this:
Save the file. If /mnt/good is currently mounted unmount it:
```
sudo umount /mnt/good
```BTW, "dir_mode=07*77" could have been the source of may problems since the * makes no sense in this context.

I just nano the file and then delete the whole line.

---

