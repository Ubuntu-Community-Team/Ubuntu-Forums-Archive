---
title: "HOWTO:  Install Geany from source + sshfs for remote open and save"
date: 2007-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by volksman on 2007-06-10
Geany is a fairly young but quite powerful text editor reminisant of UltraEdit or TreePad for windows. I've been looking for something like this since I switched to Ubuntu last year (still using UE under wine and hate it!).

So without further delay here is my first howto for the Ubuntu Forums community:

Before we start!

Geany is in the Universe repo however it is a fairly old version (when a product is so young and there is active development on it getting the latest version is usually a good idea).  If you don't care to have the latest greatest and can wait till the newer versions hit the repo then just do:

```
sudo apt-get install geany
```

And you will get (at the time of this writing) 0.10.

Otherwise use the instructions below to install either 0.11 or SVN (0.12).


1) Install some dependancies and items you will need to compile:

```
sudo apt-get install build-essential make autoconf automake1.9 subversion libtool libgtk-dev libglib2.0-dev
```

2) Go to your src dir

```
cd /usr/src
```

3) Download the latest source:

```
sudo wget http://umn.dl.sourceforge.net/sourceforge/geany/geany-0.11.tar.gz
sudo tar zxvf geany-0.11.tar.gz
```

OR get the source via svn which IMO is better:

```
sudo svn co https://svn.sourceforge.net/svnroot/geany/trunk geany
```

4) Go into the source dir and start the install

If you downloaded the tarball and unpacked it then
```
cd geany-0.11
```

OR if you went the SVN route

```
cd geany
```

then launch the config autogen script:

```
sudo ./autogen.sh
```

5) Build and install

```
sudo make
sudo make install
```

6) You should now be able to run 'geany' in any terminal and up pops your new favorite text editor!


**SSHFS**

The ONLY feature that geany is missing for it to be a perfect tool for me is the ability to open and save files to FTP or SFTP.  As such I have found that SSHFS can help me while I wait for the developers of geany to add that functionality natively to the app:

1) Install the packages needed:

```
sudo apt-get install sshfs
```

2) Mount a remote FS.  This is almost the same as a Samba mount or ext mount but the syntax is more like an ssh connection:

```
sshfs user@remote.com:/path /media/path
```

Then /media/path will contain the contents of the remote site.  This only works with SFTP servers.  I'm still trying to find a way to do this with basic FTP servers but luckily enough all my projects right now are done via SFTP.

Hope the above is useful to someone.. :)

---

### Post by huygens on 2007-06-16
Nice how-to :-)

I was too disappointed that Geany did not support Nautilus network drive. I have a SSH and Samba mounted drive (via Nautilus), but they do not show up in Geany.
So, I wanted to mount in my fstab the SSH connection, so it will be seen just like any other partitions. However, sshfs does not use mount, or let say I can not use the command mount with sshfs, so I cannot mount my directory in fstab...
If any one as an idea how to solve that? I mean having an entry in the fstab to "automount" at start-up a directory accessible via SSH.

By the way, nice idea to provide an how-to compiling Geany. Though I have a few feedback to improve your article :-)
You could use the command:
sudo apt-get build-dep geany
And you will get all the necessary dependency that Ubuntu is using to build Geany (curently 0.10.2 as you noted). Hopefully those dependencies have not change in the new release, so this command should still be valid to get the necessary packages to compile Geany.

Second feedback, in case one choose to download the latest release (instead of the svn snapshot), there is a missing command. The user should type:
./configure
:-) Of course, if it is via SVN, the autogen.sh is the way to go.

Third feedback, I would not recommend to go under /usr/src to compile geany, because you then need to perform lots of unnecessary commands using sudo. Here is an alternatives without /usr/src and less sudo :-)
```
cd $HOME
mkdir building
cd building
svn co https://svn.sourceforge.net/svnroot/geany/trunk geany
cd geany
./autogen.sh
make
sudo make install
```Only "make install" requires root privileges.

Fourth, last but not least feedback, great work and idea to publish such how-to! :-) Keep up the good work.

---

### Post by Gen2ly on 2007-06-16
Geany's great, my favorite editor.   Could you tell me, is it just my build or does geany have a problem creating new files using the command line.  For example, if you want to create new file in my desktop:

 geany ~/Desktop/mynewfile

When I am done and ready to leave, I click on Save then it prompts for what to call it (see image).  My version is slightly older, so I was just wondering, is it mine or is the a basic issue with the program?

Beside that though, like I said, this program really rocks.

---

### Post by Gen2ly on 2007-06-20
Just talked to one of the developers seems this might be a problem in my installation.  Everything else works fine.  I use it alot. Good grief.

---

### Post by Gen2ly on 2007-06-21
Ah, it works now.  I was using version 0.10.2 which didn't have this support.  I updates to 0.11 and now it works!

---

### Post by aguafuertes on 2007-08-23
Hi, 

nice guide, helped to install my first programm from source :)

One issue I found:

In 1), the following dependancy is not correct
```
libgtk-dev
```

it hast to be
```
libgtk2.0-dev
```

---

### Post by nineowls on 2008-05-02
this works
amazingly well for me
Geany is good, but being able to address our dev, qa & prod environments via file system over ssh is **priceless**
thank you!!!

by the way --permissions on fuse confused me for a minute till I read [this]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")

[trackback]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/trackback/")

---

### Post by aadansh on 2010-08-08
May this help you.

[http://pankajdangi.com/2010/07/how-can-i-access-my-ftp-contains-remotely/](http://pankajdangi.com/2010/07/how-can-i-access-my-ftp-contains-remotely/)

---

