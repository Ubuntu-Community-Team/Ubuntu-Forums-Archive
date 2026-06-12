---
title: "I am finding Ubuntu difficult"
date: 2016-06-02
forum: New to Ubuntu
---

### Post by kologha on 2016-06-02
Hello to everyone. I am retired and live on a farm out in the sticks. I decided to turn to Ubuntu as I was using Win XP until about a month ago and to be honest I don't have the money to invest in a Windows upgrade. My XP was infected with some or other virus which caused my mouse pointer to freeze intermittently which made it virtually impossible to use the mouse.

To cut a long story short I had to reinstall XP and I then decided I would have to turn to Ubuntu. I have managed to set my PC up with both XP and Ubuntu 14.04 and am dual booting, originally I decided to try dual booting as I have a CAD programme which will only run on Windows.

It's just as well that I can still access XP because yesterday I tried to upload photos from my Canon SX100 using Ubuntu and it made a complete hash of it so I went into XP and uploaded my pictures. My PC has two hard drives one for the OS and the other one for all my personal files etc, which is how I have had my PC configured for the last 10 or 12 years. It works perfectly with Ubuntu, and I can access my 2nd HD with absolutely no problems. However when trying to upload photos from my camera, I could not get the Photo Software to allow me to save them in my photo file on the 2nd HD. I tried 'Shotwell manager', 'Dark Table' and 'gThumb' all without success.

At that point I was ready to tear my hair out, because I cannot understand why the people who wrote these programmes all insist that everything must be saved in Ubuntu. I am not a computer geek, all I want is an OS which will do what I require. Am I being unreasonable? Is there a way which is not too technical which will allow me to save my stuff where I want it and not where the software programme has decided it must go?

Other problems I have had is trying to run software after I have installed it, but then can't find it. Why on earth is it so difficult? I have always used Windows from my first PC experience with Windows 3 right up to WinXP and I must say Window makes it much easier for a non geek to muddle around! Another thing I don't understand is 'Tags' What is a 'Tag' and where do I find them? Thanks for reading my rant!

---

### Post by Bob_Rimkus on 2016-06-02
Yes, Linux (Ubuntu) has a learning curve. Its has gotten better over the past 10 years, but still not as user friendly as Windows and not all software that runs on Windows will run on Linux. :)

---

### Post by QIII on 2016-06-02
The Linux learning curve is nearly identical to the Windows learning curve.

People are not born familiar with Windows and "user friendly" is industry code for "what people have become accustomed to".

A person who has never used a computer before would have as much trouble mastering Windows as Linux.

---

### Post by ajgreeny on 2016-06-02
I have always used a card reader to transfer photos and videos from camera to computer as it is a great deal more flexible than connecting the camera and letting whatever photo-manager you prefer upload them.

The default in most of those photo-managers is to upload all photos into a single folder (Pictures or Photos) and then manage them with the "tags" you speak of, eg Family, Holidays, etc etc, which you have to add yourself, so I find it much more sensible (for my mindset, anyway) to view thumbnails of the photos on the card in my file-manager and copy them in subject groups to an appropriately named folder in Pictures folder in my home.  This way you can get your photos exactly where you want them.

As for the programs that you have installed and can not find, give us more info.  If you can not find them in the menu system it could be that the applications are command-line only, but give us an example please and we'll try to help.

Finally don't forget that Linux (Ubuntu) is not a clone of Windows, nor was it ever intended to be.  It does a lot of things differently, and in my opinion, better, so you will need to think in a new way to get the best from *ubuntu. However, you may find that one of the other versions of *ubuntu is much more like XP and therefore easier for you to use.  have a look at Xubuntu, my favourite, which looks like XP in many ways, and is also lighter weight than the unity desktop of Ubuntu so may run better on an older XP machine.

---

### Post by grahammechanical on 2016-06-02
Most applications have a "save as" option which not only gives us the opportunity to name the file but also the opportunity to select the location. If we have a separate disk that we use to store data files then this will not show up as a location until we open the disk with the file manager. In Linux language this action "mounts" to partition or file system as it is called.

All partitions on all disks should show up as drive icons in the launcher (panel on the left side of the screen) or if it is Xubuntu as drive icons on the desktop top. Click on the icon relative to the disk drive that you have you data on. That will open the drive/partition in the file manager. Now, if you run the application to copy images files from the device you should get that drive as a location in the Save As dialog box.

Shotwell defaults to importing images into the Pictures folder but by opening Edit>Preferences>location tab we can set a different Library Location for importing files to. There should be a drop down menu that lists not only the standard data folders in Ubuntu but also all partitions. We can also select Other and that will open a dialog where we can browse to a partition and a folder on that partition and make that the default location for importing images from a camera.

I am sure that Windows applications also have a default location and it will usually be the Pictures or Photos folder. I certainly never found it easy to change the import location when I was uploading photographs from a camera to an Windows computer at my place of employment.

Regards.

---

### Post by mastablasta on 2016-06-03
> **kologha said:**
> 
It's just as well that I can still access XP because yesterday I tried to upload photos from my Canon SX100 using Ubuntu and it made a complete hash of it so I went into XP and uploaded my pictures. My PC has two hard drives one for the OS and the other one for all my personal files etc, which is how I have had my PC configured for the last 10 or 12 years. It works perfectly with Ubuntu, and I can access my 2nd HD with absolutely no problems. However when trying to upload photos from my camera, I could not get the Photo Software to allow me to save them in my photo file on the 2nd HD. I tried 'Shotwell manager', 'Dark Table' and 'gThumb' all without success.

Let me guess the "files" disk is NTFS formated? NTFS is a windows closed soruce file system. EXT4 should work better. evenso the user should own the disk. 

can you post the results of the followign command:
```
ls -l
```

that's a small L

and also post the output of :
```
df -h
```

use the # icon in advanced answer on forums to wrap tthe text so it is easier to read. you can mark the output and right click and copy the text.

> 
Other problems I have had is trying to run software after I have installed it, but then can't find it. Why on earth is it so difficult


if the software is terminal based then all oyu need ot do is open terminaland type it's name. if it is graphical then you open dash and type in the name of software or description to find and run it. 

if you want a windowsXP like interface try KDE with classic menu (Kubuntu) or Xubuntu (which can easilly be made to look similar to XP). another options i ZorinOS which makes it look like XP or Windows7.

> **ajgreeny said:**
> I have always used a card reader to transfer photos and videos from camera to computer as it is a great deal more flexible than connecting the camera and letting whatever photo-manager you prefer upload them.

yes, a USB card reader costs about 2 EUR (shipping included). though i am not sure compatibility is an issue here. it is likely it's about partition ownership. possibly also about unmounted disk partition.

---

### Post by kologha on 2016-06-03
Hi mastablasta. Thank you for your reply. Yes my Western Digital drive is HTML formatted, but once I found out how to mount it so that Ubuntu could see it I have had absolutely no problems. I thought after I had posted my rant, that perhaps the WD drive needs to be mounted by the various photo software packages before they can see it? I would need advice about how to do it if that is the case.


 The results for 
ls -l are:
user@user-O-E-M:~$ ls -l
total 180
-rw-rw-r-- 1 user user     0 Apr 29 09:02 -
drwxrwxr-x 3 user user  4096 May  8 19:41 Calibre Library
drwxrwxr-x 3 user user  4096 Apr 29 09:12 clipgrab
drwxr-xr-x 2 user user  4096 Apr 20 18:23 Desktop
drwxr-xr-x 3 user user  4096 Jun  2 09:57 Documents
drwxr-xr-x 2 user user  4096 May 30 12:52 Downloads
drwxr-xr-x 2 user user  4096 May 30 19:18 dwhelper
-rw-r--r-- 1 user user  8980 Apr 20 17:46 examples.desktop
-rw-rw-r-- 1 user user 78087 May  1 15:33 lshw.html
-rw-rw-r-- 1 user user 43443 May 15 23:04 mozilla.pdf
drwxr-xr-x 2 user user  4096 Apr 20 18:23 Music
drwxr-xr-x 3 user user  4096 Jun  1 15:47 Pictures
drwxr-xr-x 2 user user  4096 Apr 20 18:23 Public
drwxr-xr-x 2 user user  4096 Apr 20 18:23 Templates
drwxr-xr-x 2 user user  4096 Apr 20 18:23 Videos
user@user-O-E-M:~$ 

And the results for 
df -h are:

user@user-O-E-M:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            980M  4.0K  980M   1% /dev
tmpfs           199M  1.2M  197M   1% /run
/dev/sda5        50G  8.5G   39G  19% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            991M  572K  990M   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sdc1       466G  286G  180G  62% /media/user/WD500GB
user@user-O-E-M:~$ 

Thanks for the information about typing the name into the terminal to run new software, I never thought of that. I forgot to say but I live in
 South Africa near a very small town out in the country and to purchase any electronic gadgets like a card reader, I would have to drive 160
 kilometres round trip to the nearest big town where I might buy such a thing. Needless to say I am not desperately keen to do that. My Canon
 software only requires that I plug in the camera to the PC USB port and it opens automatically and uploads all new photos automatically to my New Photos
folder on the WD drive. It's a real pity that Canon don't make the software Linux compatible.

Thanks to the other members who posted some thought provoking posts. I will in time learn how to use Ubuntu. I first thought about installing it
in 2013 when there was so much talk about XP losing it's support and thats when I started lurking on this forum. However the more I lurked, the more
terrified of Linux I became and if it wasn't for the virus in XP I would probably still be dithering!

I am sorry I have not used the #icon as you suggested to wrap the text, I only just saw it after having written all the above, but I made the sentences
short so they (hopefully!) will be easy to read. 


Regards and thank you.

---

### Post by mastablasta on 2016-06-03
eh, silly me, it should be:

```
ls -l /media/
```

ok so apparently *Disks* has the option to automount on boot (scroll down the page ot see where you  can change the options): [https://www.liberiangeek.net/2013/05/mounting-external-storage-devices-in-ubuntu-13-04-raring-ringtail-is-a-lot-easier-with-disks-tool/](https://www.liberiangeek.net/2013/05/mounting-external-storage-devices-in-ubuntu-13-04-raring-ringtail-is-a-lot-easier-with-disks-tool/)

automount of NTFS is not advisable, but then again it seems this is how my media server is doing it and it's been just fine for the past 2 or 3 years.

you probably want /dev/sdc1       466G  286G  180G  62% /media/user/WD500GB automounted.

but before you mount make sure you own it:
sudo chown -R user:user /media/user/WD500GB

more here: [http://jsmylinux.no-ip.org/hard-drive-management/taking-ownership-of-partition/](http://jsmylinux.no-ip.org/hard-drive-management/taking-ownership-of-partition/)

-
as for the card reader i understand your issue. i just order this stuff from Aliexpress, but i guess they might not have free shipping to your place :-)

still it is a good thing to have as backup if the battery on camera dies out or something.

offtopic:
windows XP viruses can be cleaned using free linux live CD's  such as bitdefender rescue disk or avira rescue disk. however you need good internet connection (at least with Avira - it boots then downloads latest virus definitions and then it scans).

Avast and Avira are descent and free antivirus with winXP support. Adding Comodo firewall into the mix intercepts a lot of bad stuff (Comodo also has it's own antivirus which is also quite ok, it also has sanboxed apps and virtual desktop on WinXP). of ocurse if you plan to use winXP i suggest you at least have it fully updated (updates can be downloaded to a CD and then installed from it). it is not advised, but some people still use it (myself included).

---

### Post by kologha on 2016-06-03
Result of 
ls -l /media/user@user-O-E-M:~$ ls -l /media/
total 4
drwxr-x---+ 3 root root 4096 Jun  3 02:34 user
user@user-O-E-M:~$ 

Results of  /dev/sdc1       466G  286G  180G  62% /media/user/WD500GB automounted.
after I ran sudo chown -R user:user /media/user/WD500GB

user@user-O-E-M:~$ sudo chown -R user:user /media/user/WD500GB
user@user-O-E-M:~$  /dev/sdc1 466G 286G 180G 62% /media/user/WD500GB automounted.
bash: /dev/sdc1: Permission denied
user@user-O-E-M:~$ 

I do buy things off the internet occasionally but postage is very expensive so unless I really want or need something, I don't bother. My Canon camera uses rechargeable penlight batteries which is one of the reasons I bought it. I now only use Ubuntu to surf the Internet and only use XP to run my CAD software. I don't trust Windows because although I had Panda security, Zone Alarm firewall and regularly ran Malwarebytes, SpyBot Search & Destroy, as well as SuperAntiSpyware a virus still got through even though I updated the anti virus software every week or so before running it. I tried a number of virus cleaners with no luck and then I thought my mouse had packed up so I bought a new mouse all to no avail the only cure was a clean reinstall of XP which was a PITA as over the years I had made subtle changes (which I had subsequently forgotten about being 64 yrs old) and after the reinstall nothing worked as I wanted. 
Regards

---

### Post by oldrocker99 on 2016-06-03
Pal, I'm 67, retired, and eight years ago, I was a complete newbie. I have learned a lot in the intervening time. To download pictures, Shotwell is the program to use.

**NO** virus detector can get everything that's out there, which happened to me too in my XP days. I've used Ubuntu ever since, and it was the best computer decision I ever made.

Keep in mind that these forums are a *community*, and just about every question can be answered here. Welcome, and remember that the only stupid question is one that never gets asked.

---

### Post by kologha on 2016-06-03
Hi oldrocker, it seems there is hope for me yet!! I have just installed 'digiKam' and it was able to find my New Pictures folder on my WD500 drive where I store all my personal stuff. It appears to be a very useable programme, but time will tell! I'm still not happy with Shotwell, I tried it again today and there is no way it will allow me to select my New Pictures folder. It will show the drive but won't show any of the folders on the drive so I am going to abandon it for the time being and concentrate on 'digiKam'
Regards

---

### Post by mastablasta on 2016-06-03
> **kologha said:**
> Result of 

```
user@user-O-E-M:~$ sudo chown -R user:user /media/user/WD500GB
user@user-O-E-M:~$  /dev/sdc1 466G 286G 180G 62% /media/user/WD500GB automounted.
bash: /dev/sdc1: Permission denied
user@user-O-E-M:~$ 

```


yeah that means it won't run it because the disk is mounted. see the link i posted.

also if DigiKam works, just use that. in other words use what works best for you.

---

### Post by ajgreeny on 2016-06-03
Can we double check what the filesystem of sdc1 is please, as I am still not sure after reading this thread whether or not it is NTFS.

You have said > Yes my Western Digital drive is HTML formattedbut regrettably that does not make sense, but as you are answering the question "Is it NTFS?" I am assuming that comment of yours was a typo.

If it really is NTFS then the chown command shown above will not work for you as Windows filesystems do not understand or use Linux permissions.

You will need to mount that partition using a line the /etc/fstab file.  Read the thread at [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251) for a lot more detail on that and ask again if you need to.

---

### Post by kologha on 2016-06-03
Hi ajgreeny, please accept my most humble apologies! Total brain fade! I meant NTFS, cannot explain how HTML crept in. I have been using the Western Digital 500MB drive as my second drive for about a year with XP. I am still using it with Ubuntu and honestly I have no problems accessing old files and also no problems saving new files. If I boot with XP those files I saved with Ubuntu are accessible to XP. I cannot explain why it works as I do not really understand, but have read that Ubuntu has no problems reading or writing to NTFS. I am just happy that it does work. I am very much afraid that I am inclined to copy and paste code if it is suggested without really understanding what I am doing. It's going to take me a long time to learn the ins and outs of Linux code, as I said earlier I tend to muddle along and so far I have not broken anything!
Regards

---

### Post by ajgreeny on 2016-06-03
OK, that's all fine.

If you are now satisfied and feel that the problem is now solved for you please mark as SOLVED  from the Thread Tools menu up top.

---

### Post by oldfred on 2016-06-03
Do you have an OEM install or is that the name you gave it. OEM installs want you to create your own user ID and password on first boot.
user@user-O-E-M:~$

My user name if fred and system is a Z170, so I used that for system name.
fred@Z170N:~$

But if changing ownership you do not use "user" as then the owner is litterally "user"
In my case I use "fred".
But normally have save command and use some other systems so command I use often is $USER.
fred@Z170N:~$ echo $USER
fred

So this should be your command:
sudo chown -R $USER:$USER /media/user/WD500GB

---

### Post by kologha on 2016-06-04
Hi oldfred, not sure what OEM stands for. When I was working in the motor industry it stood for Original Equipment Manufacturer. Yes I gave my name as user when I installed Ubuntu, no one else uses my PC.

I tried your code and it accepted it.

user@user-O-E-M:~$ sudo chown -R $USER:$USER /media/user/WD500GB
[sudo] password for user: 
user@user-O-E-M:~$

So does that mean that Ubuntu recognizes that the drive WD500GB belongs to USER?
Regards

---

### Post by ajgreeny on 2016-06-04
Unless you have been substituting **user** for whatever the real username is, it looks as if **user** is your username on that system; am I correct?

If so, that command you used, ie  ```
sudo chown -R $USER:$USER /media/user/WD500GB 
```will have made that /media/user/WD500GB folder owned by "user" as that was the current username logged in and using the terminal.

The variable $USER will always refer to the user who is currently logged in, so if that exact same command had been run by another user on the machine that /media/user/WD500GB folder would now be owned by him, not by you.

I hope that makes sense to you.

---

### Post by kologha on 2016-06-04
Thank you. Yes my ID on this PC is 'user' as I am the only person who has access to it. 
Regards

---

### Post by oldfred on 2016-06-04
While Windows does not use case, in Linux case is important.
So user, USER and User are three different users.
But often best not to use too common of a user name. We see user and think you mean the generic "user" not your actual user name.
So your original entry was ok.

To confirm.
echo $USER

       [http://www.tldp.org/LDP/abs/html/internalvariables.html](http://www.tldp.org/LDP/abs/html/internalvariables.html)
The variables $ENV, $LOGNAME, $MAIL, $TERM, $USER, and $USERNAME are not Bash builtins. These are, however, often set as environmental variables in one of the Bash or login startup files.

---

