---
title: "Standard vs. Alternate 8.04 Ubuntu"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Arch Parsons on 2008-04-28
Hello,

I am wondering about the difference in the standard versus the alternate cd for Ubuntu Hardy Heron version.  I upgraded my Ubuntu 7.2 automatically within Ubuntu without a CD.  Does that mean I would have the 32-bit version now?  Assuming I do have the standard 32-bit version, can I or should I use the alternate cd to switch to the 64-bit version? I have a Intel P4 and have no trouble using 64-bit Vista or 64-bit XP.  Thanks in advance for any clarification on this.

---

### Post by aysiu on 2008-04-30
> **Arch Parsons said:**
> Hello,

I am wondering about the difference in the standard versus the alternate cd for Ubuntu Hardy Heron version.  I upgraded my Ubuntu 7.2 automatically within Ubuntu without a CD.  Does that mean I would have the 32-bit version now?  Assuming I do have the standard 32-bit version, can I or should I use the alternate cd to switch to the 64-bit version? I have a Intel P4 and have no trouble using 64-bit Vista or 64-bit XP.  Thanks in advance for any clarification on this. You can't just switch or upgrade from 32-bit to 64-bit. If you want to change to 64-bit, you're going to have to reinstall with the 64-bit version of Ubuntu.

This has nothing to do with Alternate versus Desktop CDs. The Alternate and Desktop are just two different ways to install Ubuntu - they are not necessarily 32-bit or 64-bit.

In other words, there are four different versions in question here:
Alternate 32-bit CD
Desktop 32-bit CD
Alternate 64-bit CD
Desktop 64-bit CD

If you had Ubuntu 7 something (there is no 7.2, so you must have had either 7.04 or 7.10) with 32-bit before, and you upgraded via the internet, you now have Ubuntu 8.04 32-bit. You would have achieved the same effect by upgrading with the 32-bit Alternate CD or reinstalling with the 32-bit Desktop CD.

The only way to get from what you have now to having 64-bit Ubuntu is by using the Alternate or Desktop 64-bit CD to reinstall Ubuntu.

---

### Post by tyroeternal on 2008-04-30
The alternate cd essentially is the same thing as the normal one except instead of it being a live cd where you load up the os from the cd and do the install in a nice graphical mode, you install from a commandline system.

If you don't want to have to bother with loading the live cd and all that just to install your system, or if your system can't handle that, you can just use the basic, no-frills installer: the alternate cd.

---

### Post by jimv on 2008-04-30
Just an FYI, if you don't intend on running your machine with more then 4 gigs of ram, there is no benefit to running a 64 bit OS.  You're better off with the 32 bit in terms of compatibility.

---

### Post by Arch Parsons on 2008-04-30
Thanks for the replies.  Sorry, I realize now that it was Ubuntu 7.2 that I upgraded from. I didn't realize all the different versions of 8.04 installs.  I already have an alternate cd which I downloaded by utorrent 1.7.7 on bit torrent using Windows and burned the cd using Nero.   I inserted the disk and clicked on upgrade, but after so long it came back and said that no further upgrades were needed. I still have no idea which particular alternate it is that I have. I have 3 gb of RAM and can see around 2.5 on 32-bit Windows. 

I have a worse problem now.  I tried to install an add-on last night called AWN from this page:  [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)
I followed the first method which they call the esay method. Later I noticed the various tips and followed tip 3 to remove the Gnome panel.  When I rebooted the menu bar along the top was missing and if I right-clicked on the background there is no option to bring it back.  So, with the little or no knowledge that I have, I can't even figure out how to access the terminal now.  I would appreciate any help on this one.

---

### Post by aysiu on 2008-04-30
> **Arch Parsons said:**
> Thanks for the replies.  Sorry, I realize now that it was Ubuntu 7.2 that I upgraded from. There is no Ubuntu 7.2.

The releases go by year and then month of release. So there's a Ubuntu 7.04 (April 2007) and Ubuntu 7.10 (October 2007), but there is no Ubuntu 7.2

> I didn't realize all the different versions of 8.04 installs. That's not specific to 8.04. All the currently supported releases have several different CDs available for download. 32-bit Desktop CD is the most popular, though. > I already have an alternate cd which I downloaded by utorrent 1.7.7 on bit torrent using Windows and burned the cd using Nero.   I inserted the disk and clicked on upgrade, but after so long it came back and said that no further upgrades were needed. I still have no idea which particular alternate it is that I have. Usually, the name of the .iso will give you an indication of what version Alternate CD it is.

Right now, if you paste ```
cat /etc/lsb-release
``` in the terminal, the output should tell you what version you're running.

As for your problem with the missing panel, try right-clicking the bottom panel and selecting **Add Panel**. If you have no bottom panel either, try pressing Alt-F2 and typing ```
gnome-panel
```

---

### Post by mivo on 2008-04-30
> **jimv said:**
> Just an FYI, if you don't intend on running your machine with more then 4 gigs of ram, there is no benefit to running a 64 bit OS.  You're better off with the 32 bit in terms of compatibility.

Well, 64-bit does have more advantages than just the RAM (see [here]("http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1")), but for someone who doesn't do heavy video encoding, mass compiling, audio work, etc, I tend to agree that 32-bit is the smoothest choice. I ran 7.04 and 7.10 in 64-bit, but went with 32-bit for 8.04 since the old workaround for Sun Java webstart and browser plugin did not longer work for me (works for several others, though). I don't notice any speed differences personally, so I'll stick with the 32-bit version during this release. Perhaps by the time 8.10 comes out the Java situation has improved (it's not Ubuntu's fault).

---

### Post by phoenix_abhi on 2008-04-30
For the top panel If the terminal thing is not working, go to usr in file system and bin. search for gnome-panel. If u find it double click. If it is not there use synaptic package manager to install/reinstall gnome desktop and related plug ins. This may take u out from the trouble

---

### Post by bodhi.zazen on 2008-04-30
i86_64 :  Advantages / Disadvantages : 

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

Also, FYI, the alternate CD is essentially the "old" Debian style installer, text based (it is graphical, not command line) and it gives additional options not available on the Desktop CD such as a minimal, command line only installation, LVM, and encryption.

Install form alternate CD:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Arch Parsons on 2008-04-30
Thanks so much, phoenix_abhi!  Once I managed to find usr/bin/gnome-panel and opened it, that did it. Now I'm back to at least appearing that I have a full upgrade. I'm impressed!  

Now, there is still the issue of a long display of files needed for booting that gets displayed at every reboot.  I'm not sure if that's going to keep happending or not.  The one line that said Fail following it is something like this:
ntfs-3g: Failed to access volume '/dev/disk/by=vvid/string... file or directory 
Please type /sbin/mount/.ntfs --help for details. I know some of the letters are wrong because the only way I could think of capturing it was with a digital camera pointed at the CRT screen. What does all that mean?? 
As far as the release that I upgraded, of course, I meant 7.1.  Here is all I see now:

arch@arch-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
arch@arch-desktop:~$

---

### Post by phoenix_abhi on 2008-05-01
> **Arch Parsons said:**
> Thanks so much, phoenix_abhi!  Once I managed to find usr/bin/gnome-panel and opened it, that did it. Now I'm back to at least appearing that I have a full upgrade. I'm impressed!  

Now, there is still the issue of a long display of files needed for booting that gets displayed at every reboot.  I'm not sure if that's going to keep happending or not.  The one line that said Fail following it is something like this:
ntfs-3g: Failed to access volume '/dev/disk/by=vvid/string... file or directory 
Please type /sbin/mount/.ntfs --help for details. I know some of the letters are wrong because the only way I could think of capturing it was with a digital camera pointed at the CRT screen. What does all that mean?? 
As far as the release that I upgraded, of course, I meant 7.1.  Here is all I see now:

arch@arch-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
arch@arch-desktop:~$

Sorry Arch. The time zone is different. I will give u the reply shortly.
Tell me ur installed ubuntu on NTFS format or ext 3. Is the installation a dual boot or only Ubuntu. However ur using hardy heron is confirmed.

Why u people are fighting instead of guiding the newbies ?:confused:
 U all are Ubuntu users and matured people. :lolflag:

---

### Post by Arch Parsons on 2008-05-01
Thanks phoenix_abhi for the reply.  The partition is Ext3.  I have multiple Windows operating systems including XP/Vista/Ubuntu which are installed in the correct sequence and boot propertly.  The others were installed on separate drives and can only be accessed through BIOS.  I wish I had known what I was doing or where I was going before I started the multiboot system. Getting back to 8.04, I'm thinking now that it would be nice to get rid of those text lines that scroll down the creen indicating files being loaded. I only experienced and/or noticed that after increasing the size of my root partition. I did that after the upgrade. It never used to happen with 7.1  I tried that /sbin/mount/.ntfs --help thing but it didn't work.  Thanaks Mivo for the interesting information on 64-bit compatibility issues.  I wasn't aware of that. I'm glad now that I stuck with the autoupgrade.

---

### Post by phoenix_abhi on 2008-05-03
Hello Arch,

I hope the link will help u U can find a lot of ntfs-3g related stuff . Go through thoroughly. Glad to here from u any joy

[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

---

