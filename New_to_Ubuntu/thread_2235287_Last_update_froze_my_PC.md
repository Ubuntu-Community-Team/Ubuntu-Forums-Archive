---
title: "Last update froze my PC"
date: 2014-07-20
forum: New to Ubuntu
---

### Post by harfin on 2014-07-20
On 17/7 I was advised of series of updates for my 64 bit version of 12.04
I have a dual boot with Windows XP
I have a Zoostorm with a A55MX/A75MX series motherboard
The first batch of updates completed without problems (new linux version etc)
There was one further update regarding (as near as I can recall) to hardware support that needed to be updated. As it came via update manager I assume that the update is 'kosher' ??
I left the download to run & complete as I was off to do my voluntary work that day
When I returned there was an on=screen message asking for my user name and password. The system repeatedly rejected my entries of the details it sought. Yes, I do know my user name and yes I do know my password
The system was going nowhere, so the safest option seemed to me was to take the option at startup to reurn to the previous version of Linux.
That alas caused my system to freeze. Initially I thought it might be downloading ex the net the earlier linux, as the WiFi adapter light flashed periodically, after several hours with nothing but a blank screen, it seems that that was not the case
I am still able to access at startup the options I mentioned earlier, but I guess it would be safer to start completely afresh. I have the iso of 12.04 on a memory stick as well as on the Windows XP desktop
Suggestions please as to where/what now would be appreciated.
My biggest hassle will be (groan, groan) that my last backup of my ubuntu & Open Office files/images etc and my Evolution saved emails / email address book is well out of current (pre crash) position.
Help!!!

---

### Post by bapoumba on 2014-07-20
Maybe have a look here : [http://ubuntuforums.org/showthread.php?t=2234478](http://ubuntuforums.org/showthread.php?t=2234478)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

---

### Post by harfin on 2014-07-20
If I understand you correctly:
a) My current ubuntu installation has probably been irrevocably damaged by attempting to revert to an earlier version. As my WinXP on the PC is working properly, however, does that mean the partitions do not appear to be damaged
c) Last year when I installed the 64 bit ubuntu 12.04 I was informed that it would continue to be supported for at least a couple of years.  Are you suggesting that I should move on to a later version of 64 bit ubuntu?
d) Is your advice aslo that I should update my PC hardware
e) Is there **any** chance to recover any of files etc from the disc partition that houses my current installation

Regards
Alan

---

### Post by howefield on 2014-07-20
> **harfin said:**
> a) My current ubuntu installation has probably been irrevocably damaged by attempting to revert to an earlier version. As my WinXP on the PC is working properly, however, does that mean the partitions do not appear to be damaged
c) Last year when I installed the 64 bit ubuntu 12.04 I was informed that it would continue to be supported for at least a couple of years.  Are you suggesting that I should move on to a later version of 64 bit ubuntu?
d) Is your advice aslo that I should update my PC hardware
e) Is there **any** chance to recover any of files etc from the disc partition that houses my current installation

Chances are that you will be able to boot from a Live USB/DVD allowing you to mount the relevant partition and copy your files to safety.

12.04 is supported till April 2017, however the latest LTS 14.04 is supported till 2019. If you are doing a fresh install anyway, the choice is yours.

---

### Post by bapoumba on 2014-07-20
Not running the HWE, I can only recommend what others have recommended too. Support is through 2017 as far as I can read. Have you tried booting from a previously working kernel ? Is that what you mean by "startup to return to the previous version of Linux" ?
Will ping kansasnoob about your thread, he is the one :)

As far as saving your data, you can always do that from a live session.

Edit : ninja'd by howefield. Well, not ninja'd really, I'm completely behind.. Will teach me to do other things while having a reply open and not submitted :)

---

### Post by harfin on 2014-07-20
so insert my 12.04 iso usb stick and reboot?

---

### Post by harfin on 2014-07-20
then what?

---

### Post by Rob Sayer on 2014-07-20
You have to mount/open the pc hard drive from the file manager you have on the live CD.  Then copy away.  See:

[http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd](http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd)

---

### Post by kansasnoob on 2014-07-20
If you try and boot the PC does the grub menu show the newer series kernel (3.13.0-32)?

If so exactly what happens when you try to boot that kernel?

---

### Post by harfin on 2014-07-20
I received screen-full that said some of existing system files were damaged and would I like them repaired to which I agreed.
I now have a flashing line cursor at bottom of monitor screen, which I assume means something is being downloaded

Am awaiting further delelopements / results

Still seems to be downloading as the cursor is still flashing three hours after it started. Or is it hanging again?

Aborted due to no continuing action.
Another try tomorrow

it asks for my logon
then my password
after 'enter' it loops and asks for my login/password again.
I know my user name and my password!
Is it possible to reset it?

> **kansasnoob said:**
> If you try and boot the PC does the grub menu show the newer series kernel (3.13.0-32)?

If so exactly what happens when you try to boot that kernel?

I selected the version you quote (it's top of the list) but went in via recovery mode initially. I then exited recovery mode and went to normal boot.
The screen then showed several screens full of text / actions etc (far too quick scrolling to read), then it opened up with
"Ubuntu 12.04.04 LTS ubuntu tty1"
"ubuntu login: " with flashing line cursor
I enter my username and hit enter
"password"
I enter my password and hit enter
It loops back to "Ubuntu 12.04.04 LTS ubuntu tty1" etc etc

I know my login and password!
Can I reset login and password again?
Alan

---

### Post by harfin on 2014-07-21
> **Rob Sayer said:**
> You have to mount/open the pc hard drive from the file manager you have on the live CD.  Then copy away.  See:

[http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd](http://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd)

I am using an iso usb stick (this was the one I used to set up 12.04 a year ago app

Not sure if this is exactly the same as a 'live CD'

---

### Post by Vladlenin5000 on 2014-07-21
> **harfin said:**
> I am using an iso usb stick (this was the one I used to set up 12.04 a year ago app

Not sure if this is exactly the same as a 'live CD'

Yes, that's a "live CD" (actually a "live DVD" now due to its size). Just make sure it is OK. Something from a year ago can be corrupted now (not likely if the USB stick is of good quality and has been stored properly).

---

### Post by harfin on 2014-07-21
> **howefield said:**
> Chances are that you will be able to boot from a Live USB/DVD allowing you to mount the relevant partition and copy your files to safety.

12.04 is supported till April 2017, however the latest LTS 14.04 is supported till 2019. If you are doing a fresh install anyway, the choice is yours.

I have a dual boot set up. So do I place the usb stick into a slot whilst I am in Windows XP and then reboot or do I turn off the PC then insert the usb stick?

Do I then have to direct the pc to boot from that stick? If so, how?

I also have the iso on my Windows desktop; would it be simpler to re-boot from there?

---

### Post by harfin on 2014-07-21
> **Vladlenin5000 said:**
> Yes, that's a "live CD" (actually a "live DVD" now due to its size). Just make sure it is OK. Something from a year ago can be corrupted now (not likely if the USB stick is of good quality and has been stored properly).

The stick has been kept specifically for that purpose only. Apart from the initial boot when I installed 12.04, it has not been used (or re-used)

I just posted a couple of questions about when / how I proceed
i.e
[COLOR=#000000]I have a dual boot set up. So do I place the usb stick into a slot whilst I am in Windows XP and then reboot or do I turn off the PC then insert the usb stick?[/COLOR]

[COLOR=#000000]Do I then have to direct the pc to boot from that stick? If so, how?[/COLOR]

[COLOR=#000000]I also have the iso on my Windows desktop; would it be simpler to re-boot from there?[/COLOR]

---

### Post by harfin on 2014-07-21
Anyone?

---

### Post by Vladlenin5000 on 2014-07-21
You boot as you usually would for any live session: Turn off, insert USB, turn on, select to boot from the USB.
(EDIT) and no, you cannot boot from a ISO file in Windows.

---

### Post by harfin on 2014-07-21
> **Vladlenin5000 said:**
> You boot as you usually would for any live session: Turn off, insert USB, turn on, select to boot from the USB.
(EDIT) and no, you cannot boot from a ISO file in Windows.

The reason I asked that question was that the only time I have used it before I was replacing a version of ubuntu that I wanted overwritten

This time I would like to set up ubuntu again and to retrieve files etc that are accessed only from ubuntu. Once that's done, then I plan to replace my version with the latest LTS version (14.04 it is I believe).

So when I re-boot (with memory stick in place!) how do I tell my PC how to boot from the memory stick? I assume this must be within the 1st stage of booting (before I get to choice between windows and ubuntu)

---

### Post by harfin on 2014-07-21
> **harfin said:**
> The reason I asked that question was that the only time I have used it before I was replacing a version of ubuntu that I wanted overwritten

This time I would like to set up ubuntu again and to retrieve files etc that are accessed only from ubuntu. Once that's done, then I plan to replace my version with the latest LTS version (14.04 it is I believe).

So when I re-boot (with memory stick in place!) how do I tell my PC how to boot from the memory stick? I assume this must be within the 1st stage of booting (before I get to choice between windows and ubuntu)

Is it via the grub command line?  If so, whats command for boot from (whatever drive my memory stick is)??

---

### Post by Vladlenin5000 on 2014-07-21
That depends entirely on your computer since it's a BIOS/UEFI settings and the procedure is exactly the same as before. What you gonna do after booting in a live session as no bearing ijn the way it boots.

---

### Post by harfin on 2014-07-21
Not sure why, but after running it I got: 
"Ubuntu 12.04.4 LTS ubuntu tty1
Ubuntu login: "  (I entered my login name)
"Password:" (Ientered my password -it worked!
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.13.0-32-generic x86_64)
* Documentation:[https://help.ubuntu.com/](https://help.ubuntu.com/)
Our Hardware Enablement Stack (HWE) is supported until April 2017
alanhart"ubuntu:~$ _"(flashing line cursor)

So what do I have to do now please?  No menu - nothing else on screen.
Do I have to start something?  
Do I have to run something?
Do I have to go to some menu?
What - please!

---

### Post by bapoumba on 2014-07-21
Please sse some discussion here : [http://ubuntuforums.org/showthread.php?t=2234478](http://ubuntuforums.org/showthread.php?t=2234478)
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264) < see if comment #10 could apply to you.

---

### Post by harfin on 2014-07-21
> **bapoumba said:**
> Please sse some discussion here : [http://ubuntuforums.org/showthread.php?t=2234478](http://ubuntuforums.org/showthread.php?t=2234478)
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264) < see if comment #10 could apply to you.

I tried that suggestion as it seemed to reply.
Alas, my system is now hanging again.

---

### Post by harfin on 2014-07-22
So back where I started
An update via update manager i.e. **recommended **by Ubuntu, is causing my system to hang.
Am I happy
**What now?**

---

### Post by bapoumba on 2014-07-22
From what I understand the problem lies between Trusty Xstack and Precise.
> Only installing the original precice Xstack (xserver-xorg-lts-precise), which removes the current xstack and after that installing the trusty xstack in one step without restart, works.

Would upgrading to Trusty be an option for you ?

---

### Post by harfin on 2014-07-22
> **bapoumba said:**
> From what I understand the problem lies between Trusty Xstack and Precise.


Would upgrading to Trusty be an option for you ?

If it's going to get me back 'on-air' then it would certainly!

Big question though, is what do I need to do - step by step please

Alan

---

### Post by harfin on 2014-07-22
If I load an official linux dvd of 14.04LTS into my dual boot pc, will it enable me to do both things, i.e. retrieve my existing files etc and enable me to get the latest version and thus avoid this impasse over 'trusty' and 'precise'

Anyone?

---

### Post by bapoumba on 2014-07-22
If the procedure outlined in the bug report has not worked for you, it would be helpful to comment in that bug report.

Steps to upgrading or fresh installing will depend on your current setup. I gather you are dual-booting with windows XP, which I have no experience about. 

Should you choose to fresh install over Precise, please see the link in my sig for a current bug and this general howto : [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). Make sure that you choose "Do something else" when prompted at the partitioning level and get your current partitions with the following to be sure which partition to use for the root filesystem.
```
cat /etc/fstab
```

Of course, have backups for anything you may not afford to loose. As already said, you can back up your files from a live session, be it from usb, dvd etc.

Upgrading will also depend on your setup. You need to remove any ppa or third party repo you are using.

I'd favor a fresh install, as the hardware stack may have brought in packages that you wont need in Trusty.

---

