---
title: "HOWTO: Install Lightscribe Software"
date: 2006-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by StefAndrew on 2006-10-31
This is a basic howto for installing Lightscribe on Ubuntu.

Currently, I am using Ubuntu 6.10 Edgy, and I can get the application to work, however, it does not want to detect my DVD/Lightscribe burner.

**_Step 1:  Download Files from Lacie.com_**
First you will need to download the 2 necessary files from [here]("http://www.lacie.com/products/product.htm?pid=10803").

Save these to your home folder, or where ever you would like.

**_Step 2:  Convert .RPM to .DEB_**
First step, if you don't have it installed already, you will need to install Alien to convert the .rpm files to .deb.  Pull up your console and type the following:

sudo apt-get update
sudo apt-get install alien

After Alien is installed, you can covert your .rpm files.  Make sure you are in the same location where you saved the .rpm files.

sudo alien -d <file-name>.rpm

*One of the files will give an error regarding scripts.  I ignored this, which might be part of my problems, but it installed fine.

**_Step 3:  Install the .DEB files._**
Now, the next to last step, we will install the .DEB files.  From your console you will need to be in the same folder we have been working from.

sudo dkpg -i <file-name>.deb

Do this command for both files.

**_Step 4:  Running the software._**
There are 2 forms of the software now installed, a gui version and a cli(command line) version.  Pull up the run program window, Alt+F2, and type in 4L-gui to run the program.

From here, you can browse to find the picture you wish to use on your lightscribe cd/dvd.  It seems to be a very basic program however, and you will have to do all image and text editing from a different program, i.e. Gimp, and then browse for the image and line it up in the 4L-gui program.

Please feel free to post comments and any problems so that the community can help out.  I will continue to update this with feedback from you, and with my own findings.

Hope this helps at least somoeone out there.

[update]
Just wanted to let everyone know that hasn't read any other threads on Lightscribe, the software is not currently working with version 6.10.  Both Lightscribe and Lacie have stated they tested it on version 6.06 with no problems.  They are looking into getting the software to work with 6.10.  I will update this post when they have updated their software, or someone develops a work around in the meantime.
[/update]

Andrew

---

### Post by StefAndrew on 2006-11-16
Quick update.  It still seems people are having trouble with Lightscribe and Edgy.  If anyone can figure out a fix or if Lacie comes up with a new version, please let us know.

Thanks.

---

### Post by cblanquer on 2006-12-07
A couple of corrections to help:
1. It seems you missmatched "-r" instead of "-d".
2. Regarding scripts, I used parameter "--scripts" to have them included.

I hope it helps.

---

### Post by StefAndrew on 2006-12-08
Thanks for pointing that out.  About the --scripts, did it give you an error when you ran alien?  I did this almost a month ago now, and I was sure when I used the --scripts parameter, it gave errors when converting to .deb.

Thanks again for the help.

---

### Post by ECPCLINUX on 2006-12-09
Hello, I installed Lacie Lightscribe for Linux but, I used Automatix to install it. It seems it works well but it won't recognize my Samsung Lightscribe drive. I'm currently using Ubuntu 6.10, I was wondering If anyone knows how to fix this problem. If anyone does could you please post it here? Thx! ](*,)

---

### Post by po0f on 2006-12-09
ECPCLINUX,

Currently, only Dapper (6.06) is supported.

---

### Post by StefAndrew on 2006-12-09
Yes, poOf is correct.  Lacie also knows that it is currently broken for 6.10.  They are working on finding what is causing the problem and correcting.  Lightscribe.com also has software for linux now, but they say specifically that it doesn't work with Debian based distros such as Ubuntu.

Hopefully soon they will have this fixed.  I miss using my lightscribe drive, but not enough to go back to M$ just for that.  I've been Windows free on my main PC for over 6 months now, and no looking back!

---

### Post by mervg on 2006-12-11
I'm ready to set up lightscribe on Dapper, if I can figure out how to get the software downloaded. No matter what source I try, the software is, according to the screen, downloaded by MPlayer. Okay, maybe so, but where does it go? I didn't know MPlayer was a download manager for .rpm, and I wonder if anyone who has already downloaded this software could give me any suggestions. (I have Nero Linux-trial version loaded, but no lightscribe)

---

### Post by bodhi.zazen on 2006-12-12
Nice How-to

This thread has been added to the UDSF wiki.

[Lightscribe](http://doc.gwos.org/index.php/Lightscribe)

---

### Post by mervg on 2006-12-12
> **mervg said:**
> I'm ready to set up lightscribe on Dapper, if I can figure out how to get the software downloaded. No matter what source I try, the software is, according to the screen, downloaded by MPlayer. Okay, maybe so, but where does it go? I didn't know MPlayer was a download manager for .rpm, and I wonder if anyone who has already downloaded this software could give me any suggestions. (I have Nero Linux-trial version loaded, but no lightscribe)

(Bumping) What if I delete Mplayer?) Never mind - that did it. Whew!

---

### Post by bionnaki on 2006-12-21
nice. I want to purchase a lightscribe. hopefully this how-to works.

---

### Post by po0f on 2006-12-25
Just to let people know that stumble upon this thread and use Edgy 6.10, [you can](http://www.ubuntuforums.org/showthread.php?t=322829) indeed use your LightScribe burners with Edgy.  :)

---

### Post by cd-r80 on 2006-12-28
That Mplayer Download problem: In Firefox, "save link as" (right click).

---

### Post by Jerry N on 2007-09-27
I have Lightscribe capable drives on 3 computers (Win XP) and a pile of Lightscribe CDs and DVDs but I haven't created a Lightscribe label for several months and haven't worried about it at all in Linux.  After creating a few LS labels, I went back to the old trusty Sharpie Ultra Fine Point Marker.  If I really felt the need for fancy labels I would buy one of those $129 Epson printers that will print a full color smudgeproof label on a disk in less than 3 minutes.  I am assuming that it could be made to work in Linux.

Jerry

---

### Post by Joe_Linux on 2007-10-15
I am using Ubuntu 7.10 and followed the how-to in the first part of this thread I was not able to install the first deb file

joe@joe-desktop:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
joe@joe-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper dpkg-dev gettext html2text intltool-debian libbeecrypt6 librpm4
  po-debconf rpm
Suggested packages:
  lsb-rpm lintian dh-make debian-keyring cvs gettext-doc
Recommended packages:
  libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  alien debhelper dpkg-dev gettext html2text intltool-debian libbeecrypt6
  librpm4 po-debconf rpm
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 4255kB of archives.
After unpacking 15.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main dpkg-dev 1.13.24ubuntu6 [147kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main html2text 1.3.2a-3 [95.5kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gettext 0.16.1-1ubuntu2 [1551kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main po-debconf 1.0.8 [111kB]        
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main debhelper 5.0.42ubuntu1 [514kB] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libbeecrypt6 4.1.2-6build1 [108kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main librpm4 4.4.1-14build1 [990kB]  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main rpm 4.4.1-14build1 [603kB]      
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main alien 8.65 [104kB]             
Fetched 4255kB in 14s (289kB/s)                                                
Selecting previously deselected package dpkg-dev.
(Reading database ... 116599 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.16.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.8_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.42ubuntu1_all.deb) ...
Selecting previously deselected package libbeecrypt6.
Unpacking libbeecrypt6 (from .../libbeecrypt6_4.1.2-6build1_i386.deb) ...
Selecting previously deselected package librpm4.
Unpacking librpm4 (from .../librpm4_4.4.1-14build1_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.4.1-14build1_i386.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../archives/alien_8.65_all.deb) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up html2text (1.3.2a-3) ...

Setting up gettext (0.16.1-1ubuntu2) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.8) ...
Setting up debhelper (5.0.42ubuntu1) ...
Setting up libbeecrypt6 (4.1.2-6build1) ...

Setting up librpm4 (4.4.1-14build1) ...

Setting up rpm (4.4.1-14build1) ...

Setting up alien (8.65) ...
joe@joe-desktop:~$ sudo alien -d lightscribe-1.8.15.1-linux-2.6-intel.rpm
Warning: Skipping conversion of scripts in package lightscribe: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
lightscribe_1.8.15.1-1_i386.deb generated
joe@joe-desktop:~$  sudo alien -d 4L-1.0-r6.i586.rpm
4l_1.0-1_i386.deb generated
joe@joe-desktop:~$ sudo dkpg -i lightscribe-1.8.15.1-linux-2.6-intel.rpm
sudo: dkpg: command not found
joe@joe-desktop:~$ 

Any help would be appreciated

---

### Post by GreatGariny on 2007-10-16
There is a typo in the tutorial.  The command is dpkg NOT dkpg.

> joe@joe-desktop:~$ sudo dkpg -i lightscribe-1.8.15.1-linux-2.6-intel.rpm
sudo: dkpg: command not found

So this command should work:
```
sudo dpkg -i lightscribe-1.8.15.1-linux-2.6-intel.rpm
```

---

### Post by m_gasior on 2007-10-16
Check this site [>>Pre-Release Software Evaluation<<]("http://www.lightscribe.com/downloadsection/pse/index.aspx?campaign=1573&recipient=779800&link=download2")

> LSS support for Debian-based Linux distributions such as Ubuntu is now available.

[lightscribe-1.10.13.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribe-1.10.13.1-linux-2.6-intel.deb")

---

### Post by Mochtroid-X on 2007-10-21
> **m_gasior said:**
> Check this site [>>Pre-Release Software Evaluation<<]("http://www.lightscribe.com/downloadsection/pse/index.aspx?campaign=1573&recipient=779800&link=download2")



[lightscribe-1.10.13.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribe-1.10.13.1-linux-2.6-intel.deb")
That's great and all, but utterly useless since HP's link for *lightscribeApplications-1.8.11.0-linux-2.6-intel.deb* is down and I can't find a working copy of it anywhere else.

---

### Post by phisher1 on 2007-10-21
Grab LaCiE LightScribe Labeler 

[http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm](http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm)

Convert the rpm using alien
apt-get install alien
sudo alien -k 4L-1.0-r6.i586.rpm which will make 4l-1.0-r6-i386.deb

sudo dpkg -i 4l-1.0-r6-i386.deb to install like normal.. works fine

---

### Post by Hilko on 2007-11-09
This is how I got simple labeler and 4L (Lacie Lightscribe Labeler for Linux) working in Gutsy;

Go to [http://www.lightscribe.com/downloads...nux/index.aspx](http://www.lightscribe.com/downloads...nux/index.aspx) , download and install
lightscribe system software
lightscribe simple labeler.

This must be done in the above order. Choose the .Deb files, (not the .rpm). Installation instructions are given there, but it just comes down to downloading and double clicking on the downloaded files.

To install 4L, download 4l_1.0-r6_i386.deb from [http://uploads.mitechie.com/lightscribe/](http://uploads.mitechie.com/lightscribe/) and double click the downloaded file.

Add launchers on your panel;
for simple labeler use the command: /opt/lightscribeApplications/SimpleLabeler/SimpleL abeler
for 4L use the command: 4L-gui

done.

The applications run fine, but I have not yet tested them by actually burning a label.

---

### Post by xjgnsdof on 2007-11-10
Good directions, Hilko; it was pretty easy to set up on Gutsy. Have you since tested it out on a Lightscribe DVD?

---

### Post by Hilko on 2007-11-10
I just burned my First label ! and it worked !!! (I've tested both simple labeler and 4L)

The launcher for 4L runs the program but the only thing is that to actually burn a label with 4L one needs to run it with root priveleges. So in a terminal type: ```
$sudo 4L-gui
```
then you can enjoy burning sweet labels :)

---

### Post by xjgnsdof on 2007-11-10
Nice. I set up a launcher with that command, and it's working great.

---

### Post by phillywize on 2007-11-10
The install went fine -- (although the lightscribe.com link was broken when I tried it).  The.deb files from mitechie.com worked fine, and the readme.txt on that site was good too.  Thanks!  (haven't burned anything yet, but I'll report back).


> **Hilko said:**
> This is how I got simple labeler and 4L (Lacie Lightscribe Labeler for Linux) working in Gutsy;

Go to [http://www.lightscribe.com/downloads...nux/index.aspx](http://www.lightscribe.com/downloads...nux/index.aspx) , download and install
lightscribe system software
lightscribe simple labeler.

This must be done in the above order. Choose the .Deb files, (not the .rpm). Installation instructions are given there, but it just comes down to downloading and double clicking on the downloaded files.

To install 4L, download 4l_1.0-r6_i386.deb from [http://uploads.mitechie.com/lightscribe/](http://uploads.mitechie.com/lightscribe/) and double click the downloaded file.

Add launchers on your panel;
for simple labeler use the command: /opt/lightscribeApplications/SimpleLabeler/SimpleL abeler
for 4L use the command: 4L-gui

done.

The applications run fine, but I have not yet tested them by actually burning a label.

---

### Post by xjgnsdof on 2007-11-10
Yeah, the link is broken. The correct link is [http://www.lightscribe.com/downloadSection/linux/index.aspx]("http://www.lightscribe.com/downloadSection/linux/index.aspx").

I burned my first text-only Lightscribe label through Simple Labeler. I'm guessing that a 4L label burn will go swimmingly.

---

### Post by Stevie2k on 2007-11-25
I just added a hint how to enhance the contrast really a lot for the actual lightscribe software...  (I am just using 32 Bit Intel Gutsy, no idea if this works everywhere...)

take a look here: [http://ubuntuforums.org/showpost.php?p=3835068&postcount=19]("http://ubuntuforums.org/showpost.php?p=3835068&postcount=19")

Greets,
Stevie2k

---

