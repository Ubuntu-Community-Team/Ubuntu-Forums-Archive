---
title: "Need help getting xfire for pidgin..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-04-27
Anyone know how i can install xfire or Gfire that is for pidgin in Ubuntu 8.04 x64????

---

### Post by SOULRiDER on 2008-04-27
Installing [http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.debhttp://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.debhttp://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.deb) should do it. At [http://ubuntuforums.org/showthread.php?t=524347](http://ubuntuforums.org/showthread.php?t=524347) they suggested copying the plugin manually (explained there) if the deb package doesnt work correctly.

---

### Post by jonpz on 2008-05-02
I'm not sure if this is still relevant info, but here's how I got it to work.  I'm the kind of cat that prefers to compile from source if I can't get a repository package.

1. Download the latest source tarball from here: [https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388](https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388) (as of this writing it was gfire-0.7.0.tar.gz).

2. You'll need some packages for the compilation, etc.  I believe build-essential imagemagick and pidgin-dev should do it (maybe someone else could help verify this). So:
```
sudo apt-get install build-essential imagemagick pidgin-dev
```

3. Untar the source code tarball, configure, compile and install.  I personally like to work from /usr/src for compilations, but the downside there is you have to be super user to get it to work.  You could alternatively work from your user's home directory.  Only the 'make install' command should have to be run with a sudo.  Here's how I did it though:
```
sudo su
mv /home/[user]/Desktop/gfire-0.7.0.tar.gz /usr/src
cd /usr/src
tar zxvf gfire-0.7.0.tar.gz
cd gfire-0.7.0
./configure --prefix=/usr
make
make install
exit
mkdir ~/.purple
cp /usr/src/gfire-0.7.0/data/gfire_games.xml .purple/
```
or alternatively (I didn't do it this way, so there might be mistakes, but it should work):
```
mv /home/[user]/Desktop/gfire-0.7.0.tar.gz ~
tar zxvf gfire-0.7.0.tar.gz
cd gfire-0.7.0
./configure --prefix=/usr
make
mkdir ~/.purple
cp data/gfire_games.xml ~/.purple/
sudo make install
```

These steps of course assume the package name is gfire-0.7.0.tar.gz (which is accurate as of this writing) and that the tarball got downloaded to your user's desktop (the default download location for Firefox).  And, of course, you would replace [user] with your username.  This was run on Ubuntu 8.04 x64. If pidgin is running when you install, you will have to restart pidgin to get it to work.

Hope that helps.

---

### Post by lbinter on 2008-05-06
[http://downloads.sourceforge.net/gfire/gfire_0.7.0-amd64.deb?modtime=1209923668&big_mirror=0](http://downloads.sourceforge.net/gfire/gfire_0.7.0-amd64.deb?modtime=1209923668&big_mirror=0)

This is the 64bit deb File

Link from [http://edhewitt.co.uk/gfire/](http://edhewitt.co.uk/gfire/)

Worked perfectly for me

---

### Post by dtrot55 on 2008-05-07
THANKS! Will def give it a try when i get off work

---

### Post by Zanshin on 2008-05-09
gfire ? Just installed it.  :guitar:

Here is the EZ noob GUI way if you're new to the cli stuff:

Go here

[http://sourceforge.net/project/showfiles.php?group_id=141362]("http://sourceforge.net/project/showfiles.php?group_id=141362")

Download 

I used this pkg:
 	gfire-0.7.0.deb 

Right click on the file in your download folder and pick the top item "Install with GDebi package installer"  

Load pidgin, go to accounts/ add, and ta-da, it's an option in the list!!

Seems to work for buddy list, find xfire profile, but no connection to the gfire games server list?  

Good luck!  :)

---

### Post by dtrot55 on 2008-05-09
Worked>>>thanks@!!!

---

