---
title: "Howto: NoNetDebs - upgrade Ubuntu without Internet (or with low-bandwidth connection)"
date: 2007-10-10
forum: Outdated Tutorials &amp; Tips
---

### Post by ruibernardo on 2007-10-10
[COLOR="Red"]Mod Edit: No longer active
Alternative: [http://keryxproject.org/](http://keryxproject.org/) [http://www.webupd8.org/search/label/keryx?max-results=10](http://www.webupd8.org/search/label/keryx?max-results=10)[/COLOR]

Hi,

NEW: major changes. New host and new features - see [post #49]("http://ubuntuforums.org/showpost.php?p=4908090&postcount=49").

For those accessing the Internet from a library, school, college, workplace, from windows, etc.

Just upload the status file from the offline Ubuntu (the complete pathname is **/var/lib/dpkg/status**) to your user account, select the ubuntu release, check if you want to upgrade or not, add a list of packages you want to install, click "List packages", **[COLOR=Red]wait[/COLOR] a minute** and you will get a list of the packages you need and you still don't have installed on your ubuntu offline, just like if you had done "sudo apt-get install".


[B][http://nonetdebs.homeip.net](http://nonetdebs.homeip.net)

or [http://nonetdebs.unixpod.com](http://nonetdebs.unixpod.com)
[/B] 
** To see how it works check [post #11]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11").**
**VERY IMPORTANT: To install**** [COLOR=Red]ubuntu-restricted-extras[/COLOR] offline in Gutsy check [this post]("http://ubuntuforums.org/showpost.php?p=4519538&postcount=4"). **If you don't do it like posted on that link, you'll get broken packages and a broken system!


================================================
The following is here just for historic curiosity and concept. 
Please read post #11 and #49 for about nonetdebs website.
================================================

last few days I've been messing around with this BASH script I've made - nonetdebs. It's fresh (not wide testing done yet, just here) and I need some feedback about if it is useful and if it really works. 

nonetdebs can download or list the packages you need to download for your Ubuntu at home with no Internet connection.

[IMG]http://ubuntu.no.sapo.pt/nonetdebs/nonetdebs.png[/IMG]

It is somehow related/based in this [http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/](http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/) and this [http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/) but done the automatic and easiest way (with a nurcses GUI), plus the independence of which Linux/Ubuntu version you are running (nonetdebs creates a chroot, so nothing is installed on the connected system, the packages are just downloaded) and plus avoids downloading already installed packages (the file you bring from the other computer tells what packages are already installed there). 

nonetdebs can be an alternative to APTonCD and/or APT-move: 
- APTonCD and APT-move need an equivalent version of Ubuntu on both computers, nonetdebs don't; 
- Creating DVD mirrors of the repositories is a big download and needs frequent updates, nonetdebs just downloads upgrades and new packages you want, knowing the packages you already have. It is a more individualized option. 

[SIZE=4]
What you need:[/SIZE] 

1. The status file from your Ubuntu box. You can email if to yourself (~2 MB, maybe 5 MB, 10 MB max, it is located at /var/lib/dpkg/status), or copy it to a CD-RW or USB memory stick/pen.

2. A computer that have Internet connection.[INDENT]Option 1: A computer, as long as you can boot it with a LiveCD (Ubuntu Desktop?) and have an Internet connection with it. For real Windows, maybe you can use Wubi to install Ubuntu in it and use this script, or use cygwin --- all untested options except for the LiveCD (testers needed). A writeable partition  from the LiveCD: ext3, something writeable. Many possible untested options here... (except FAT32, debootstrap *apparently* doesn't like it)
[/INDENT][INDENT]     Option 2: Any Linux box with Internet, as long as you can install debootstrap and dialog and you know its root password (k/x/ubuntu, fedora, whatever). BASH and wget are also needed, but are generally available in almost all Linux distros.
[/INDENT][SIZE=4]How it works:[/SIZE]
 * on the following text, "the other computer" is the Ubuntu without Internet.

**The complicated way:**[INDENT]1. You copy the file /var/lib/dpkg/status from the other computer to a USB pen/stick or to a CD.

2. You take a LiveCD and a USB pen to the computer with internet and boot it.

3. You install "dialog" and "debootstrap" packages on the LiveCD, then you [download]("http://ubuntu.no.sapo.pt/nonetdebs/nonetdebs") and run nonetdebs script on a terminal.
  
4. You setup nonetdebs (mirrors for downloading, locale, Ubuntu version, status file).

5. You select upgrades, select new packages and make the downloads to the USB memory.

5. You go home.

6. You plug the USB pen on the other computer, open a terminal, type 

```
cd /media/disk
./nonetrepo

sudo apt-get update
sudo apt-get --allow-unauthenticated upgrade
sudo apt-get --allow-unauthenticated install packages_names
```[/INDENT]**The simple way:**[INDENT]1. You have a copy of your status file from the other computer (email attachment, or on CD or USB);

2. You download the packages "dialog" and "debootstrap" and run the nonetdebs script (download it [from here]("http://ubuntu.no.sapo.pt/nonetdebs/nonetdebs") and make it executable);

3. nonetdebs downloads, setups and creates a chroot with debootstrap of the Ubuntu version of the other computer on the connected computer (on USB or disk - ext3/something_writeable and with the needed space available - 200 MB minimum ). 

This will make a download of a minimal Ubuntu of the Ubuntu version you have choose (50 MB of download, 200 MB max of disk or USB space). This is a one time download. The next time you use nonetdebs, you can select this chroot again, no more chroot downloading needed. You can even create a backup of that chroot from the script;

4. You copy the status file (from the other computer) to the chroot (done from the script). With the status file, the chroot will «know» what packages you have at home and will know which one to upgrade and/or install -- less downloads needed, more accurate upgrades;

5. You select to upgrade and/or install any new packages you want from the repositories. The script will only select the packages you don't have on the other computer, and will select all dependencies except the ones you already have installed (less download volume);

6. once nonetdebs has created a list of the files you need to download (this list will be inside the chroot if, for some reason, you can't download and save the packages with the LiveCD, or if you have a low-bandwith at home and can't/don't_want_to make the downloads there and only have Internet access from a Windows box, etc). The list is the internet address of the packages needed on the repositories (check post [#2]("http://ubuntuforums.org/showpost.php?p=3518443&postcount=2") to download it from Windows).

7. You download the packages nonetdebs will create a script when you download the packages - nonetrepo - and puts it in the same directory where you saved your packages. This script  - nonetrepo - is to add the new repository without too much trouble (easier).

 8. OPTIONAL: you can create an ISO file and burn it from Windows ((reboot needed here - look at post [#2]("http://ubuntuforums.org/showpost.php?p=3518443&postcount=2")). 

9. You go home (where the other computer is) and run
```
./nonetrepo
```from the directory where the packages are, to had the new repository. You can do this directly on the USB memory stick/pen or copy the files from a CD to the hardisk and run the script from there (a writable directory/partition is needed here for dpkg-scanpackages work, although some tweaking might work to avoid copying the files to disk).

10. You're done. Update APT (Synaptic or apt-get) and install the new packages. Use 
```
sudo apt-get --allow-unauthenticated upgrade
``````
sudo apt-get --allow-unauthenticated install name_of_the_packages
```to install them. Update-manager will not work, because the files aren't signed.
[/INDENT][SIZE=4]More Info[/SIZE]
I've tested it upgrading a Ubuntu 7.10 Gutsy Tribe-5 to its latest updates (more than 400 packages upgraded) with a LiveCD and a USB memory pen, then I connected it to internet, add the regular repositories, and no more needed updates were found. :popcorn:

Note to aptitude users: although it is possible to make apt-get download "recommended packages" (to be used with aptitude on the other computer) it doesn't work with Dapper, so I've not enabled this option, but it can be done with Feisty/Gutsy (Edgy not tested) just with some tweaking (with apt.conf on the chroot directory and APT options).

If you try to write to non-writeable partitions, the script will tell you that you can't.

TODO: nonetrepo - check on the other computer if the new repository already exists on source.list (duplicates).
WISHLIST: nonetdebs - gtk frontend (zenity).

The nonetdebs script can be found here: [http://ubuntu.no.sapo.pt/nonetdebs/nonetdebs](http://ubuntu.no.sapo.pt/nonetdebs/nonetdebs)
("dialog" and "debootstrap" also packages required).

---

### Post by ruibernardo on 2007-10-11
Thank god nobody found this thread here :lol:.

I say that for 2 reasons:

- The script I released yesterday (0.124) had some syntax errors (wasn't working);
- I was claiming that you could run it with a FAT32 partition, my bad.

Forgive me about the syntax errors, I've tested the script before I've made some changes, and found that it wasn't working. :redface: But it's all right now. :-({|=

About FAT32, I should know that FAT32 wouldn't work with debootstrap. I was testing here the "worst case scenario" (saving the chroot to a FAT32 partition) and found that debootstrap changes the owner of some files and FAT32 *apparently* doesn't support that (FAT32 is a 1 owner filesystem, sorry about that :oops:). At the moment I even can't assure anybody that a debootstrap in NTFS would work either (can somebody confirm this, please?).

So, if you need to upgrade you system and only have access to a computer with a M$ filesystem (FAT32 or NTFS) **and** you don't have a USB memory pen, I advise you to do the following:

- Run the script and create the chroot in $HOME.

- Save the list of files to [http://rafb.net/paste/](http://rafb.net/paste/) or any similar website. The list of files you selected is located in /var/*.txt inside the directory you choose to create the chroot with debootstrap (for example:  $HOME/nonetdebs/var/list_upgrades.txt). You can use Firefox from the LiveCD to do that. ;-) 

- Then use any Windows software you like to download these files (it is a list of addresses of the packages in the repositories, like this: [http://archive.ubuntu.com/ubuntu/pool/main/libs/libservlet2.4-java/libservlet2.4-java_5.0.30-6ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libservlet2.4-java/libservlet2.4-java_5.0.30-6ubuntu1_all.deb)).

Of course, if you have a USB memory pen/stick, and you formated it with a ext3 filesystem, you will not have any problem and you can download the packages directly into it and install these packages directly from it on the other computer. :guitar:

This time it's for real, it is working. \\:D/

Please, any feedback is welcome.

---

### Post by urukrama on 2007-10-12
This could be exactly what I'm looking for. I have a computer that isn't always connected to the internet, and installing something on it can be such a drag. Thank you! I'll give it a try next time I want to install something.

---

### Post by ruibernardo on 2007-10-12
I hope it works for you urukrama. Any question or problem, please feel free to ask :)

I've added a little improvement. Until now the script would copy all the packages that debootstrap used to create the chroot to the download directory (~170 of them) when the user wanted to update/upgrade the other computer. I've corrected that. 

Now the script only copies the packages that it finds on the "already downloaded packages" and are not on the download directory and are listed on the list_upgrades.txt file. 

This saves some space used to move around the packages (CD or USB) and I think it will avoid any APT/dpkg problems on the other computer (and with nonetrepo) because of unneeded and/or duplicated packages on the other computer.

Also corrected the creation of download directory. It was being created, but the script was saying that the directory already existed.

---

### Post by blithen on 2007-10-12
I haven't tried it yet, but this is defiantly a great idea. Looks very offical. Great job!

---

### Post by ruibernardo on 2007-10-22
Hi again,

since the Canonical repository for Gutsy is named "gutsy partner" instead of (for example) "feisty commercial main" on the other releases, I've updated the script to reflect that change. 

I've tried to «install» opera in Gutsy and the files were listed ok, so the script works fine with Canonical repos and Gutsy.

---

### Post by dhruva023 on 2007-10-22
thanks, i will be trying it

---

### Post by ruibernardo on 2007-10-23
Some corrections today. 

Apparently I wasn't using a completely "new" gutsy install during my testings. When I tested the script again on a fresh «target», it didn't had the package dpkg-dev installed (dpkg-scanpackages, used by nonetrepo), so I made the script download it and install it (including any dependencies) if it isn't present on the target.

** tested in a fresh install of alternate desktop cd of gutsy - after upgrading the target (9 packages) with nonetdebs/nonetrepo, I've connected it to the internet and no more upgrades were needed **

---

### Post by ruibernardo on 2007-10-30
For those who can't boot a LiveCD on the workplace, library, cybercafe, etc, I've adapted the script to work from a website.

Just register, set your profile, upload the status file, click "List packages" and wait a minute for the list of the packages you need to download. 

For now it's just for i386 (dapper/edgy/feisty/gutsy), no medibuntu nor canonical repos.

[http://nonetdebs.homeip.net](http://nonetdebs.homeip.net)

---

### Post by Sef on 2007-11-07
Seems more appropriate here than Community Cafe.

---

### Post by ruibernardo on 2007-11-10
Thanks Sef, I appreciate that.

I've noticed that some people had a hard time with the registration and to get the list of packages they need or want.

Here's a way of getting it done (using a USB memory):[INDENT][SIZE=3][COLOR=black]**A.**[/COLOR][/SIZE] On the offline computer, copy the status file to the USB memory. /media/disk usually is where USB memories get mounted on the system (verify if it was your case). To do it, type on a terminal:
```
sudo cp /var/lib/dpkg/status /media/disk/status.txt
```The .txt extension is needed to upload the file later. 

If it is a removable media (like USB in this case) eject it before you unplug it, so no data is lost:
```
sudo eject /media/disk
```Or right-click in the media in Nautilus and click "Unmount".

[COLOR=Red]** [SIZE=3][COLOR=black]B.[/COLOR][/SIZE]**[/COLOR] Go to the online computer, open the browser, go to [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net) and create an account (click the "Create new account" link). You will need an email account to receive the password and link to activate the account.

You will receive a mail from nonetdebs AT nonetdebs.homeip.net with a link to activate your account. Just click the link to activate the account and press the "Log in" button.

[SIZE=3][COLOR=black]** C.**[/COLOR][/SIZE] Modify your password to one that you can remember later and  click "Submit" in the end of the page. 

You will be redirected to "My account" page. Now follow this steps to set up your account and to download your first packages (the next time you will only need to upload the new status file and change the name of the packages you want to download):

[IMG]http://ubuntu.no.sapo.pt/nonetdebs/image-2.png[/IMG]

**[COLOR=Red]1[/COLOR]**. Click the link "**Create your Status file from target**" to upload the file to the website.

[IMG]http://ubuntu.no.sapo.pt/nonetdebs/image-3.png[/IMG]

**[COLOR=Red]2[/COLOR]**. Click the button "**Search**" and select the file;
**[COLOR=Red]3[/COLOR]**. The file must have a **.txt** extension;
**[COLOR=Red]4[/COLOR]**. Click "**Upload**";
**[COLOR=Red]5[/COLOR]**. Click "**Submit**".

[IMG]http://ubuntu.no.sapo.pt/nonetdebs/image-4.png[/IMG]

**[COLOR=Red]6[/COLOR]**. After you submitted the status file, click "**Edit**" to edit the settings of the target.
**[COLOR=Red]7[/COLOR]**. Now click "**Repositories**" on the top of the page.

[IMG]http://ubuntu.no.sapo.pt/nonetdebs/image-6.png[/IMG]

**[COLOR=Red]8[/COLOR]**. Select the repositories you want. To have all the packages available from the Ubuntu repositories, enable **Main**, **Universe**, **Restricted** and **Multiverse**. To install libdvdcss2 (to play DVD's) and w32codecs (to play some video files) you will need to enable the **Medibuntu** repository too.
**[COLOR=Red]9[/COLOR]**. Click "**Submit**" to save your changes.
**[COLOR=Red]10[/COLOR]**. Click "**Target**" on the top of the page.

[IMG]http://ubuntu.no.sapo.pt/nonetdebs/image-8.png[/IMG]

**[COLOR=Red]11[/COLOR]**. Select the Ubuntu **release** of the offline computer (Dapper, Edgy, Feisty, Gutsy);
**[COLOR=Red]12[/COLOR]**. Select the **architecture** (i386, amd64, PPC or sparc);
**[COLOR=Red]13[/COLOR]**. Select your **locale** (language). Select the UTF-8 ones in case of doubt.
**[COLOR=Red]14[/COLOR]**. Click "**Submit**" to save your changes.

[IMG]http://ubuntu.no.sapo.pt/nonetdebs/image-9.png[/IMG]
**[COLOR=Red]15[/COLOR]**. Click "**Install**".
**[COLOR=Red]16[/COLOR]**. Type the name of the package you want to install on target.
**[COLOR=Red]17[/COLOR]**. Click "**Submit**" to save your changes.
**[COLOR=Red]18[/COLOR]**. Click "**New Packages**" on the left of the page and wait about 1 minute or so to get the list of packages you need to download.

[B][IMG]http://ubuntu.no.sapo.pt/nonetdebs/image-11.png[/IMG]
[/B]
**[COLOR=Red]19[/COLOR]**. Click on the links and download the package you want and all its dependencies you still don't have installed on the target and a little script to install all the packages.
[SIZE=3][COLOR=black][B]
D.[/B][/COLOR][/SIZE] Save all the package files to the USB memory. Copy the scripts to a text editor and save them to the USB memory too. [COLOR=Red]If you used Windows to save the scripts[/COLOR], please take a look at this thread: [http://ubuntuforums.org/showthread.php?t=613778](http://ubuntuforums.org/showthread.php?t=613778). It's about end-of-line characters that are different in Windows and how to make the script executable if you used a Windows text editor to save the scripts.

You're done in the connected computer.

[SIZE=3][COLOR=black]**E.**[/COLOR][/SIZE] Go to the offline computer, plug the USB memory (or the media you used), and open a terminal. Go to the directory where the USB memory is mounted:
```
cd /media/disk
```and run the script file you saved. If you have named it like "updates", run:
```
sudo bash updates
```The script will run the "dpkg -i" commands to install the new packages. Don't panic if you see any dependencies problems while the script is executed. An "apt-get install -f" is executed in the end of the script. It will resolve all the dependencies and finish installing the packages that were left behind.

[/INDENT]**[COLOR=Black]The next time you want to update/upgrade/install packages, you have to copy the actual status file from the offline computer to a USB memory and upload it to the website again.[/COLOR]** The status file changes when you install new packages, so you need the most recent one or else you will be downloading files you already have installed.

Enjoy Ubuntu! :popcorn:

---

### Post by ruibernardo on 2007-11-16
Canonical commercial/partner and medibuntu repositories added to the website.

Please beware that some packages do further downloads when you install them. For example, if you install the package msttcorefonts (microsoft fonts), upon the install several downloads will be made, and as your target doesn't have an Internet connection, it will not be able to do it, and thus leaving the package broken (not completely installed).

Do not try to install packages on the target that make further downloads.

---

### Post by ruibernardo on 2007-11-26
Another repository added: WineHQ for the latest versions of wine.

---

### Post by ruibernardo on 2007-11-30
Now the website supports all computer architectures available on the repositories. 

Until now only i386 was used, now the user can select the following architectures: i386, amd64 (all 64 bits PCs), powerpc (PowerPC and Apples), and sparc systems (Sun).

---

### Post by fulllefty on 2007-12-04
> **epimeteo said:**
> Canonical commercial/partner and medibuntu repositories added to the website.

Please beware that some packages do further downloads when you install them. For example, if you install the package msttcorefonts (microsoft fonts), upon the install several downloads will be made, and as your target doesn't have an Internet connection, it will not be able to do it, and thus leaving the package broken (not completely installed).

Do not try to install packages on the target that make further downloads.

If that so, what should I do if I want install msttcorefonts? Is there another way to do that (without internet connection)?

How could I know if the package will make further download? Is there any signing /something?

---

### Post by durand on 2007-12-04
Thats a very neat solution!

---

### Post by ruibernardo on 2007-12-04
> **durand said:**
> Thats a very neat solution!Thank you durand.

> **fulllefty said:**
> If that so, what should I do if I want install msttcorefonts? Is there another way to do that (without internet connection)?I've found a thread in this forum to do that: [msttcorefonts on standalone machine]("http://ubuntuforums.org/showthread.php?t=203994").
> **fulllefty said:**
>  How could I know if the package will make further download? Is there any signing /something?
Unfortunatly I don't think there is any signature or something to know that. I know that the sun-java* (JRE and SDK) packages and msttcorefonts do it. The package ubuntu-restricted-extras downloads Sun Java, so it will do it too.

I'm trying to track down more [packages that do further downloads]("http://ubuntuforums.org/showthread.php?t=630696") to warn users about it on the website. 

If you find more packages, please say.

---

### Post by fulllefty on 2007-12-09
Thank you for making such a cool site like nonetdebs. It's help us a lot :)

---

### Post by ruibernardo on 2007-12-10
Thanks fulllefly.

Don't forget, if you find any package that tries to make any download, post it in that thread or here. ;)

---

### Post by mathutu on 2007-12-14
thanks for that useful tool (website).

I would like to ask if it is possible to add repositories by hand? for example is there any way to add "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main" to your list of repositories. It can be useful, for example to try testing kde 4 rc 2.

Best wishes.

---

### Post by ruibernardo on 2007-12-20
> **mathutu said:**
> thanks for that useful tool (website).

I would like to ask if it is possible to add repositories by hand? for example is there any way to add "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main" to your list of repositories. It can be useful, for example to try testing kde 4 rc 2.

Best wishes.

I see. That would be a nice feature. 

After tracking those "more downloads" packages and making the user interface more easy to use I'll try to add this feature and maybe enable the user to completely edit the sources.list file to use. The only problem would be to add the gpg keys of those repositories in the chroot, if the repository have one. 

Thanks you for the idea, mathutu.

---

### Post by astadolfo3 on 2007-12-23
Is there a simple package to download and install to complete the upgrade? 

at the bottom of the the upgrade page: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

it states: "Download and burn the alternate installation CD."

what installation CD? This is not the bootable CD since it does not have the directory /cdrom/cdromupgrade indicated in the instructions.

where is this upgrade installation CD? Why not put a link in the upgrade page? Why not make it simple?

BTW, I tried the online upgrade since I do have a good internet connection, but it keeps failing.

---

### Post by ruibernardo on 2007-12-24
Hi astadolfo3,

sorry for the late reply. Can you post what was the error you got?

Another thing: upgrading from a cd is not the same as running "sudo apt-get upgrade" <- this is what "Upgrade" is on the website (man apt-get).

For a real dist-upgrade (moving from feity to gutsy), use the bash script from the first post, use aptoncd to make all the packages available to the update-manager. For the record: I never enable this (dist-upgrade) in the website.

---

### Post by gary4gar on 2008-01-08
suggestion, can you upload a default gutsy install status file on site, will be helpfully for new users :)

default means, no other packages are installed except the one installed by the ubiquity

---

### Post by thenailedone on 2008-01-09
Wow... I think my prayers have been answered!

I will give this a go ASAP and report back (but I can't for see any problems :) )

edit: Well I have now used nonetdebs... and I have to say that it was slightly puzzling at first but I got the hang of it eventually...

I was expecting a more automated download but it still much easier and convenient than trying to make sure you got the package you wanted and all of the dependencies (without downloading packages you already have...)

I would seriously give nonetdebs a 8/10 score and will continue to use... but I am sure it can be even better (much better)...

---

### Post by clockb0x on 2008-01-22
I'm in an interesting situation where my target Ubuntu system has no internet access, but my machine with internet access can only run Windows.  The IT folks have things locked down such that I cannot boot a live CD.  Our internet filtering also blocks the website version of NoNetDebs.

I am able to SSH into an offsite linux machine and was able to get the list of packages.  I then downloaded those packages using my Windows system and transferred them to the Ubuntu machine.  I tried installing them by using ```
sudo dpkg -i *.deb
```Then I issued ```
sudo apt-get install -f
```which proceeded to remove a ton of stuff and left my machine in an inoperable state.  This is not a big deal since it was a clean install and I can just do it again.  My question is, where did I go wrong?  My guess is that apt-get doesn't know what it's doing since I can't do an ```
apt-get update
```

---

### Post by jenkinbr on 2008-02-25
Just to warn everybody, I have had issues in the past with the shell script generated by the website version of nonetdebs.  Specifically, the script is often generated in a way that some of the lines are generated as 
```

dpkg -i ./
dpkg -i ./
dpkg -i ./
dpkg -i ./

```
Fixing it is a simple matter of locating the links and coping the file name after the ./ .  However, this can cause problems if you don't notice in time to fix it.

Yes, I know (and do) use apt-on-cd, but I still think this should be noted.

@ clockb0x
 I know this is a really late reply, but could changing your command from
```
dpkg -i *.deb
```
to
```
dpkg -i ./*.deb
```
solve your problem?

---

### Post by ruibernardo on 2008-03-04
Hi everyone and thanks for finding NoNetDebs in some way useful.

I've been "offline" because of some problems took my time in the last couple of months. Now I hope I can develop a little more this website (no fancy things, just to get it working good and make it more useful).

@gary4gar - "can you upload a default gutsy install status file on site, will be helpfully for new users". I could, but IMHO it would bring more complications than would help. There is Dapper 6.06, Dapper 6.06.1, Dapper 6.06.2, Edgy, Feisty, Gutsy and now Hardy, each one of this releases have different architectures (i386, amd64, PPC). All this different releases/versions/architectures have a different status file. I only have a Gutsy i386 here... I would suggest users to save a clean (fresh install) status file in some copy/paste website and post a link here in this thread.

@thenailedone - Thank you for finding the website so good. No fireworks - a plain drupal5 website - but I think it's more important that it works well. I'm looking forward for suggestions.

@clockb0x - Sorry to hear that. I should remove the script from the website. I put it there to make things easy to who don't have aptoncd installed. I've saied it before, aptoncd creates and deals very well with packages - it s the best method to install packages.

Also be careful about packages that make more downloads when they are installed on the offline target (use vlc or mplayer for codecs) because some packages will be broken (they didn't download anything, so they are not completely installed, so the are broken) and removing them may force you to remove all packages that depend on "ubuntu-desktop" package - this issue only happens with propriety software, don't use them - use gnash for flash, don't install "ubuntu-restricted-extras" nor Sun Java nor mscorefonts - they can't be redistributed, so a download from their site have to be done when you install the package. 

@jenkinbr - I recently found that problem (like white empty "dpkg -i " lines. I found later that resizing the browser so the lines can be fully displayed solves that.

Thank you all for your comments and help.

---

### Post by ruibernardo on 2008-03-04
After being away from the computer for the last couple of months, I've made today some improvements:

- Additional APT line (sources.list):
> **mathutu said:**
> I would like to ask if it is possible to add repositories by hand? for example is there any way to add "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main" to your list of repositories. It can be useful, for example to try testing kde 4 rc 2.
Very very late (sorry), but now it's done. On the repositories tab of the accounts settings there is a text line. You can add the APT line there, it will be pasted on sources.list (no gpg key, so apt-get will report missing key if the repository have one).

- Hardy repositories added.

- Backports repositories for all Ubuntu releases (to be used only if you know what you are doing).

I hope this changes don't break anything. Please report potential problems here in this thread or in the website.

---

### Post by ruibernardo on 2008-03-15
Hi people, to get "ubuntu-restricted-extras" installed offline without getting broken packages: [http://ubuntuforums.org/showpost.php?p=4519538&postcount=4](http://ubuntuforums.org/showpost.php?p=4519538&postcount=4)

---

### Post by alfayate on 2008-03-24
Hi

Thank you for the nonetdebs script, I was looking for something like that... but unfortunately it doesn't work for me.

It doesn't matter what directory I choose to chroot, it always says it's not a suitable directory...

when I try to do it in the command line:

chroot /directory

I've got the reply:
cannot run command `/bin/bash': No such file or directory

I'm using the version 0.128 of the script
I have a Debian Etch stable

I think It's a problem with the chroot command, but I've been looking for a while in some forums and I've got nothing useful. Any ideas?

Thank you very much for your help

---

### Post by ruibernardo on 2008-03-24
Hi,

I was going to say that you can't run the script in a not-updated system. This because in a not updated system, let's say a 6.10 Edgy one, the files for the deboostrap to create next-coming releases aren't there, i.e. a debootstrap for Gutsy in Edgy can't be executed because the "gutsy" file in /usr/share/debootstrap/scripts/ that says to debootstrap how to build a Gutsy minimal system doesn't exist. An updated package (from ubuntu backports repo) will solve this.

In your case it's because you don't have those scripts. Etch only have debootstrap script files for Warty, Hoary and Breezy and for the Debian releases. Debian Sid/unstable version of deboopstrap has scripts for Ubuntu releases 'till Gutsy (hardy isn't out yet). Install the sid version or add/copy the scripts you don't have to the /usr/share/debootstrap/scripts/ in your system.

Because of that the chroot wasn't built by debootstrap, and the script found no suitable directory to work or to chroot.

---

### Post by NikS on 2008-03-29
Hi,

Thanks epimeteo!!
Thanks a lot for this GREAT facility for the ubuntu users like me, who lack net!! (quite backword we r)!!

I have a problem, n need some help with it..

I dont hv net at my home ubuntu system. I needed to install mplayer and wine, tried to do it using the .deb packages i got from net (net cafe, cant carry my pc to a wireless net cafe!!) Being a complete newbee, in Linux and formerly using windows, knew nothing about the 'dependencies'!!!
Next thing i tried was: when i double-clicked the package in ubuntu it would tell me the dependency it lacked, i would go to net, download that particular dependency, come back home, install it, try again to install the .deb package, fail, get the next dependency, would go back to net..........!!!!
Did it almost 5 or 6 times, nut it was not feasible, no way!!!

then came to know about the forum, joined, learnt about nonetdebs, got my status file, n here i am:
I uploaded my status file, selected repositories, typed in the packages, selecte my target os n all n all....

now when i select "new packages", it replies:

" For New Packages
To install the package(s) xmms wine mplayer you must download the following package file(s): 

No apt-get error nor package files listed to download. Apparently you already have this/those package(s) installed on the target (verify it in Synaptic). Update your status file if it is not the case. "


Can u help???

---

### Post by ruibernardo on 2008-03-29
Hi niks,

I've just tested your status file and had no problems at all. Can you try again?

---

### Post by rajaram_s on 2008-03-29
The website just works great and should be ultimately useful for people like me. I enabled all the repositories from which it can download, but still for many obvious packages like beryl or audacity, it says the package is already installed.

I am sure the package is not installed in my computer.

I also have uploaded the latest status.txt file. What could be the problem? I was able to get amarok and some udates tough...

---

### Post by rajaram_s on 2008-03-30
[SIZE="3"]Also, the downloaded package dint install the softwares I wanted. I had asked for amarok and it had all packages except amarok. The worst thing about it is that, the packages I got also were already installed in my computer. I am very sure that I have uploaded the latest status.txt file. Is this a problem with nonetdebs? Do they have any error reporting tool?

Also, reg adding additional custom repositories, there is an option for adding only one custom repository list. This could be updagraded to a list of custom repositories, as many 3rd party softwares require more than one custom repository rom which packages are to be downloaded....[/SIZE]

---

### Post by ruibernardo on 2008-03-30
If nonetdebs didn't list the main amarok package, that would mean it was installed on the target- at least it was listed in the status file (maybe you just downloaded it and tried to install it with "sudo dpkg -i") or you didn't select the right repositories. Or maybe you missed some links and didn't download all the files.Can you be more specific on this problem? 

I'll add more lines for repositories later. Thanks for the suggestion.

---

### Post by NikS on 2008-03-31
Thank you epimeteo for ur reply..
and your help as well..

I just checked for new packages on nonetdebs, it has asked a package to download and install..

Thank you very much!!

---

### Post by alfayate on 2008-04-12
Hi Epimeteo!

Thank you very much for your answer. I installed debootstrab from the unstable branch and everything went ok. ;)

It's always nice to find people so kind and skilled....

---

### Post by odwyerda on 2008-04-18
Excellent guide,

although when i did it I get an error

Errors encoutered while processing
bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned error code (1)


????
no idea what that means

---

### Post by ruibernardo on 2008-04-18
Hi odwyerda,

I think you've found a package that, upon installation, makes some download. If you don't have an internet connection at the time, the installation will fail and the package will be broken.

I didn't know this issue with that package, so it's another one that must be blacklisted if you want to use Ubuntu offline.

I've «googled» and found this thread:  [[SOLVED] dpkg / bcm43xx-fwcutter Error]("http://ubuntuforums.org/showthread.php?t=527109"). I hope it works for you.

---

### Post by vitesse on 2008-04-30
OMG! :)

This is what I was looking for so many time :D:D

But I wont recieve the email with the instructions to activate the account.


:(

Any ideas

---

### Post by jenkinbr on 2008-04-30
Make sure that you supply the correct email when you set up an account.  My first time, I accidentally added an extra character at the end of my address, and I could not activate the account because of this.

@epimeteo:  Possibly a "verify e-mail" box during account setup?

---

### Post by vitesse on 2008-04-30
Yeah!

I got the activation e-mail.

I followed the tutorial to upgrade ubuntu, and worked fine. 

Download debs, update target, update status back to website. but now I want to download xine, xmms, gstreamer

And this is the message that sends me:

```
Sorry, but apt-get returned the following error (edit the locale in your account to have the error message in English or in another language of your choice):

E: No se pudo encontrar el paquete gstreamer (Could not find the package gstreamer) 
```

---

### Post by jenkinbr on 2008-04-30
That would be because there are no packages by that name.

Try doing a search for "gstreamer" on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
(scroll down past the release links)

This link points to the results under hardy:
[http://packages.ubuntu.com/search?keywords=gstreamer&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=gstreamer&searchon=names&suite=hardy&section=all)

ps - I frequent [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for this reason.  I find the search feature rather helpful for finding the packages that I need.

---

### Post by vitesse on 2008-04-30
> **jenkinbr said:**
> That would be because there are no packages by that name.

Try doing a search for "gstreamer" on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
(scroll down past the release links)

This link points to the results under hardy:
[http://packages.ubuntu.com/search?keywords=gstreamer&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=gstreamer&searchon=names&suite=hardy&section=all)

ps - I frequent [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for this reason.  I find the search feature rather helpful for finding the packages that I need.

I searched for gstreamer in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and I have all the repos enabled in my account.

Based on that I think that a search for gstreamer* should give all the packets starting with gstreamer.

After that I tried to install amarok and everything whent right until I intalled the packets in the offline ubuntu and notice that some packets needed like amarok-engine were missed.

I opened the bash file copied from the site, and amarok-engine was missed too.

Need help :D
TIA

---

### Post by jenkinbr on 2008-04-30
I haven't tried doing a wildcard search using nonetdebs - let me know if that works for you.  It would save a lot of space on the "sudo apt-get " line, which only allows 255 characters.

As for missing dependencies, that remindes me - I had that happen the other day.  When I ran synaptic with my freshly created apt repo disk created using aptoncd, I tried marking the metapackage provided, but couln't because not all dependancies were satisfied.  turns out, I was missing package 'm4', so I could not install libtool, autoconf, among others.

---

### Post by vitesse on 2008-04-30
> **jenkinbr said:**
> I haven't tried doing a wildcard search using nonetdebs - let me know if that works for you.  It would save a lot of space on the "sudo apt-get " line, which only allows 255 characters.

Wildcard search works.

IMHO I think this an aspect that shoud be improved. Maybe should be some kind of check list, or show software by application like in synaptic. Tthis way you can select the name of the mayor application like xine and the query will return all debs needed for installing xine.

BTW the wildcard search return ALL debs with gstreamer* in the name. This could be reduce if you restrict the repos to search.

---

### Post by ruibernardo on 2008-05-08
Hi,

sorry for loosing this discussion, but I've been busy. Can't add much more to what it's been said, but to confirm what jenkinbr suggested: to use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search packages, although a new "apt-get update" feature is available now. It's not simple, though.

First, the news. I'm not hosting the website anymore. The website is now kindly hosted by unixpod.com at [http://nonetdebs.unixpod.com](http://nonetdebs.unixpod.com). The registration mail will come from there, obviously. You still can use [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net). DynDNS will redirect you to unixpod.com.

I've managed to finally integrate drupal, apt-get as normal user and nonetdebs code (90% redone, so please say if something is broken). Now the site is more quick and its use is more similar to the real use of apt-get.

There are several improvements, and the "apt-get update" one is the most important, as it finally breaks the isolation of the offline apt-get system. [Based in this comment]("http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/#comment-54908") I've found while browsing, I've made nonetdebs get those files for you even if you don't have the status file in your account. I think it's very useful. 

Now you can save what is downloaded by apt-get when you run "apt-get update" with the selected repositories. The offline apt-get system will know what is available on the repositories! You will be able to browse Synaptic as if you where online. And Synaptic can create download scripts with this. Also, "apt-get -qq --print-uris" will work offline.

"apt-get update", sources.list visible, several APT lines in sources.list and also the execution of "dpkg -l" if a package is not listed and the user knows it isn't installed will help (I hope) to clarify this mysterious "amarok" problem. Vitesse, when you can, please say what you see if you try to install it again, please.

I hope to ear some feedback on this major changes.

> **[nonetdebs reloaded at unixpod]("http://nonetdebs.unixpod.com/node/16#comment-71")**

             There have been a major change in nonetdebs website.
 

   New host
   Bad news for old users
   New features
   apt-get update and var_lib_apt_lists.tar.bz2
 

**New host**
 

Now the website is hosted at unixpod.com - [http://unixpod.com/about/](http://unixpod.com/about/). The website will be accessible with the same name, but hosted there. The email will come from there. 

Thank you very much, unixpod.com administrators and to the IRC chanel #unixpod in freenode. 
 

This new host (a QEMU virtual machine - gutsy server - running in my personal and only computer was the previous one), should have a much better connection than mine. 

There is a space limit, so now I'm trucating old status files. As now the website is hosted by someone else than me, please don't abuse it. Now there are limits to how much "apt-get" commands you can run. Don't keep clicking to make the page render, wait. It's useless to keep clicking now, it will be logged and you'll get banned. If apt-get is taking too long, select a Ubuntu mirror (in the repositories tab). If you want to see the last apt-get command you executed again, select aptget > Last apt-get output.
 

**The bad news for old users**
 

If you didn't login the last 30 days, chances are that your status file was truncated (zero bytes size). This will be normal procedure from now on. And will get worst because of disk space limit. The disk space is very limited in the new host, so I might have to truncate files very often, be prepared and always have your latest status file with you when you use nonetdebs).

Anyway, as it is recommended to always use the latest status file, it shouldn't be a problem, unless you don't have it at the moment. If you don't have the status file ATM, you still can try the new "apt-get update" feature, see bellow. 

Now you have to run "apt-get update" yourself if you change repositories, just like in a connected computer.

No more locale support (sorry, but the host don't have them). All output will be in english from now on.
 

**The new features**
 

Now you can see much more. You will be able to
   - select a mirror (if ubuntu server is loaded, mirrors are an option now);
   - actually see the sources.list file you're using;
   - add multiple APT lines to the file;
   - see the output of apt-get update;
   - see the last request you made without running apt-get again (no wait);
   - run "apt-get source" to download the source files of a package;
- get the files that apt-get downloads when you run "apt-get update" so you can browse available packages that are in your selected repositories in the target computer. 
 

**apt-get update and var_lib_apt_lists.tar.bz2**
 

About "apt-get update". When you run "apt-get update" on the website, you have a checkbox to say that you want to download the files that are saved by apt-get in /var/lib/apt/lists/ directory. In this directory apt-get saves the Packages.gz files that are on the repositories you selected. 

These files say to apt-get which packages are available in the repository and where to find it in the repository. When you remove someting in sources.list file, apt-get deletes the file from that repository. When you add a new line in sources.list, a new file is downloaded. apt-get only keeps the repositories that are in the sources.list file. All repositories files that are in /var/lib/apt/lists/ directory but aren't in sources.list are deleted when you run "apt-get update". 

It is important to know this because if you don't change sources.list as it was when you executed "apt-get update" here in the website, the -updates and -security repositories (which are commented by default if your system was never online) will never be available in the target, because the sources.list file don't have them. Each time you'll extract the file and run "apt-get update" without the new repositories in the sources.list file, apt-get will delete them.

So, save a copy of the sources.list file you have here in the website. That way you can edit and update the target's sources.list too. You can see the sources.list file that was used in the "Last apt-get output" page (if you use Windows, you will have to convert the file from DOS/Windows format or edit the file by hand). 

Once you downloaded the file and got to the target computer, extract the var_lib_apt_lists.tar.bz2 file, edit your sources.list file and really run "apt-get update" there. Then you will be able to see all the available packages in the selected repositories (new and upgrades) using apt-cache, Synaptic and in the update-manager.
 You still can't download them, but you can run "apt-get -qq --print-uris" yourself or create a download script in Synaptic. You still will need a linux system to run it. Maybe you can use wget for windows to run it from Windows (not tested). Anyway you still can use nonetdebs to list them, if you upload the status file.

To extract the file in the target:
    
    sudo tar -xvjf var_lib_apt_lists.tar.bz2 -C /
 
In the near future I will try to document all this in a clearer way.
     


---

### Post by ruibernardo on 2008-05-08
Vitesse, sorry for this late reply, I've just look at your amarok problem.

- Based on your status file you don't have amarok installed.
- I've found a funny thing about amarok: apt-get will download the same packages for "[amarok]("http://packages.ubuntu.com/hardy/amarok")" or for "[amarok-engine]("http://packages.ubuntu.com/hardy/amarok-engine")" or "[amarok-engines]("http://packages.ubuntu.com/hardy/amarok-engines")". "[amarok-engine]("http://packages.ubuntu.com/hardy/amarok-engine")", the singular, is a virtual package that provides "amarok-xine".
- I tried just "amarok" and nonetdebs did list 3 packages to download (confirms that it isn't installed in that status file).

When you ran the install script, did it gave any errors? Like missing file or file not found? There could be a problem in the package filenames, like packages with a percent signal in the file name. If it happened, the script may fail to find the package, but I'm not sure. 

Can you confirm?

I don't want to be boring, but aptoncd should be used to install the packages. The script is to be used only if you STILL don't have aptoncd installed (or dpkg-scanpackages, installed by dpkg-dev) or another tool to create a local repository with your downloaded packages.

Even if there is a problem with the packages filenames (happens depending on the browser your using, I think), aptoncd will live with that very well. It will list and install amarok anyway. You even could rename the file amarok-xine_1.4.9.1-0ubuntu3_i386.deb to this_is_evil_2.6.3-22zzz_amd64.deb. aptoncd wouldn't care. It will read the control file inside the package and find out what it installs (amarok in this case).

So I recommend to just use the script to install "aptoncd" (or "dpkg-dev"), then use the new status file to download what you want and install them with aptoncd.

---

### Post by jenkinbr on 2008-05-08
> **epimeteo said:**
> 
So I recommend to just use the script to install "aptoncd" (or "dpkg-dev"), then use the new status file to download what you want and install them with aptoncd.

I actually did something similar with my switch to hardy.  I grabbed aptoncd, which returned one package, then I went ahead (without changing status files) downloaded a ton of other stuff - pretty much everything that I run.  I did take note that I might request the same file more than once, but the dl manager I used was smart in that it detected that I wanted to download the same file twice, and asked me what I wanted to do.

Also, thanks for the site upgrade.  It was getting to be slow.  An actual server should help to speed things up a bit.

---

### Post by ruibernardo on 2008-05-08
> **jenkinbr said:**
> I actually did something similar with my switch to hardy. I grabbed aptoncd, which returned one package, then I went ahead (without changing status files) downloaded a ton of other stuff - pretty much everything that I run. I did take note that I might request the same file more than once, but the dl manager I used was smart in that it detected that I wanted to download the same file twice, and asked me what I wanted to do.

Also, thanks for the site upgrade.  It was getting to be slow.  An actual server should help to speed things up a bit.
Good to know it's working better, jenkinbr :)

In this first day in the new host there was two problems that made the use of nonetdebs a bit of erratic. I've corrected them. The problems were about the mirrors and disk space.

Some users have selected different ubuntu mirrors. I should say that not all the countries of the list have a ubuntu mirror, and if it didn't or it's slow (one case I noted of slowness was "Chile CL") apt-get didn't timeout and would not return an error. Solved with Acquire::http::timeout "5"; in apt.conf, so now if the repository or the mirror is too slow, you should see an error saying that (it wasn't doing this before).

A missing parameter in the cron job that should cleans old work directories (each user have one now, created when they execute any "apt-get" link), made the website exceed it's quota space in the server, so several users had strange errors today. Sorry about that, it's corrected now.

For old users (and new too): if you change any repository after you executed any "apt-get" link, you MUST click "apt-get update" to update the repositories that apt-get is using, just as if you were connected. Before it wasn't necessary because every time apt-get was executed, it executed "apt-get update". Now it's not happening that way (except the first time you execute "apt-get", when the work directory is created). This is more consistent with the normal use of apt-get, but you must pay attention to it, because if you don't, apt-get will not find the new repositories and the new packages and can reply saying it can't find a package.

Also about repositories: when a new account is created no repositories are selected. You have to select repositories before you use the "apt-get" links in the menu. This can lead the user to go to "Repositories" and select them, but if the user don't click "apt-get update" after selecting (and in fact, changing the repositories), it will find the same error again. I'll try to correct this in the next few days, but until then, if you change any repositories settings, click "apt-get update" and then "apt-get install/upgrade/whatever".

Tomorow I'll try to improve the documentation of the website to reflect all this new tricks and traps :) I might create a wiki page so users can read common solutions and problems, etc, and may post suggestions and tricks they use to use their offline Ubuntu.

---

### Post by madjr on 2008-06-01
> **epimeteo said:**
> 
WISHLIST: nonetdebs - gtk frontend (zenity).



wow, nonetdebs is awesome. Just what i was looking for.

I'll be looking forward to the **gtk frontend in zenity**, specially as a replacement of the terminal install script.

most users are intimidated of the terminal because they often forget the commands and are left in the cold.

it'll be just as easy as installing apps in windows without internet and passing them to friends n family. :)

---

### Post by hammer v2 on 2008-06-01
Woah what a great script! Thanks! I've been working on something like this..but yours is WAY better! Can I please have a copy of the latest version of this script? (Is the version in this forum the latest version?) I've got some ideas to make it more newbie friendly and I'd like to add them to your script if you don't mind...


Thanks again! GREAT JOB!
H.

---

### Post by jenkinbr on 2008-06-11
I finally got around to using the new version of nonetdebs today, and so far I am not impressed.

See [http://nonetdebs.unixpod.com/node/25#comment-100](http://nonetdebs.unixpod.com/node/25#comment-100) and [http://nonetdebs.unixpod.com/node/25#comment-99](http://nonetdebs.unixpod.com/node/25#comment-99) .

---

### Post by djpc on 2008-06-23
I cannot access the website for some reason. I just get a Ip address error saying it cannot be found or that the website is not listed on this server:confused:

---

### Post by jenkinbr on 2008-06-23
> **djpc said:**
> I cannot access the website for some reason. I just get a Ip address error saying it cannot be found or that the website is not listed on this server:confused:
It does that every once in a while - just wait about a minute and try again.

I guess you mean the 404: Not Found error

From the Unixpod site:
> LDAP Problems
Submitted by charlie on Sun, 06/22/2008 - 20:07.

Hi everyone, we just had an unknown issue with the LDAP server that caused us to lose every single LDAP account from the directory. Luckily, we've been keeping backups, and we were able to restore a lot of accounts from a backup of that. Unfortunately the backup was a little old, so we recreated all the accounts not in the backup through Drupal. So, worst comes to worst, you'll just need to check your emails for your new password. We're now making backups every 12 hours, so we won't have a problem like this in the future. If for whatever reason your account wasn't recreated, please contact a staff and we'll create it from the information stored in Drupal. Thanks for using Unixpod!

I am guessing that this is part of the problem...

---

### Post by _khAttAm_ on 2008-06-27
NoNetDebs is not working for me as well.... its been 3 days and can't still access it... does anybody have any idea??

---

### Post by my_wing on 2008-06-30
> **epimeteo said:**
> Hi,

sorry for loosing this discussion, but I've been busy. Can't add much more to what it's been said, but to confirm what jenkinbr suggested: to use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search packages, although a new "apt-get update" feature is available now. It's not simple, though.

First, the news. I'm not hosting the website anymore. The website is now kindly hosted by unixpod.com at [http://nonetdebs.unixpod.com](http://nonetdebs.unixpod.com). The registration mail will come from there, obviously. You still can use [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net). DynDNS will redirect you to unixpod.com.

I've managed to finally integrate drupal, apt-get as normal user and nonetdebs code (90% redone, so please say if something is broken). Now the site is more quick and its use is more similar to the real use of apt-get.

There are several improvements, and the "apt-get update" one is the most important, as it finally breaks the isolation of the offline apt-get system. [Based in this comment]("http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/#comment-54908") I've found while browsing, I've made nonetdebs get those files for you even if you don't have the status file in your account. I think it's very useful. 

Now you can save what is downloaded by apt-get when you run "apt-get update" with the selected repositories. The offline apt-get system will know what is available on the repositories! You will be able to browse Synaptic as if you where online. And Synaptic can create download scripts with this. Also, "apt-get -qq --print-uris" will work offline.

"apt-get update", sources.list visible, several APT lines in sources.list and also the execution of "dpkg -l" if a package is not listed and the user knows it isn't installed will help (I hope) to clarify this mysterious "amarok" problem. Vitesse, when you can, please say what you see if you try to install it again, please.

I hope to ear some feedback on this major changes.

Please the site is not up for +- a week now get this error message


Not Found

The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch Server at nonetdebs.unixpod.com Port 80

I don't know is this my error or the site is not up.  Need to upgrade to FF3 please help me or provide me with contact detail to the site administrator.

---

### Post by jenkinbr on 2008-06-30
> **my_wing said:**
> 
I don't know is this my error or the site is not up.  Need to upgrade to FF3 please help me or provide me with contact detail to the site administrator.

I don't know where the problem lies, but it is not with us users.  The problem is something to do with the server, which is why you (and everyone else) are getting that error.  I've tried contacting epimeteo about this issue, and have heard nothing back.  As he is the one who has the connection with unixpod, there is not much for us to do except wait patiently until the problem is solved.  I, too, have packages that I need to install and upgrade, and every day I have to wait, it gets a little more painful.

---

### Post by brijith on 2008-07-01
> **jenkinbr said:**
> I don't know where the problem lies, but it is not with us users.  The problem is something to do with the server, which is why you (and everyone else) are getting that error.  I've tried contacting epimeteo about this issue, and have heard nothing back.  As he is the one who has the connection with unixpod, there is not much for us to do except wait patiently until the problem is solved.  I, too, have packages that I need to install and upgrade, and every day I have to wait, it gets a little more painful.


Yea You said It ! This waiting is very painful.. Let's Hope the problem will get solved soon ..... :(

---

### Post by _khAttAm_ on 2008-07-10
I cud have used it in my computer as well.. but I can't find the script that supports hardy...

---

### Post by blindvic on 2008-07-11
> **[SIZE="3"]Not Found[/SIZE]**
The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch Server at nonetdebs.unixpod.com Port 80

I can't access it for a month. So, the project has died?

---

### Post by EXCiD3 on 2008-07-11
I dunno whats happend. I've tried to contact the author a couple of times. Hopefully nothing terrible has happened. Maybe he migrated to windows! :lolflag:

I'm currently working on a slight variant of his project that will make it even easier to use but ive got plenty of work to do, check it out in my signature, its called keryx.

---

### Post by jenkinbr on 2008-07-14
It seems to be a sad state of affairs for Nonetdebs, although I like your idea of starting a different project.  One suggestion: if possible, could you also make a web interface as well - I am not allowed to run arbitrary programs, even scripts, on the school machines that I use.

---

### Post by EXCiD3 on 2008-07-14
> **jenkinbr said:**
> It seems to be a sad state of affairs for Nonetdebs, although I like your idea of starting a different project.  One suggestion: if possible, could you also make a web interface as well - I am not allowed to run arbitrary programs, even scripts, on the school machines that I use.

Yes that was one of my intentions. I planned on contacting the maker of Nonetdebs and collaborating both of our projects together, his with the web interface and mine with the application. I know little PHP and if have still not gotten a hold of him, so i will be looking for a PHP developer to help if anyone is interested.

I dont want to hijack this thread, so please if you have anything to talk about for the Keryx project, please do so on the forums here: [http://keryx.betaserver.org/forum/index.php](http://keryx.betaserver.org/forum/index.php)

---

### Post by Wydarr on 2008-07-23
Oookie... it's been a long time since the site is down. Do you have any idea why is the site down, or if there is a different option to install new packages / update the ones already installed. 
I am in dire need of updating an offline machine, via a Windows computer, and so far it's the only viable option from what I've found. 
Cheers.

---

### Post by EXCiD3 on 2008-07-23
> **Wydarr said:**
> Oookie... it's been a long time since the site is down. Do you have any idea why is the site down, or if there is a different option to install new packages / update the ones already installed. 
I am in dire need of updating an offline machine, via a Windows computer, and so far it's the only viable option from what I've found. 
Cheers.

Unfortunately he and his site have seem to fallen off the edge of the earth :( I havent heard anything back from him and have no idea whats happened. For the mean time you can take a look at my project, Keryx. Its almost into alpha stage which means, while it wont be the most user friendly, itll get the job done. And if you can run exe's off your flash drive on a windows computer then you will be set. Hate to be doing 'advertising' for my project on this thread, but i was hoping to work together with the creator of nonetdebs to have both a web interace AND an application to do this also. If anyone knows PHP and would like to help make a web interface similar to NoNetDebs, please contact me. I hope that NoNetDebs is back up soon, its very useful for when the computers you intend to download the updates on dont allow running arbitrary programs...Feel free to contact me if you would like to help! :)

---

### Post by EXCiD3 on 2008-07-31
Well sadly still no word on anything NoNetDebs related...On the other hand I have released my first Alpha version of Keryx if anyone is interested. Once i get the Ubuntu plugin and everything working nicely in a beta I will start learning PHP and working on a web interface unless someone would like to help me with that or the NoNetDebs project returns miraculously (which i hope!). If you are interested in checking out Keryx while we wait for NoNetDebs heres the link: [http://keryx.betaserver.org](http://keryx.betaserver.org)

---

### Post by jenkinbr on 2008-08-25
[http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/)

It no longer generates a 404 Not Found, but still does not produce the results we would expect...

Time for me to buy a laptop. :|

---

### Post by hammer v2 on 2008-08-29
Hey guys... I'm trying to make a one click packaging system for ubuntu, kubuntu and xubuntu. It doesn't reinvent the wheel and works by using stuff that's already in ubuntu (apt debs etc..). same principle as nonetdebs.
Basically the deal is this;

I'm creating an automated way to bundle a package and all it's dependencies together into one executable file. When The user clicks on the file, it creates a local repository, updates the sources.list and install a metapackage that depends on everything in the new repository. I've tested it and it works great! Yay! 

Anyway, the creation of these "superdebs" happens in a Virtual Machine. Basically I create a BASE distribution as a live CD (Read only) that only gets run in a VM. All this distro does is run my package creator script. It opens up synaptic. You choose which package you want in your superdeb and presto! It creates a superdeb for you.

Only catch is....I need a "BASE" distro. 
Too much stuff in the base distro and the superdebs won't work for everyone. Too little and each "superdeb" will be enormous!

I know I can't please everyone here... but what would be a base distro that would provide a superdeb that works accross kubuntu, xubuntu and Ubuntu?

Sorry for the long post....
H.

---

### Post by ugm6hr on 2008-08-29
I think NoNetDebs has clearly gone.

Discussions regarding potential replacements should start in a new thread in thee programming or Cafe sections.

I'm moving this to outdated Tutorials.

---

### Post by hammer v2 on 2008-09-04
I finished it! yay! well sorta...still crap programming but this definately works.


you can download it from here;

[http://superdeb.googlecode.com/files...reator2.tar.gz](http://superdeb.googlecode.com/files...reator2.tar.gz)

To install it copy all the files exactly into your home directory and run Superdebcreator0.1.sh

Er...I ain't no programmer so use at your own risk! do let me know how you go. I'd love some feedback.


Here's an install file for Amsn I made for gutsy...try it.
[http://superdeb.googlecode.com/files...TA-UB0710.sdeb](http://superdeb.googlecode.com/files...TA-UB0710.sdeb)

p.s if none of those links work try visiting here...
[http://code.google.com/p/superdeb/downloads/list](http://code.google.com/p/superdeb/downloads/list)

I'm a complete novice. Hope this helps!
H.

---

### Post by EXCiD3 on 2008-10-13
If anyone is still looking for a NoNetDebs replacement, check out Keryx: [http://keryx.betaserver.org](http://keryx.betaserver.org)

---

### Post by hammer v2 on 2009-02-02
I finally got superdeb working! I've made double-click installer files for ubuntu (8.10) using a simple gui system.

Just double click on the .sdeb file and it installs - NO INTERNET NEEDED!!

 I'm about to unleash it onto the world but first I wanna be sure it's working correctly. If any of you are using intrepid, would you be so kind as to download pingus (a simple game)from here;

[http://superdeb.googlecode.com/files...-2-UB0810.sdeb]("http://superdeb.googlecode.com/files...-2-UB0810.sdeb")

just download the file, double-click on it and follow the prompts. It's not pretty but seems to be working ok over here.

Please let me know how you guys go! Give me as much feedback as you want. If it works I'll release it properly in the next day or so.

H.

---

### Post by ugm6hr on 2009-02-03
Re: superdeb

I would suggest you start a new thread about this (either in General help or Installation/Upgrades) and post a link from here.

This How-to is now outdated, so will not be particularly well seen.

---

### Post by hammer v2 on 2009-02-03
Already done that, just thought I'd get a bit more coverage if I replied to the end of this thread too. :D

The new thread is located here;
[http://ubuntuforums.org/showthread.php?t=1058376]("http://ubuntuforums.org/showthread.php?t=1058376")

Did you try it ugm6hr? Did it work for you? Busting to get some feedback here.... :)

Have a nice day!
H.

---

### Post by jenkinbr on 2009-02-03
> **ugm6hr said:**
> Re: superdeb

I would suggest you start a new thread about this (either in General help or Installation/Upgrades) and post a link from here.

This How-to is now outdated, so will not be particularly well seen.
IT'S ALIVE! IT'S ALIVE!

IT'S .....oh.

Still dead.  Subscribed threads issued an almost false alarm...

*still wondering what happened to the OP...*

---

### Post by EXCiD3 on 2009-02-03
> **jenkinbr said:**
> *still wondering what happened to the OP...*

Yeah I hope he is alright.

---

### Post by kevinguillorytraining on 2009-10-09
Nice tutorial. Thanks

---

### Post by Albertint on 2010-07-21
So, does this work w/ Lucid?

EDIT: Oh, OK. This sorta stuff has got to be posted in the OP.

---

### Post by shrijesh on 2011-10-01
Hi I have a computer where I have used Ubuntu 11.04 but there is no possibility of internet connection in it. Whenever i try to play any songs/videos it shows that some codec needs to be installed and it needs internet..But I have got internet in a Windows 7 computer. How can I update my Ubuntu from Windows 7???? I tried a lot to do it by seeing this ubuntu forum. Please help me....or you may post a video how to do it if you can.
Thank you

---

### Post by shrijesh on 2011-10-01
d

---

### Post by ugm6hr on 2011-10-01
@shrijesh
This tutorial is outdated - i.e. does not work.
I would suggest starting a new thread to ask for help. There are plenty of help sites to help you understand the basics of Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
One option if you need to play video / music on a computer without internet is to install Linux Mint - it is very similar to Ubuntu, but includes all those codecs and VLC as default.
If you need any further help - please start a new thread in Absolute Beginners section.

---

### Post by shrijesh on 2011-10-01
> **ugm6hr said:**
> @shrijesh
This tutorial is outdated - i.e. does not work.
I would suggest starting a new thread to ask for help. There are plenty of help sites to help you understand the basics of Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
One option if you need to play video / music on a computer without internet is to install Linux Mint - it is very similar to Ubuntu, but includes all those codecs and VLC as default.
If you need any further help - please start a new thread in Absolute Beginners section.
Thanks   i just found a new solution to it ....that is keryx...easy to use for me...i JUST started to use Ubuntu 2 days ago....

---

### Post by madjr on 2011-10-01
> **shrijesh said:**
> Thanks   i just found a new solution to it ....that is keryx...easy to use for me...i JUST started to use Ubuntu 2 days ago....

yes, keryx is very good.

[http://www.webupd8.org/search/label/keryx?max-results=10](http://www.webupd8.org/search/label/keryx?max-results=10)

---

