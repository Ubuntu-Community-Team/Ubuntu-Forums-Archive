---
title: "HowTo Install Gaim 2.0 Beta 6 in Edgy"
date: 2007-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by motang on 2007-02-12
Well Gaim 2.0 Beta 6 has been out for some time now, and I have had some time using it on my Win XP but I missed it on my Ubuntu laptop, so I did a bit a research and came across on how to install is from source.  It was very easy and I am going to list the step that I did to install Gaim 2.0 Beta 6 on my Ubuntu Edgy laptop.
1. Make sure you un-install your current Gaim program by typing 
```
sudo apt-get remove gaim
```
in the terminal window.

2. Download the source from Gaim's site. Click [here]("http://sourceforge.net/project/downloading.php?group_id=235&use_mirror=internap&filename=gaim-2.0.0beta6.tar.bz2&55682247") to download the source.

3. Unpack the compressed file onto your Desktop (you can right click on the compressed file and choose Extract Here in GNOME desktop).

4. Once unpacked launch your terminal window and navigate to your Desktop and then to the unpacked Gaim directory
```
cd ~/Desktop/gaim-2.0.0beta6/
```

5.Once in the directory type in 
```
./configure
```
in the terminal window

6. After the configuration is done type in
```
make
```
into the terminal

7. Wait till the make is done (this might take some time), and then type 
```
sudo make install
```
into the terminal

8. After the installation is done you have you brand new Gaim 2.0 Beta 6 installed on you Ubuntu machine.

[COLOR="Red"]NOTE[/COLOR]: You might want to check if you have the dependencies installed on you system to see if you have this installed type in ```
sudo apt-get build-dep gaim
``` into the terminal.  Also please be advised to backup your profile before installing.  In order for you to backup locate .gaim folder in you home directory.  Hope this helps and happy chatting with the new Beta 6 of Gaim 2.0.

---

### Post by Pedro84 on 2007-02-14
Gam 2.0 Beta 6 .deb packages are avaible to download at [http://download.ubuntu.pl/_Edgy_Eft/gaim/2.0.0-beta-6/]("http://download.ubuntu.pl/_Edgy_Eft/gaim/2.0.0-beta-6/")

---

### Post by cmmike1 on 2007-02-14
does this version support file transfers while talking to someone on aim? everytime i would try this it closes gaim down.

---

### Post by motang on 2007-02-14
Cool thanks for the links to the .deb file, I am going keep that in mind and use it on my desktop. :-D

---

### Post by David Mulligan on 2007-02-16
How does one get around apt-get's desire to uninstall ubuntu-desktop along with gaim?

How can we get them to just upgrade the ubuntu package to beta 6?

Thanks,
David

---

### Post by glennric on 2007-02-16
Gaim 2.0 beta 6 is available from the following repository.  Add these lines to /etc/apt/sources.list

```

# Gaim 2.0 beta (GPG Key:  D0AFFF5E937215FF)
deb http://www.elisanet.fi/mlind/ubuntu edgy main
deb-src http://www.elisanet.fi/mlind/ubuntu edgy main

```

You can add the GPG key if you like by typing the following lines in a terminal.
```

# gpg --keyserver subkeys.pgp.net --recv D0AFFF5E937215FF
# gpg --export --armor D0AFFF5E937215FF | sudo apt-key add -

```

Then 'sudo apt-get update' and 'sudo apt-get install gaim'.  You may want to browse synaptic and see what other related packages are available.

---

### Post by Zer0Nin3r on 2007-03-01
I'd be wary of adding repositories if they aren't a reputable source, not saying that the above one isn't...

---

### Post by stalefries on 2007-03-01
The repository I have been using since Gaim 2.0 beta 3 or so has been debuntu.org. It's really good, they get packages out very quickly.

---

### Post by Kingsley on 2007-03-01
Sometimes DBUS support isn't readily configured for some plugins.
```
./configure --enable-dbus
```

---

### Post by zorkerz on 2007-03-08
in step 5 with the ./configure command i get this error

> configure: error:

You must have libxml2 >= 2.6.0 development headers installed to build Gaim.in synaptic it shows that i have libxml2 installed version 2.6.26.dfsg-2ubuntu4

is this my problem? What do i need it get to make this work and how do i go about it?
thanks

Update:  I just noticed that gaim 2.0 beta 3 was still installed in synaptic for some reason the lock version was set I had to undo thin before it would remove it.  I think this may have had something to do with being installed by automatix.  Although removing gaim through automatix did not get ride of this either.  However i still get the same error after removeing this version of gaim.

---

### Post by zorkerz on 2007-03-08
Ok problem solved.  After removing the locked automatix version of gaim 2.0 beta 3 with synaptic.  I was able to successfully install with the deb file pasted above in gdebi.

---

### Post by dunomous on 2007-03-21
It seems that the archive for ubuntu (which is containing my precious libxml2-dev source) is timing out. The time is around midnight on the east coast of the United States. Are the servers rebooting/updating or something?

---

### Post by milad on 2007-03-25
if you want MSN or Google Talk support wich need SSL you should use ./configure --enable-gnutls=yes instead of ./configure

---

### Post by marikohurst on 2007-03-29
> **Pedro84 said:**
> Gam 2.0 Beta 6 .deb packages are avaible to download at [http://download.ubuntu.pl/_Edgy_Eft/gaim/2.0.0-beta-6/]("http://download.ubuntu.pl/_Edgy_Eft/gaim/2.0.0-beta-6/")

Thanks so much for this link!! It works great!! When you go to install this stuff... don't forget to install tk 8.4 & tcl8.4 otherwise it won't work1 Thanks though!! Yippee!! =D>

---

