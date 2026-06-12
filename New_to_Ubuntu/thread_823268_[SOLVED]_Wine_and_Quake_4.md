---
title: "[SOLVED] Wine and Quake 4"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by kayfes on 2008-06-09
How would I go about playing Quake 4 with Wine?  I have wine installed just ready to do the rest to play Q4.

Thank you in advance for any help.

Oh and I am running on about 6 hours of sleep in the last 3 days and I thought I could actually run the install for Quake off the disk.  Of course didn't work lol but should I undo what I did if its is possible to do so?

---

### Post by kpkeerthi on 2008-06-09
Why do want to run Quake 4 on wine when you can play it natively on Linux? Google's your friend.

---

### Post by golgo13 on 2008-06-09
[http://ubuntuforums.org/showthread.php?t=708402](http://ubuntuforums.org/showthread.php?t=708402)

---

### Post by Rhubarb on 2008-06-09
Quake 4 has a native Linux installer that you can use.  - So there's no need to use wine at all.
It works in 32 and 64bit Ubuntu.

This may help you to install it:
[http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

---

### Post by kayfes on 2008-06-09
Thank you guys im a noob with ubuntu and linux in general and Im really tired but I just got my 9 series nvidia card working with Ubuntu and want to test it.  Will post a reply and mark as solved when I get it running.

---

### Post by kayfes on 2008-06-09
So I am downloading the torrent file for Q4 after I do that what should I do?  Does anyone have advice?  Maybe someone that has done this before?

Thank you in advance.

---

### Post by rajeev1204 on 2008-06-09
quake4-linux-1.4.2.x86.run

This is the file u need to download. Itsthe installer.

U need to copy the pak files from the cd to q4base directory,which is created when u run the installer.or u can manually create it where u want.

For example my path is /home/rajeev/quake4/q4base.

Easiest way is to let the installer create the necessary path which it usually does in /usr/local/games/.

---

### Post by kayfes on 2008-06-09
So how do I run quake4-linux-1.4.2.x86.run?  I have in my home directory.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> So how do I run quake4-linux-1.4.2.x86.run?  I have in my home directory.



type ```
sudo sh quake4.......run
```

---

### Post by kayfes on 2008-06-09
It installed and all that then what do I do?  Remember I grew up on point and click with Windows and am still a noob.

---

### Post by kayfes on 2008-06-09
Where you said it should be at but what do I do to play the game?

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> Where you said it should be at but what do I do to play the game?



Now u need to copy the quake  4 pak files from the cd/dvd to the directory where it is installed.

the pak files will be in the cd/dvd in a folder called maybe data or something.


Copy all of them to /usr/share/local/quake4/q4base

just tell me where exactly the pak files are on cd/dvd and ill tell u the command to copy the files to ur system

---

### Post by kayfes on 2008-06-09
Gonna have a smoke but I think I see where you are going with this.  After I copy those Am I going to be able to play?

---

### Post by kayfes on 2008-06-09
Looking for Local and only have Locale?

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> Looking for Local and only have Locale?



First , have u found the pak files on the quake 4 cd?

---

### Post by kayfes on 2008-06-09
Here is where they at on the CD

/media/cdrom0/Setup/Data

Thank you

PS 

At least when I right click on properties that where it says they are at.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> Here is where they at on the CD

/media/cdrom0/Setup/Data

Thank you

PS 

At least when I right click on properties that where it says they are at.


Just type this code in terminal  .The terminal is at applications>accessories>terminal

```
sudo cp /media/cdrom0/Setup/Data/pak* /usr/local/games/quake4/q4base
```

---

### Post by kayfes on 2008-06-09
steven@steven-desktop:~$ sudo cp /media/cdrom0/Setup/Data/pak* /usr/local/games/quake4/q4base
[sudo] password for steven: 
cp: cannot stat `/media/cdrom0/Setup/Data/pak*': No such file or directory
steven@steven-desktop:~$ 

If the directory is wrong how do I find the right one?  Gonna look back through the posts again and see if I messed up somewhere.

It sucks being a noob but every time I have troubles I get on this forum and everyone is very helpful so thank you all.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> steven@steven-desktop:~$ sudo cp /media/cdrom0/Setup/Data/pak* /usr/local/games/quake4/q4base
[sudo] password for steven: 
cp: cannot stat `/media/cdrom0/Setup/Data/pak*': No such file or directory
steven@steven-desktop:~$ 

If the directory is wrong how do I find the right one?  Gonna look back through the posts again and see if I messed up somewhere.

It sucks being a noob but every time I have troubles I get on this forum and everyone is very helpful so thank you all.


Can u do this>>> ```
cd /media/cdrom0/Data
```

and also ```
ls -l
``` after this step.

---

### Post by Rhubarb on 2008-06-09
Just put my Q4 DVD in, the pak files are in another directory.
So just try this:

```
sudo cp /media/cdrom0/Setup/Data/q4base/pak* /usr/local/games/quake4/q4base
```

---

### Post by rajeev1204 on 2008-06-09
> **Rhubarb said:**
> Just put my Q4 DVD in, the pak files are in another directory.
So just try this:

```
sudo cp /media/cdrom0/Setup/Data/q4base/pak* /usr/local/games/quake4/q4base
```

Hey thanks man. I think thats the problem.I lost my quake cds so i dont know exact place.:)

---

### Post by kayfes on 2008-06-09
steven@steven-desktop:~$ cd /media/cdrom0/Data
bash: cd: /media/cdrom0/Data: No such file or directory
steven@steven-desktop:~$ ls -l
total 300512
drwxr-xr-x 2 steven steven      4096 2008-06-09 00:16 Desktop
drwxr-xr-x 2 steven steven      4096 2008-06-07 11:01 Documents
lrwxrwxrwx 1 steven steven        26 2008-06-07 10:46 Examples -> /usr/share/example-content
drwxr-xr-x 2 steven steven      4096 2008-06-07 11:01 Music
-rwxr-xr-x 1 steven steven  19820877 2008-06-07 18:04 NVIDIA-Linux-x86-173.14.05-pkg1.run
drwxr-xr-x 2 steven steven      4096 2008-06-08 22:39 Pictures
drwxr-xr-x 2 steven steven      4096 2008-06-07 11:01 Public
-rw-r--r-- 1 steven steven 287552973 2008-06-08 23:51 quake4-linux-1.4.2.x86.run
drwxr-xr-x 2 steven steven      4096 2008-06-07 11:01 Templates
drwxr-xr-x 2 steven steven      4096 2008-06-07 11:01 Videos
-rw-r--r-- 1 root   root        1516 2008-06-07 18:45 xorg.conf.backup
steven@steven-desktop:~$ 




I have the CD version with 4 cds, I bought this game a while ago when I first got a decent vga card a 7 series but now I have a 9800gt and have the drivers and everything running in Ubuntu including my cube desktop which is ******* cool by the way.  All I want to do is play a game using my new card.  Completely given up on Microsoft comp crashed all the time anyways thus I couldn't play games so if I can play one game its a step up ;)

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> steven@steven-desktop:~$ cd /media/cdrom0/Data
bash: cd: /media/cdrom0/Data: No such file or directory



I have the CD version with 4 cds, I bought this game a while ago when I first got a decent vga card a 7 series but now I have a 9800gt and have the drivers and everything running in Ubuntu including my cube desktop which is ******* cool by the way.  All I want to do is play a game using my new card.  Completely given up on Microsoft comp crashed all the time anyways thus I couldn't play games so if I can play one game its a step up ;)


I too have the version with 4 cds. Not a problem.

Insert cd again and check under filesystem/media/cdrom if its there.

---

### Post by kayfes on 2008-06-09
Yeah its there.  So I did everything you guys said to where do I go from here?

Thank you again guys.

---

### Post by kayfes on 2008-06-09
code:

sudo cp /media/cdrom0/Setup/Data/q4base/pak* /usr/local/games/quake4/q4base


And it hangs there for a while then brings me back to steven@steven-desktop:~$ 


Is that good or bad?

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> Yeah its there.  So I did everything you guys said to where do I go from here?

Thank you again guys.


Maybe it has copied the files?

Did u get any message ?

---

### Post by kayfes on 2008-06-09
> **rajeev1204 said:**
> hmm

that doesn't sound good yo.

---

### Post by rajeev1204 on 2008-06-09
Ok lets try mounting the cd with proper permissions.

```
sudo umount /dev/cdrom0
```

```
sudo mount -t iso9660  -o norock /dev/scd0 /media/cdrom0

```

Try this.```

```.Then check again under media/cdrom0.

Please let me know.

---

### Post by kayfes on 2008-06-09
steven@steven-desktop:~$ sudo umount /dev/cdrom0
[sudo] password for steven: 
umount: /dev/cdrom0: not found
steven@steven-desktop:~$ sudo mount -t iso9660  -o norock /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
steven@steven-desktop:~$ 

thats what I got sorry for the long wait for the reply had to get some food haha.

Thank you again everyone.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> steven@steven-desktop:~$ sudo umount /dev/cdrom0
[sudo] password for steven: 
umount: /dev/cdrom0: not found
steven@steven-desktop:~$ sudo mount -t iso9660  -o norock /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
steven@steven-desktop:~$ 

thats what I got sorry for the long wait for the reply had to get some food haha.

Thank you again everyone.


ok good we made some progress it seems.

```
sudo umount /dev/scd0
```

```
 sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0

```


btw, i too had some lunch :)

---

### Post by kayfes on 2008-06-09
this is what i got:

steven@steven-desktop:~$ sudo umount /dev/scd0
steven@steven-desktop:~$  sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected but explicit `-w' flag given
steven@steven-desktop:~$ 

thanks for the help

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> this is what i got:

steven@steven-desktop:~$ sudo umount /dev/scd0
steven@steven-desktop:~$  sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected but explicit `-w' flag given
steven@steven-desktop:~$ 

thanks for the help

good.

it should be mounted now with right permissions.

navigate to /media/cdrom0 and check the contents

---

### Post by MaindotC on 2008-06-09
rajeev you have a lot more patience than I will ever have in my life.

---

### Post by kayfes on 2008-06-09
What should I be looking for in cdrom0?  I should note that I have never had the option to insert another cd except for the first one.  I don't see how I can play Q4 without using all the disks.  Thanks again.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> What should I be looking for in cdrom0?  I should note that I have never had the option to insert another cd except for the first one.  I don't see how I can play Q4 without using all the disks.  Thanks again.


U have to manually insert each cd and copy the pak files.

First, tell me, whats under /media/cdrom0??

---

### Post by kayfes on 2008-06-09
/media/cdrom0/DirectX
/media/cdrom0/Docs
/media/cdrom0/Setup
/media/cdrom0/0x0409.ini
/media/cdrom0/00000001.TMP
/media/cdrom0/autorun.inf
/media/cdrom0/DrvMgt.dll
/media/cdrom0/instmsia.exe
/media/cdrom0/instmsiw.exe
/media/cdrom0/ISScript9.Msi
/media/cdrom0/Quake 4(TM).msi
/media/cdrom0/SECDRV.SYS
/media/cdrom0/setup.exe
/media/cdrom0/Setup.ini
/media/cdrom0/version.inf


damn I am kind of lost here.

---

### Post by kayfes on 2008-06-09
If I posted what you needed.  Thank you once again.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> If I posted what you needed.  Thank you once again.

Yes this is what i was looking for.

whats under /media/cdrom0/Setup ??

We are almost done here :)

---

### Post by kayfes on 2008-06-09
Which do you want me to go into?

/media/cdrom0/Setup/Data
/media/cdrom0/Setup/rsrc

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> Which do you want me to go into?

/media/cdrom0/Setup/Data
/media/cdrom0/Setup/rsrc


go to data and tell me whats there

---

### Post by kayfes on 2008-06-09
/media/cdrom0/Setup/Data/pb
/media/cdrom0/Setup/Data/q4base
/media/cdrom0/Setup/Data/MayaImportx86.dll
/media/cdrom0/Setup/Data/Mss32.dll
/media/cdrom0/Setup/Data/mssvoice.asi
/media/cdrom0/Setup/Data/Quake4.exe
/media/cdrom0/Setup/Data/Quake4Ded.exe
/media/cdrom0/Setup/Data/Toolsx86.dll

I hope this works

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> /media/cdrom0/Setup/Data/pb
/media/cdrom0/Setup/Data/q4base
/media/cdrom0/Setup/Data/MayaImportx86.dll
/media/cdrom0/Setup/Data/Mss32.dll
/media/cdrom0/Setup/Data/mssvoice.asi
/media/cdrom0/Setup/Data/Quake4.exe
/media/cdrom0/Setup/Data/Quake4Ded.exe
/media/cdrom0/Setup/Data/Toolsx86.dll

I hope this works


ok now do this step. copy and paste

```
sudo cp -a /media/cdrom0/Setup/Data/q4base /usr/local/games/quake4
```

---

### Post by kayfes on 2008-06-09
> **rajeev1204 said:**
> U have to manually insert each cd and copy the pak files.

First, tell me, whats under /media/cdrom0??



Its just hanging there.  I think this is where I am getting stuck at.  How should I go about doing that?  Thanks again sorry for being such a noob.

---

### Post by kayfes on 2008-06-09
This is what I get:


steven@steven-desktop:~$ sudo cp -a /media/cdrom0/Setup/Data/q4base /usr/local/games/quake4
[sudo] password for steven: 
 
steven@steven-desktop:~$

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> Its just hanging there.  I think this is where I am getting stuck at.  How should I go about doing that?  Thanks again sorry for being such a noob.

Its not hanging. its copying the files.

Let it finish the process .

U can check whether files are copied by navigating to /usr/local/games/quake4/q4base .

Paste the contents here.

thanks.good luck.

---

### Post by kayfes on 2008-06-09
/usr/local/games/quake4/q4base/arena_ctf.cfg
/usr/local/games/quake4/q4base/ctf.cfg
/usr/local/games/quake4/q4base/dm.cfg
/usr/local/games/quake4/q4base/game000.pk4
/usr/local/games/quake4/q4base/game100.pk4
/usr/local/games/quake4/q4base/game200.pk4
/usr/local/games/quake4/q4base/mapcycle.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-mp1.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-mp2.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-mp3.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-q4cmp_pak001.scriptcfg
/usr/local/games/quake4/q4base/pak010.pk4
/usr/local/games/quake4/q4base/pak011.pk4
/usr/local/games/quake4/q4base/pak012.pk4
/usr/local/games/quake4/q4base/pak013.pk4
/usr/local/games/quake4/q4base/pak014.pk4
/usr/local/games/quake4/q4base/pak015.pk4
/usr/local/games/quake4/q4base/pak016.pk4
/usr/local/games/quake4/q4base/pak017.pk4
/usr/local/games/quake4/q4base/pak018.pk4
/usr/local/games/quake4/q4base/pak019.pk4
/usr/local/games/quake4/q4base/pak020.pk4
/usr/local/games/quake4/q4base/pak021.pk4
/usr/local/games/quake4/q4base/pak022.pk4
/usr/local/games/quake4/q4base/q4cmp_pak001.pk4
/usr/local/games/quake4/q4base/teamdm.cfg
/usr/local/games/quake4/q4base/tourney.cfg
/usr/local/games/quake4/q4base/zpak_czech_01.pk4.off
/usr/local/games/quake4/q4base/zpak_czech_02.pk4.off
/usr/local/games/quake4/q4base/zpak_english.pk4
/usr/local/games/quake4/q4base/zpak_english_01.pk4
/usr/local/games/quake4/q4base/zpak_english_02.pk4
/usr/local/games/quake4/q4base/zpak_english_03.pk4
/usr/local/games/quake4/q4base/zpak_english_04.pk4
/usr/local/games/quake4/q4base/zpak_french_01.pk4.off
/usr/local/games/quake4/q4base/zpak_french_02.pk4.off
/usr/local/games/quake4/q4base/zpak_french_03.pk4.off
/usr/local/games/quake4/q4base/zpak_french_04.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_01.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_02.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_03.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_04.pk4.off
/usr/local/games/quake4/q4base/zpak_polish_01.pk4.off
/usr/local/games/quake4/q4base/zpak_polish_02.pk4.off
/usr/local/games/quake4/q4base/zpak_russian_01.pk4.off
/usr/local/games/quake4/q4base/zpak_russian_02.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_01.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_02.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_03.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_04.pk4.off


Thank you

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> /usr/local/games/quake4/q4base/arena_ctf.cfg
/usr/local/games/quake4/q4base/ctf.cfg
/usr/local/games/quake4/q4base/dm.cfg
/usr/local/games/quake4/q4base/game000.pk4
/usr/local/games/quake4/q4base/game100.pk4
/usr/local/games/quake4/q4base/game200.pk4
/usr/local/games/quake4/q4base/mapcycle.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-mp1.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-mp2.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-mp3.scriptcfg
/usr/local/games/quake4/q4base/mapcycle-q4cmp_pak001.scriptcfg
/usr/local/games/quake4/q4base/pak010.pk4
/usr/local/games/quake4/q4base/pak011.pk4
/usr/local/games/quake4/q4base/pak012.pk4
/usr/local/games/quake4/q4base/pak013.pk4
/usr/local/games/quake4/q4base/pak014.pk4
/usr/local/games/quake4/q4base/pak015.pk4
/usr/local/games/quake4/q4base/pak016.pk4
/usr/local/games/quake4/q4base/pak017.pk4
/usr/local/games/quake4/q4base/pak018.pk4
/usr/local/games/quake4/q4base/pak019.pk4
/usr/local/games/quake4/q4base/pak020.pk4
/usr/local/games/quake4/q4base/pak021.pk4
/usr/local/games/quake4/q4base/pak022.pk4
/usr/local/games/quake4/q4base/q4cmp_pak001.pk4
/usr/local/games/quake4/q4base/teamdm.cfg
/usr/local/games/quake4/q4base/tourney.cfg
/usr/local/games/quake4/q4base/zpak_czech_01.pk4.off
/usr/local/games/quake4/q4base/zpak_czech_02.pk4.off
/usr/local/games/quake4/q4base/zpak_english.pk4
/usr/local/games/quake4/q4base/zpak_english_01.pk4
/usr/local/games/quake4/q4base/zpak_english_02.pk4
/usr/local/games/quake4/q4base/zpak_english_03.pk4
/usr/local/games/quake4/q4base/zpak_english_04.pk4
/usr/local/games/quake4/q4base/zpak_french_01.pk4.off
/usr/local/games/quake4/q4base/zpak_french_02.pk4.off
/usr/local/games/quake4/q4base/zpak_french_03.pk4.off
/usr/local/games/quake4/q4base/zpak_french_04.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_01.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_02.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_03.pk4.off
/usr/local/games/quake4/q4base/zpak_italian_04.pk4.off
/usr/local/games/quake4/q4base/zpak_polish_01.pk4.off
/usr/local/games/quake4/q4base/zpak_polish_02.pk4.off
/usr/local/games/quake4/q4base/zpak_russian_01.pk4.off
/usr/local/games/quake4/q4base/zpak_russian_02.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_01.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_02.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_03.pk4.off
/usr/local/games/quake4/q4base/zpak_spanish_04.pk4.off


Thank you

Yes my friend.Its been copied.

Now insert 2nd cd and repeat as follows


```
sudo umount /dev/scd0
```

```
sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0
```

```
sudo cp  /media/cdrom0/Setup/Data/q4base/*.pk4 /usr/local/games/quake4
```


Repeat for 3rd and 4th cd.

Let me know.

---

### Post by kayfes on 2008-06-09
And then am I going to do that for the follwing 2 disks?

Smoke break by the way thank you again I am so glad I made the switch to Linux.  **** I would even be able to run my comp for the time I took to do all of this in windows let alone be able to play a damn game. thanks.

---

### Post by kayfes on 2008-06-09
Here i go thanks for the patience.

---

### Post by kayfes on 2008-06-09
Now what should I do?

---

### Post by kayfes on 2008-06-09
Gonna do it again for cd 3 and 4 like you said.  Duh.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> Gonna do it again for cd 3 and 4 like you said.  Duh.


oops sorry small error

```
sudo cp -v /media/cdrom0/Setup/Data/q4base/*.pk4 /usr/local/games/quake4/q4base
```

Thats the right code for 2 3 and 4 th cd

After u r done copying all 4, paste contents of /usr/local/games/quake4/q4base.


I apologise for that mistake.

---

### Post by rajeev1204 on 2008-06-09
Steps for cd 2 3 and 4. after inserting each cd.

```
sudo umount /dev/scd0
```

```
sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0
```

```
sudo cp -v /media/cdrom0/Setup/Data/q4base/*.pk4 /usr/local/games/quake4/q4base
```


Repeat for 3rd and 4th cd.

Let me know.[/QUOTE]

---

### Post by kayfes on 2008-06-09
> **rajeev1204 said:**
> Steps for cd 2 3 and 4. after inserting each cd.

```
sudo umount /dev/scd0
```

```
sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0
```

```
sudo cp -v /media/cdrom0/Setup/Data/q4base/*.pk4 /usr/local/games/quake4/q4base
```


Repeat for 3rd and 4th cd.

Let me know.[/QUOTE]


Ok Was getting error messages will try with that last post and update thanks again.

---

### Post by kayfes on 2008-06-09
steven@steven-desktop:~$ sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected but explicit `-w' flag given
steven@steven-desktop:~$

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> steven@steven-desktop:~$ sudo mount -t iso9660  -rw -o norock /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected but explicit `-w' flag given
steven@steven-desktop:~$

its normal message.

Just copy paste the 3rd piece of code i gave u.

---

### Post by kayfes on 2008-06-09
steven@steven-desktop:~$ sudo cp -v /media/cdrom0/Setup/Data/q4base/*.pk4 /usr/local/games/quake4/q4base
cp: cannot stat `/media/cdrom0/Setup/Data/q4base/*.pk4': No such file or directory
steven@steven-desktop:~$ 


for the 3rd code?

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> steven@steven-desktop:~$ sudo cp -v /media/cdrom0/Setup/Data/q4base/*.pk4 /usr/local/games/quake4/q4base
cp: cannot stat `/media/cdrom0/Setup/Data/q4base/*.pk4': No such file or directory
steven@steven-desktop:~$ 


for the 3rd code?


aargh.

ok tell me whats under /media/crom0/..... all the contents

---

### Post by kayfes on 2008-06-09
And when I put it in the drive it tells me it can't display the contents of the drive.

---

### Post by rajeev1204 on 2008-06-09
> **kayfes said:**
> And when I put it in the drive it tells me it can't display the contents of the drive.


Then try 1st and 2nd piece of code . 

then try to navigate to /media/cdrom0

---

### Post by kayfes on 2008-06-09
I have to sleep now thanks for the help I will jump on this thread tomorrow night and try from step one and see what happens.  Thank you again.  Any help you can give until then would be much appreciated.

---

### Post by kayfes on 2008-06-09
I am not able to acces /media/cdrom0.  I get this error message:

You do not have the permissions necessary to view the contents of "cdrom0".

---

### Post by kayfes on 2008-06-10
Ok So I started from the beginning and I copied the codes to the files.  Now I am guessing here but the reason the other cds were giving me heck was the fact that I didn't need any files from them.  I got tired of well trying to install the files and tried to run it.  My first attempt to run didn't work the command quake4 didn't work so I used sudo quake4 and wuddah you know the game works with the exception of sound but I don't think thats the game I believe its my sound card not working in general at the moment.  So on to fix that and thank all of you that helped me out!

---

### Post by rajeev1204 on 2008-06-10
> **kayfes said:**
> Ok So I started from the beginning and I copied the codes to the files.  Now I am guessing here but the reason the other cds were giving me heck was the fact that I didn't need any files from them.  I got tired of well trying to install the files and tried to run it.  My first attempt to run didn't work the command quake4 didn't work so I used sudo quake4 and wuddah you know the game works with the exception of sound but I don't think thats the game I believe its my sound card not working in general at the moment.  So on to fix that and thank all of you that helped me out!


Glad to know its working.

Dont use sudo for running the game. 

Try this command ```
sudo chown -R steven\:.quake4
```


Now run the game without sudo.


regards

Rajeev

P.S.iam sure u somehow copied all 4 cd files to location or game wont run.

For sound not working> stop all other applications running in background like rhythmbox etc.

---

### Post by MaindotC on 2008-06-10
keyfes if you need to go through all that just to get files of a cd you're installation has majour issues.  You may want to consider a nice, fresh, clean install.

---

### Post by rajeev1204 on 2008-06-13
> **strAlan said:**
> rajeev you have a lot more patience than I will ever have in my life.



Patience is always a virtue.  :):)




regards

rajeev

---

