---
title: "How to change directory/file permissions"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by jps2012 on 2013-07-07
I'm trying to change the permissions for a folder and all its contents. I've used "pwd" to confirm I'm at the correct directory, issued the command, but keep getting a "no such file" response from Terminal. If you see what I'm doing wrong in the following, please let me know (I thought I was placing the slash in the wrong area, but that doesn't seem to be it): 

[From Terminal:] "Admins-MacBook:EarthstockPortlandBest2012 joel$ sudo chmod -R 755 /EarthstockPortlandBest2012
Password:
chmod: /EarthstockPortlandBest2012: No such file or directory
Admins-MacBook:EarthstockPortlandBest2012 joel$ sudo chmod -R 755 EarthstockPortlandBest2012/
chmod: EarthstockPortlandBest2012/: No such file or directory
Admins-MacBook:EarthstockPortlandBest2012 joel$ pwd
/Volumes/JPSBackupDrive1/EarthstockPortlandBest2012

---

### Post by hansdown on 2013-07-07
Hi jps2012.

You should try

> gksu nautilus

You should be able to navigate to the folder, and copy with permissions, etc.

---

### Post by scbingham on 2013-07-07
You are misusing the '/'
Be very sure you really do want to change ALL files & directories within & including [COLOR=#000000]EarthstockPortlandBest2012[/COLOR] to 755. Changing permissions can have disastrous results & be a pain to put right.

[COLOR=#000000]EarthstockPortlandBest2012 looks like it sits within [/COLOR][COLOR=#000000]/Volumes/JPSBackupDrive1, not /[/COLOR]

Issue the command [COLOR=#000000]sudo chmod -R 755 EarthstockPortlandBest2012 when you are in [/COLOR][COLOR=#000000]/Volumes/JPSBackupDrive1[/COLOR][COLOR=#000000] & it will work.
[/COLOR]
Hope this helps.

---

### Post by fosterD on 2013-07-08
hi, there are somethings isn't right in your commands.
1- as scbingham said, you was misusing the '/'. When you use > sudo chmod -R 755 /EarthstockPortlandBest2012
it means you want to change the permission of 'EarthstockPortlandBest2012' directory, under '/'. Obviously, you didn't have that directory there. So you received an error message
If you mean the directory of the current location, you need to use './' instead

2- from the result of pwd,> Admins-MacBook:EarthstockPortlandBest2012 joel$ pwd
/Volumes/JPSBackupDrive1/EarthstockPortlandBest2012
you are sitting inside 'EarthstockPortlandBest2012' directory, that was the reason of your error.

If you want to change the permission of that directory, try
cd /Volumes/JPSBackupDrive1
sudo chmod -R 755 ./EarthstockPortlandBest2012

---

### Post by jps2012 on 2013-07-08
scbingham and fosterD: Thanks very much for the instructions. I didn't realize I needed to be sitting one directory above the directory whose files I wanted to change the permissions for. I went a level up, issued the same command, and it worked. 

BUT I issued the same command for another directory in the JPSBackupDrive1 device (it's actually an external harddrive) and got an "operation not permitted" response. 

Any idea why it would work for one directory, but not another (the directory only contains image files--NEF files)? 

Here's what the command and response look like (I tried it with the slash preceding Earthstock also): 

Admins-MacBook:JPSBackupDrive1 joel$ sudo chmod -R 755 EarthstockPortland2012/
chmod: Unable to change file mode on EarthstockPortland2012/: Operation not permitted
chmod: Unable to change file mode on EarthstockPortland2012//_DSC3020.NEF: Operation not permitted

---

### Post by dannyboy79 on 2013-07-08
what filesystem is this external drive formatted as? NTFS doesn't support linux permissions. 
also you don't have to be 1 directory above to change permissions, you can be where ever you want but it's important what you enter, either a . to signify the current directory you're in OR just write the full path to the directory you want to change. Here's 2 examples:
```
pwd
``` shows me that I am in /home/ubu/
i want to change permissions of /home/ubu/test
i could issue ```
sudo chmod 755 /home/ubu/test
```
OR
I could cd to /home/ubu/test/ and issue ```
chmod 755 .
```

---

### Post by jps2012 on 2013-07-09
dannyboy: Thanks very much for the insight into directory problem. I didn't know I had to specify a '.' to indicate I meant (in the command line) 'do this in the current directory.' The file system is a Mac journaled drive (I'm learning the command line in Ubuntu and Mac, and am usually able to apply the same commands in Terminal because I'm using Bash). The permissions issue really has me stumped, though. I'm still trying to sort it out.

---

### Post by dannyboy79 on 2013-07-09
i don't believe you can use linux to change the permissions, owner or group on an hfsplus partition (i am not sure at all). is it over 2TB?

---

