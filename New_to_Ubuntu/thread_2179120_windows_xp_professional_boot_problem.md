---
title: "windows xp professional boot problem"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by mike109 on 2013-10-06
I have just completed the installation of ubuntu 13.04 alongside an existing Windows XP professional system. The installation had no apparent problems and I was able to boot to Ubuntu but I cannot now into Windows as "A disk read error occured". I am totally new to Ubuntu and my only knowledge in this area is very very rusty and crumbling command line Unix.

---

### Post by DuckHook on 2013-10-06
Please describe in detail the steps you took to install. Also, please post results of terminal commands:```
sudo fdisk -l
``````
sudo parted -l
```You will be asked for your password. Typing your password will return no feedback at all. This is designed behaviour for security.

---

### Post by mike109 on 2013-10-06
My first stage was to download Ubuntu 13.04 in windows XP professional within the machine I was planning to load Ubuntu. Following that I burned the complete iso file to a DVD using Infra Recorder. Leaving the DVD in the machine I rebooted and followed the steps as directed. The only options I remember that required decisions were twofold. First there was a request to vary the partition size. It was of the order 50/50, I made no adjustments. The second decision was to allow updates which I elected to take. I have one concern in that on completion of the installation the machine did not shutdown to the extent of powering off. My memory fails me on the exact comment on the screen but there was an "[OK]" on the right hand side of the screen and everything seemed complete. I waited something of the order of 3 to 5 minutes. There was no disc activity so I powered off.
Terminal commands. First time I have seen Ubuntu or Linux for that matter. I am sure the commands are very similar to Unix commands which in turn are not a million miles from MsDos, But at this moment I cannot see how to get command entry screen. It is quite late in this part of the World so that revelation will have to be postponed until tomorrow.

---

### Post by DuckHook on 2013-10-06
> **mike109 said:**
> ...It is quite late in this part of the World so that revelation will have to be postponed until tomorrow. No problem at all. Take your time.

The Ubuntu terminal can be invoked in all sorts of ways, but the easiest way right now is just to use <Ctrl>+<Alt>+<t>.

Also, did you backup all important data from XP before installing? If not, then it is **EXTREMELY IMPORTANT** that you stop booting up from your HDD and just use a LiveDVD session to communicate with this forum from now on. The concern would be that you somehow nuked your XP installation during your Ubuntu install. This probably did not happen (don't panic) but better safe than sorry.

When you can give us the results of the two commands, forum members will be in a better position to advise.

---

### Post by mike109 on 2013-10-08
I realised I was going to need a lot of time for the command responses. There has to be an easier way but that option has to be in the future. As this is by hand I will abbreviate a little but where do I draw the line - here goes
**_FDISK_**
Disk sda 500.1  Total sectors 976771055

       boot         start            end          blocks     ID     System
sda1 *                 63   534031575   267015756+    7   HPFS/NTFS/exFAT
sda2         534032382   976769023   221368321     5    Extended
sda5         534032384   972580863   219274240    83    Linux
sda6         972582912   976769023      2093056    82    Linux swap/Solaris

[B][U]PARTED
[/U][/B]
No     Start        End           Size          Type   File System           Flags
1       32.3kB     273GB      273GB       primary        ntfs                boot
2         273GB    500         227          extended     
5         273        498         225          logical         ext4
6         498        500        2143mb     logical          linux swap(v1)

It was a bit quicker than I thought and I have checked it

For the XP system there are backups but of course not simple ones. Everything can be recreated but will take several hours to achieve. The only thing that will be sad is to lose my Spotify "suggestions"

---

### Post by DuckHook on 2013-10-08
Well done. In future, you do not have to retype output. Simply drag your mouse across all of the terminal output. It will be highlighted. Then right click and select "copy". This will copy contents into clipboard buffer. Then "paste" into whatever text editor/dialogue box you happen to want it to go into.

With respect to your original problem:

The good news is that XP looks intact and was not wiped out. That's it in sda1 constituting approx half of your HDD. Should be a relatively simple matter to fix.

**CAUTION** These next steps will likely go well, but when tooling around with partitions, there are no guarantees. Worse come to worst, you may have to reinstall everything, so it's good that you have backups. This is not likely to happen... but just a heads up.

The easiest way to fix this problem is to run Boot-Repair. Instructions are [here]("https://help.ubuntu.com/community/Boot-Repair"). The site explains it better and more fully than I ever could, so no use in my just repeating what it already says. If you have any questions about it, post back here for info/clarifications first. If everything is clear to you, then proceed, and do let us know how it goes.

---

### Post by mike109 on 2013-10-09
I have tried Boot-Repair as suggested.
I downloaded the program on another PC and burned it to disc using Infra Recorder.
Booted this disc on the dodgy PC and ran the simple Recommended repair route.
Unfortunately did not work. I can still boot into Ubuntu but not Windows XP.
The message on completion of the disk-repair was [http://paste.ubuntu.com/621432](http://paste.ubuntu.com/621432)
Of course I have tried nothing else

---

### Post by oldfred on 2013-10-09
Your link to pastebin does not work. Best to see details.
But you probably need a Windows repair from your XP installer. Often chkdsk is required as after any resize of NTFS it needs chkdsk, but usually auto runs it on reboot.
       Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

---

### Post by mike109 on 2013-10-09
Before I start doing anything else there is just one thing it is worth mentioning. When running disk-repair it said this could run for several minutes. I would gues it was all over within a minute. I did have a thought that as I booted from a dvd the work was to the DVD rather than the hard disc. There is only one hard disc in the PC but there were no indications where the work was done.

---

### Post by DuckHook on 2013-10-10
Boot repair would have done its work on your HDD, not your DVD. It is designed with enough smarts to look at your HDD first.

Please follow *oldfred*'s advice and his links. He knows what he is talking about. Frankly, I breathed a sigh of relief when he came on to advise you.

---

### Post by mike109 on 2013-10-10
I have now attempted to recover the situation with the Windows Recovery Console.
CHKDSK did find errors on the disc and it recovered them.
Still no joy with Windows boot so I repeated the chkdsk with a /p to force a further check. Disc still OK.
The next thing was to repeat the boot-repair and reboot. The problem is unfortunately is still there.
The message this time from boot-repair was
[http://paste.ubuntu.com/6217312]("http://paste.ubuntu/6217312")

---

### Post by oldfred on 2013-10-10
Your link still does not work. Is this yours?
[http://paste.ubuntu.com/6217312/](http://paste.ubuntu.com/6217312/)

Update:
What are these two settings in Boot.ini?
[spybotsd]
timeout.old=30


At least partition looks normal & all the boot files are shown. But grub can only boot a working Windows. If chkdsk still had an error rerun it again. You often have to run until there are no errors as it does not fix everything on one pass.
You can from Boot-Repair or Windows install the Windows boot loader and see if it directly boots. Otherwise you need to try a full set of XP repairs.

       To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

   Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

   FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

   If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

   Boot files may need attributes also from Windows repair console:
attrib +r c:\filename
attrib +h c:\filename
attrib +s c:\filename

---

### Post by mike109 on 2013-10-11
I did do a quick reply but it has gone. Will I ever see it again. Really I am just checking.

---

### Post by mike109 on 2013-10-12
I certainly had a [http://paste.ubuntu.com/6217312](http://paste.ubuntu.com/6217312)
I have no idea where the Spybotsd and Timeout have come from - nothing to do with me.
I am struggling somewhat even to the extent of somehow losing my first attempt at this post. Precautions this time - preparing it well away from the Forum.
I used my XP Pro installation disc to enter the Recovery Console. At this point I was presented with two Windows installations. The first was Windows and the second Windowss. Looking at the content I felt Windowss was the installed version. I guess the other one was coming from going through the initial stages of XP installation before I got to the Recovery Console
I ignored FIXMBR and continued with FIXBOOT and BOOTCFG /REBUILD. When presented with two option to create a boot record I said no to the first and created one for the second under Windowss.
Then ran CHKDSK and ran into unrecoverable file condition.
I ran Boot-Repair the result was successful with [http://paste.ubuntu.com/6224526](http://paste.ubuntu.com/6224526). CHKDSK now ran clear.

Having completed this stage the situation is as before. I can boot into Ubuntu but I still get a disc error if I try Windows.

I an not sure whether I have exhausted this easier route or should I now try to mount my Windows drive etc

Of course this short note covers many other aborted attempts which has caused me much head scratching. I am becoming veryoldmike, lets be honest veryveryoldmike.

---

### Post by mike109 on 2013-10-13
Having booted Ubuntu I have been looking at the the files I have available from my Windows system. In the \windows\servicepackfiles\I386 there is nothing. In the parallel directory servicepackcache\I386 there are 19 files but not ntdetect.com or ntdlr. I have also checked the \windowss directory

---

### Post by fwYrn4Y on 2013-10-13
I had a similar issue. Grub seems to have found and fixed the missing OS

---

### Post by oldfred on 2013-10-14
Your BootInfo report looks normal, so it is some internal issue with XP. You should also have copies of boot files in your XP install disk, but that is where attribute may have to be changed.
Also typos in boot.ini can cause issues. If editing from Linux be sure to save with Windows line endings. Gedit now has that as an option.

 If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

---

### Post by mike109 on 2013-10-14
As you realise I am out of my depth. I have never edited a Boot.ini file so correcting one frightens the life out of me.
In an earlier note you asked me about Spybotsd. I did not think I had used that software on that PC but I have checked and of course there it is.
As you think it could be an internal issue with XP I resorted to my more sledgehammer approach and did a repair in the windows installation using the XP Professional installation disc. Of course by that I mean the more general Repair function not the Recovery Console. Nothing was achieved. 
What I still cannot understand is that there are two Windows installations on the hard disc Windows and Windowss. It is something I have done accidently rather than by design. I did repair both installations
Having mounted the Windows disc into Ubuntu I have taken a good and secure copy of those documents and settings files to an external disc. 
The PC has not too much on it as it has always been in my mind to make it a Media PC. In fact I was moving away from that idea with comparitive failure of Windows 8 and that was why I did the installation of Ubuntu.
With my inexperience is my best solution to start over again from scratch? New XP followed by new Ubuntu. I assume that is the better sequence.

---

### Post by oldfred on 2013-10-14
Did you run Windows repairs 3 times? It does not fix everything on one run. One will be reinstalling the Windows boot loader so have Ubuntu live installer available to reinstall grub after you get Windows working.

I do not see a second Windows entry in boot.ini, unless the spybot entry loads another entry somehow.

---

### Post by mike109 on 2013-10-16
In many ways this is now the start of a new thread.
However to complete the current thread. I did repairs 3 times as you suggested on both? Windows systems. Again no luck but maybe this is because the booting process following each repair never started because of the "disk error".
The other possibility is that this second windows system which you cannot see in boot.ini is causing some situation.
The net result is that I decided to reinstall Windows totally. Interestlngly it asked me which Windows system I wished to replace. I opted to reformat the partition to clear everything out. I next made an error in deleting the Ubuntu partition.
When does this become a new thread?
The Windows installation went comparatively smoothly trying to avoid a Yahoo toolbar and the resulting improbability that I could no longer load various drivers.
The long and short of it I finally had a viable XP system.
I then tried to reinstall Ubuntu and because I had deleted  the former installation and with it the root file system.
The absence of the root file system was causing me concerns on how to create one.
Next came a catastrophe.
Perched precariously I had an attack of cramp. I do realise this is not a medical forum.
I have no idea what happened other than my precarious perch crashed. Now I have a disc with a locked partial installation and no access to Ubuntu or my carefully reinstalled XP system.
Please do not laugh

---

### Post by oldfred on 2013-10-16
If grub installed then that is at the end of the install. You should be able to reinstall a Windows boot loader.
After any power failure while system is doing something you usually need chkdsk if Windows or fsck if Ubuntu. If partition table is corrupted then it is a bit more difficult.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Since new install I would suggest just reinstalling after you can get it to load. If issues then you may need testdisk. Or you can post from Boot-Repair a link to the BootInfo report so we can see what is where.

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by mike109 on 2013-10-16
Thank you for the input. I am working on things. It appears to be partitioning.
At the expense of being accused of bringing too much XP into a Ubuntu forum, before the disaster I tried something else. The XP installation disc is multi license, so the selfsame disc was used to create XP on another PC. It is my main PC and much used. The installation is old and I use Spybot regularly. So I tried the XP disc to Repair the System. Of course there is only one windows installation and having completed the repair I realise there was a major difference. The problem PC rebooted immediately after copying files, whereas the good PC continued through a full installation checking security code establishing networks etc etc. I do not what this says other than something had been corrupted during to original Ubuntu installation

---

### Post by oldfred on 2013-10-16
Windows resize always requires a chkdsk afterwards. Usually best to resize Windows and then immediately reboot it, so it can repair itself before installing Ubuntu. Sometimes the NTFS configuration is just not correct and causes issues.

---

### Post by mike109 on 2013-10-17
You will be astonished and relieved to know that I have a PC which allows me to boot into Ubuntu and also Windows XP.
Unfortunately I am not entirely certain how this has been achieved. I guess I have picked over those bites of knowledge you suggested and tried a few things. But I was careful to avoid anything that suggested editing. There were no revelations, nothing said something was now fixed. Your final suggestion to run testdisk (I ran it from Windows) resulted in no problems found. I then reinstalled and overwrote the remnants of Ubuntu and lo and behold.
Thank you I can now go forward

---

### Post by oldfred on 2013-10-17
Glad you got it working. 
Sometimes it just is the magic pixie dust that solves the problem. :)

---

