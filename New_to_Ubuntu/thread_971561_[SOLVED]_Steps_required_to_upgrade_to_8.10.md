---
title: "[SOLVED] Steps required to upgrade to 8.10"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by stevebond001 on 2008-11-05
Hi
I am currently running Hardy (8.04) and have my PC set up just the way I want (all applications running just fine).  I would like to upgrade to Ubuntu 8.10 but I want to do this in a way that if it goes horribly wrong, I can revert to my original setup.  I have partitioned my disk under Hardy as per the attached.  As you can see, I have my Home folder located on a separate partition to my root folder.  Having read other posts, this approach seems to be the best to allow upgrading without affecting my existing data.
What I'm looking for is the best way to upgrade to 8.10, to allow for rollback to Hardy if things go wrong.  I was thinking of the following approach but need some guidance / assistance:

1.  Backup the root partition and save it to the partition housing my Home folder (what command / program is best for creating this backup / image?)
2.  Run "update-manager -d" from a terminal to perform an upgrade of the O/S.
3.  If things go right then great - however if things go wrong then I need to restore the backup / image created in step #1 (again, what command / program would be the best?).

Any assistance would be gratefully received.

Many thanks in advance.

---

### Post by Elfy on 2008-11-05
First I would say is there a pressing need tp update to Intrepid - if there is then fine and if it's because you just want to - that's exactly why I did.

There are many different ways to backup - there are some gui methods kicking about, but this is the community wiki page - [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) 

You can't roll back to hardy - you'll need to reinstall.

Personally I'd prefer to use the alternate cd to upgrade with rather than do it with update manager. That said I don't upgrade but do a clean install.

---

### Post by MrWES on 2008-11-05
Since you have /home on a separate partition; I'd do a fresh install of Ibex vs. the upgrade route. IMHO it's worth a little extra time to reinstall your apps versus the headaches that sometimes come with an upgrade.

Bill

---

### Post by stevebond001 on 2008-11-05
forestpixie & MrWES
Thanks very much for the prompt replies - much appreciated.

The reason that I am keen to upgrade is that I have customised my build quite a bit (boot splash screens, logon managers, themes, Compiz settings, screenlets, etc) as well as installing all the applications I need (and removing the ones I don't need).  Although in theory I would be able to repeat this, it would take quite a while to achieve - that's why I'd rather upgrade. 

I have just used QuickStart (what a great piece of software that is) to create a TAR backup of my root directory and stored it on my /home partition.  If you're interested it's at [http://quickstart.phpbb.net](http://quickstart.phpbb.net)  

I'm going to take forestpixie's advice and download the alternate CD to upgrade (thanks for the tip there).  However, if it does all go horribly wrong, do I just restore the TAR backup taken earlier and everything should be back to normal, or have I missed something out? 

Thanks very much for the help - it's really appreciated

---

### Post by Elfy on 2008-11-05
> do I just restore the TAR backupThat should be the case - I will just mention here that a lot of your configs are actually stored in /home so you'll have them anyway :)

I have to say that while I pointed you at that page I've not used the information myself - I'm very good at telling people to backup and negelcting to do so myself.

---

### Post by stevebond001 on 2008-11-05
lol - don't worry, I'm grateful for the advice in the first place.  I'm just checking in case I'm doing anything stupid.

I'm downloading the alternate CD now - I'll report back when I've attempted the upgrade (that's assuming that I'm able to, of course - you never know, my PC may be totally broke and I have to rebuild from scratch anyway).

Thanks once again.

---

### Post by Elfy on 2008-11-05
Make sure that you check the md5sum and the burn before you start ;)

L:inks just in case

[http://releases.ubuntu.com/8.10/MD5SUMS](http://releases.ubuntu.com/8.10/MD5SUMS)
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM) on Linux
[https://help.ubuntu.com/community/BurningIsoHowto#MD5](https://help.ubuntu.com/community/BurningIsoHowto#MD5) Sums
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by stevebond001 on 2008-11-05
WooHoo.....
Guess what - it worked perfectly.  I'm now running Intrepid after a seamless upgrade.  The only issue (if you can call it that) is that the upgrade removed my Openoffice 3.0 installation and replaced it with 2.4 (which comes as part of the distro).  However, I have followed some instructions (detailed below) to fix this.

For anyone who wants to try this, here are the steps I followed:
1.  Downloaded the Alternate CD .iso image from the Ubuntu Website.
2.  Rather than burn a CD with the image (which you can do if you prefer) I mounted it with the following command
***sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0***

3.  after it was mounted, I ran the following command to start the upgrade
***gksu "sh /cdrom/cdromupgrade"***  This started the upgrade and took about 20 minutes to complete.  After the upgrade I rebooted and logged back in to my familiar desktop (screenshot attached if you're interested)

4.  I removed and replaced Openoffice as per the following thread:
***[http://ubuntuforums.org/showthread.php?t=947388](http://ubuntuforums.org/showthread.php?t=947388)*** (Post number **9**)

Everything is now working as it was before the upgrade.  I am a very happy teddy now.\\:D/

Thanks to all who helped with this, and good luck to all who try this upgrade method (but make sure you have your backup, just in case..)

Cheers

---

### Post by Elfy on 2008-11-05
I _*like*_ that desktop - where'd you get the image from :D

Can you also mark the thread solved please.

---

### Post by stevebond001 on 2008-11-05
Thread Marked as solved (Hope I've done it right).

Also, desktop graphic attached FYI - not sure where I got it from.  If you're interested in different desktops, etc, take a look at [http://art.gnome.org/](http://art.gnome.org/) - there's loads of good stuff there

Thanks once again.

---

### Post by Elfy on 2008-11-05
thanks stevebond001 - have that now :)

Less on my desktop than your's though

---

