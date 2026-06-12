---
title: "HOWTO: Install a new version of PAN from CVS (This avoids the slowdowns and lockups)"
date: 2005-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2005-04-01
**[CENTER]Does PAN lock up on you or slow to a crawl?  Here is the solution![/CENTER] **

The version of pan in the repositories has a problem where it locks up or slows down to a crawl when downloading from large binary groups.  This is due to the way that PAN stores all those headers.

Charles Kerr recently made a large update that resolves most of these problems that is available via CVS.

NOTES:
[list]
[*]**THIS IS A BETA AND IT WILL HAVE SOME BUGS**
[*]This converts your data to a new format, if you need to back out to the version available in the repositories remove the folder $home/.pan
[*]We will not be installing PAN, just building it and running it from our home directories.  This way when Charles makes updates you can remove the pancvs folder and perform these steps again to get the newer version and if/when a version reaches the repositories you can simply install them via Apt or Synaptic and delete the pancvs folder
[*]All of the text in the code blocks is entered one line at a time into a terminal window in your home directory.  By default when you start a normal terminal it is in your home directory.  If you want to make sure you are in your home directory type cd $home
[/list] 


Part 1:  Retrieving Dependencies:

Use Apt to grab the dependencies required to build PAN from CVS:
```
sudo apt-get install cvs
sudo apt-get install gnome-common
sudo apt-get install gcc
sudo apt-get install libgtk2.0-dev
sudo apt-get install libxml2
sudo apt-get install libxml2-dev
sudo apt-get install libpcre3-dev
```

Part 2: Download the current from CVS:
Create a directory named pancvs
```
mkdir pancvs
```
Change to the pancvs directory
```
cd pancvs
```
download the PAN source
```
export CVSROOT=":pserver:anonymous@anoncvs.gnome.org:/cvs/gnome"
```
```
cvs -z3 checkout pan
```

Part 3: Build PAN
Change to another pan subdirectory (Yeah this gets a bit nested, you can easily do this straight from home and just have PAN)
```
cd pan
```
Run autogen to configure  If it is successfull you will see a blurb about type make to build PAN
```
./autogen.sh
```
Build PAN
```
make
```



Part 4: Create a Menu Entry
If you have not already downloaded the menueditor application (Hoary Only) get Amaranth's great app from:
[http://www.ubuntuforums.org/showthread.php?t=21390](http://www.ubuntuforums.org/showthread.php?t=21390)
Use dpkg to install the .deb, for example if the file is named: menueditor_0.4.3ubuntu1_all.deb use the following command:
```
sudo dpkg -i menueditor_0.4.3ubuntu1_all.deb
```
Log out and back in click on the menu editor under Applications->System Tools

Use the following options to create a new menu entry for PAN:
```
Name: Pan
Comment: Newsreader for Gnome
Command: Click Browse-> Go to your home directory, then the pancvs folder, then the pan folder and finally scroll down and select the file named pan (not pan.c) and click open.
Category: Internet
Click Save
```

Log in and out of Gnome for the changes to menu item to show up.

You should now be able to run PAN from the menu and it will be able to download even the BUSIEST of the binary newsgroups.

For more information on Pan or to drop Charles a thank you for making working on this great app go to [http://pan.rebelbase.com](http://pan.rebelbase.com)

If you have any questions post them here and I will do my best to answer them.

---

### Post by vnbuddy2002 on 2005-04-04
Thanks.  The latest CVS enhance the performance quite alot!

---

### Post by Darrena on 2005-04-04
[QUOTE=vnbuddy2002]Thanks.  The latest CVS enhance the performance quite alot![/QUOTE]

Glad it helped!

---

### Post by vnbuddy2002 on 2005-04-05
Little note for anyone who experience "Segment fault" with during the compilation. You might want to re-compile again.

---

### Post by Darrena on 2005-06-12
I built a debian package for this that works fine on my system so I don't have to do all of this everytime I reload, I don't have anywhere to host it so if someone wants it post here or send me a PM and I will get it to you.  I tried to work with JDong to get it into backports but I am not sure if it met his requirements or not.

---

### Post by fig_jam_uk on 2006-01-12
This seems sooooooooo much better, And youve also saved my voice in the prossess (stops me shounting obscenities at the moitor, like a n00b)

Thanks again....

---

### Post by dnB on 2006-03-07
thanks for the informative post.
instead of downloading the menu editor i just used 
sudo ln -s /new/pan/locationoffile /usr/bin/pan
as per hosting a deb file to accomplish this, i would be more than happy to host it, i can be reached at [email]dnb@xbins-kai.org[/email]

Brandon

---

### Post by mazirian on 2006-07-11
As I just discovered, the cvs sources are not the new rewrite of pan.  To get the rewrite, which drastically reduces the amount of memory pan uses and keeps it fro bombing out on binary newsgroups with millions of headers, you'll need to grab the snapshots from [http://pan.rebelbase.com/download/releases/](http://pan.rebelbase.com/download/releases/)

---

### Post by blockcipher on 2007-03-02
I have an issue doing this.  Here is what I get:

mikee@CipherX:~/pancvs$ export CVSROOT=": pserver:anonymous@anoncvs.gnome.org:/cvs/gnome"
mikee@CipherX:~/pancvs$ cvs -z3 checkout pan
**Unknown host anoncvs.gnome.org**.
mikee@CipherX:~/pancvs$ 


How do I go about setting this up?

Thanks alot.

---

### Post by Darrena on 2007-03-04
This thread is out of date, there is now a complete rewrite of pan available, if you would like recent packages I build then around a day after release.

See [http://pan.rebelbase.com](http://pan.rebelbase.com) for details or the link in my sig below.

---

### Post by blockcipher on 2007-03-04
Darrena,

Thanks so much!  I am updated :)  Giving it a try now.

---

### Post by fifth on 2007-03-04
> **Darrena said:**
> This thread is out of date, there is now a complete rewrite of pan available, if you would like recent packages I build then around a day after release.

See [http://pan.rebelbase.com](http://pan.rebelbase.com) for details or the link in my sig below.

Thanks for the deb Darrena, very much appreciated.

Haven't experienced slow downs with the previous versions but i'm liking the new beta a lot. More customizations to play with :) and nzb support :D

---

### Post by blockcipher on 2007-03-04
I had HUGE slowdowns/lockups.  This works awesome!

---

### Post by hype on 2007-03-04
Indeed, i highly recommend using latest version.

 It's working just perfect; no crash/bugs so far.

It responds so much faster, you can feel it was rewrote.

---

