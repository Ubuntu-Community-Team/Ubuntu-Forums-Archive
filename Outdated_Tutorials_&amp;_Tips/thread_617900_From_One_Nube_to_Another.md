---
title: "From One Nube to Another"
date: 2007-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by TrakerJon on 2007-11-19
To install RealPlayer...
1. Go to System menu
2. Select Administration
3. Select Software Sources
4. Add [**deb http://www.debian-multimedia.org](**deb http://www.debian-multimedia.org) stable main** to the Third Party Software section
5. Close and Reload
6. If you get a key error type: **sudo apt-get install debian-multimedia-keyring** in a terminal session
7. Type: **sudo apt-get install realplayer** in a terminal session
8. Launch from Applications/Sound and Video menu and hit Next through to Finish

---

### Post by TrakerJon on 2007-11-19
Install msfonts...

**sudo apt-get install msttcorefonts**

---

### Post by taurus on 2007-11-19
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Achetar on 2007-11-19
Install Flash
sudo apt-get install flash-nonfree
(make sure university repository is enabled)

---

### Post by TrakerJon on 2007-11-19
To install **Gnutella** ('cause ya gotta have tunes man)...

Open a Terminal session...

**sudo apt-get install gtk-gnutella**

**Audacious** is essentially a lot like XMMS...

**sudo apt-get install audacious**

The new **XMMS2** used with **Esperanza** has a very rich sound (even out of cheap speakers).

**sudo apt-get install xmms2**

**sudo apt-get install xmms2-plugin-all**

**sudo apt-get install esperanza**

You might like **BMPx** too...

**sudo apt-get install bmpx**

Edit audio...

**sudo apt-get install audacity**

**Azureus** might come in handy...

**sudo apt-get install azureus**

---

### Post by TrakerJon on 2007-12-23
You'll want these at some point...lots of codecs for audio and video.

1. Go to System menu
2. Select Administration
3. Select Software Sources

Add **deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main** to the Third Party Software section

Close and Reload

If you get a key error type: **sudo apt-get install debian-multimedia-keyring** in a terminal session

**sudo apt-get install w32codecs**

Kaffeine is nice too...but make sure you install Realplayer, Win32 Codecs and libdvdcss2 first.

**sudo apt-get install libdvdcss2**

**sudo apt-get install kaffeine**

Then modify the decoder references under Settings and xine Engine Parameters to reflect the correct paths to both Realplayer and Win32 codecs

Some folks like Amarok... **sudo apt-get install amarok**
Some rave about VLC... **sudo apt-get install vlc vlc-mozilla-plugin**
and there's also Xine... **sudo apt-get install xine-ui xine-plugin**

**Kaffeine** works the best for me when playing DVD's (without having to tweak something).

---

### Post by TrakerJon on 2007-12-23
If you've installed **Kubuntu** you may want the Synaptic Package Manager

**sudo apt-get install synaptic**

---

### Post by TrakerJon on 2007-12-23
Post Deleted - No Longer Revelent

---

### Post by TrakerJon on 2007-12-25
You'll want the following...

**sudo apt-get install totem-gstreamer**

**sudo apt-get install gstreamer0.10-plugins-base**

**sudo apt-get install gstreamer0.10-plugins-good**

**sudo apt-get install gstreamer0.10-plugins-bad**

**sudo apt-get install gstreamer0.10-plugins-ugly**

**sudo apt-get install gstreamer0.10-ffmpeg**

and these...

**sudo apt-get install avifile-divx-plugin**

**sudo apt-get install avifile-xvid-plugin**

**sudo apt-get install libxine1-ffmpeg**

**sudo apt-get install xine-plugin**

---

### Post by barbedsaber on 2007-12-25
This is good stuff, it will take so much pressure off of the forums.

---

### Post by TrakerJon on 2007-12-25
Adobe Flash

**sudo apt-get install flashplugin-nonfree**

---

### Post by yestoAPRS on 2007-12-25
I just installed Ubuntu 7.10 yesterday on an old xtra windows 98 box.
I have no clue what I am in for.
I want to get Xastir up and running for amateur radio.
Your'e looking at one of the most clueless guys to sit in front of Linux.
I do have an Internet Radio Linking Project CPU running CentOS though that used to have Redhat Fedora ver.9  on it and I managed to get that going Saturday.  So I'm the new guy Merry Christmas.

---

### Post by TrakerJon on 2007-12-25
Adobe still makes the best .pdf viewer...

**sudo apt-get install acroread**

---

### Post by TrakerJon on 2007-12-25
yestoAPRS,

Well, I haven't progressed to the point of running an amateur radio station but what I've posted here seems to work for most folks.

Trak

---

### Post by TrakerJon on 2007-12-25
Post Deleted - No Longer Relevent

---

### Post by TrakerJon on 2007-12-25
Associate files with applications...

   1. Right-click on a file you wish to set a default application association
   2. Select Properties
   3. Select the Open With tab (all makes sense, now, doesn&#8217;t it?)
   4. Select the application you want associated with that file type
   5. Click Close

Double-click the file to make sure it opens with the desired program.

---

### Post by TrakerJon on 2007-12-25
**Wine**

**sudo apt-get install wine**

Lots of Windows programs will work on Ubuntu with the help of Wine, I just use simple ones like mIRC and PuTTY.

---

### Post by yestoAPRS on 2007-12-26
> **TrakerJon said:**
> yestoAPRS,

Well, I haven't progressed to the point of running an amateur radio station but what I've posted here seems to work for most folks.

Trak

Right now I am trying to drive the soundcard that was in the cpu. 
I don't know what kind it is, I didn't look yet but it's a Gateway computer.
Whatever windows 98 had for a soundcard I imagine, don't know who has been in the box.
It was free from an estate and I didn't have the password for the operating system that was in it so...
Ubuntu went in it. 7.10.  I don't even have it on the internet yet.
I have such a long way to go with it.

---

### Post by TrakerJon on 2007-12-26
yestoAPRS,

 I suggest you learn a little about the architecture of your box before proceeding. Go to the Gateway site and enter in the serial/product code to find out what it shipped with regarding hardware and device drivers. Secondly, you might want to consider installing Windows 2000 or XP and then the various software drivers related to your hardware as practice...you'll have a huge learning curve if you don't know basic OS and hardware fundamentals before trying to manually configure a Linux box. In other words you're putting the cart before the horse. 

Note: Windows APRS software is also available until you get the hang of Linux.

Trak

---

### Post by yestoAPRS on 2008-01-08
> **TrakerJon said:**
> yestoAPRS,

 I suggest you learn a little about the architecture of your box before proceeding. Go to the Gateway site and enter in the serial/product code to find out what it shipped with regarding hardware and device drivers. Secondly, you might want to consider installing Windows 2000 or XP and then the various software drivers related to your hardware as practice...you'll have a huge learning curve if you don't know basic OS and hardware fundamentals before trying to manually configure a Linux box. In other words you're putting the cart before the horse. 

Note: Windows APRS software is also available until you get the hang of Linux.

TrakOk well I already have all the windows APRS software:
WinAPRS
UI-view
APRSPoint
I already have Xastir V.1.9.2 is up and running on the internet after spending 7 hours building the program.
It can be sound enabled but my soundcard isn't working.
Also I have a working IRLP centOS up and running connected to our local amateur radio 2 meter repeater.
the centOS automatically detected the soundblaster soundcard and it works just fine I am using AUMIX to control the settings and saved them with  AUMIX -S  as root in the terminal window.
So I am not completely in the dark just in the twilight.:)  I can't see why Ubuntu doesn't detect the soundcard (it is a soundblaster also) in the Gateway box.


Sooooo there you have it.  I have three Windows boxes with XP pro running amateur radio software
Annnnd now I want to continue down the road and get the Linux box with Ubuntu and Xastir working with all the features.  Also I have to figure out how to setup the serial port COM1 from the Ubuntu box and Xastir so the TNC and the tranciever can talk to each other.  


I am sure  I won't be able to count the change in my pocket or carry on a conversation with a "normal" person when I get this figured out.:lolflag:


Learning the AX.25 protocol is no picnic either considering I never had a computer in front of me in my life until May of 2004.

But I need help, help, help!

Respectfully yours,
:confused:

---

### Post by TrakerJon on 2008-02-10
**Clam Antivirus**

Go to **System** then **Administration** select **Software Sources** and under **Third-Party Software** add: 

**deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free**

Under **Authentication** click **Import Key File** after you've downloaded it from:

**[http://www.debian.org/volatile/etch-volatile.asc](http://www.debian.org/volatile/etch-volatile.asc)**

**sudo apt-get install clamav clamtk unrar lha clamav-docs arj unzoo**

Launch the **Virus Scanner** from **Applications** under **Accessories**.

---

### Post by TrakerJon on 2008-02-16
Some other notes...for those taking UNIX classes like me,

Install the **C Shell**...**sudo apt-get install csh**

Install the **T Shell**...**sudo apt-get install tcsh**

Install the **K Shell**...**sudo apt-get install ksh**

Install the **Z Shell**...**sudo apt-get install zsh**

Looking for the **Vi** editor? **Vim** works the same on Ubuntu...**sudo apt-get install vim**

You might want to practice using **mailx**...**sudo apt-get install mailx**

Last but not least...if you need an **SSL client** to login to the UNIX box at school or work, **PuTTY** is awesome and also free. I use the Windows version (after installing Wine **sudo apt-get wine**) from [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Side Note: **University of Massachusetts Lowell** offers online certification courses in **UNIX** (one of the few that do) and believe it or not it is affordable [http://continuinged.uml.edu/certificates/unix.cfm](http://continuinged.uml.edu/certificates/unix.cfm)

---

### Post by TrakerJon on 2008-03-30
Install **spell** and **sed** for spell check and streamline editing...

**sudo apt-get install spell**
**sudo apt-get install sed**

---

### Post by TrakerJon on 2008-05-16
Firestarter is an easy to configure GUI firewall for your Ubuntu workstation...

**sudo apt-get install firestarter** from a terminal window

or simply...

**sudo ufw enable** to enable your default firewall at system startup.

---

### Post by TrakerJon on 2008-05-20
USE AT YOUR OWN RISK (may cause broken packages)


**Medibuntu**

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by TrakerJon on 2008-05-21
USE AT YOUR OWN RISK (may cause broken packages)


**Debian Stable**

[http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main


**Debian Volatile**

deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free

sudo wget -q [http://www.debian.org/volatile/etch-volatile.asc](http://www.debian.org/volatile/etch-volatile.asc) -O- | apt-key add -

**Debian Backports**

deb [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib non-free

deb-src [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib non-free

sudo wget -q [http://backports.org/debian/archive.key](http://backports.org/debian/archive.key) -O- | apt-key add -

(if you have problems getting the key download [http://backports.org/debian/archive.key](http://backports.org/debian/archive.key) and import it)

---

### Post by R_T_H on 2008-05-21
Nube means cloud in Latin, IIRC

---

### Post by Sealbhach on 2008-05-22
> **R_T_H said:**
> Nube means cloud in Latin, IIRC

No, that's nebula. 


.

---

### Post by R_T_H on 2008-05-23
from an online dictionary: 

nubes
N F 
cloud/mist/haze/dust/smoke; sky/air; billowy formation (hair); swarm/multitude 

From my old textbook: 

**nubes, nubis** *f* cloud


.

It's a little off topic, so let the thread return to helping people

---

### Post by TrakerJon on 2008-06-03
It was recommended by others to use the following commands for installing the latest Java JRE 1.0.6_06 with Ubuntu but I had a problem with the java browser plugin using the latest Firefox so you may want to try my solution.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


I download the latest <jre version>.rpm.bin file from Java.com ...then extract the .rpm file after making it executable.

Install alien...

sudo apt-get install alien

and then use...

sudo alien --scripts <jre file name>.rpm to convert it to <file name>.deb and then install the .deb file.

Then I link to the java plugin from the /usr/lib/firefox 3.0/plugins folder...

sudo ln -s /usr/java/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

---

### Post by anotherdisciple on 2008-06-03
> **taurus said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I'm not trying to be a jerk or anything, but Taurus' link would eliminate a lot of this post. By typing sudo aptitude install ubuntu-restricted-extras you get the M$ fonts, flash-nonfree, all of the codecs that I can think of, a pdf reader(i don't think it's adobe though),and java.

Wine was a good suggestion for new people. To my knowledge... all linux distros already come with the C shell, K shell, Vim, spell, and sed... so those aren't much help. I'm not so sure that the debian repos will due any good over the ubuntu repos.

Anti-virus seems like bloat to me. Linux is amazingly secure. Firestarter confuses me because from what little I know about IP tables... linux is really really secure from default.

So, to make your post more simple for noobs.... 

For just about everything you'll need multi-media... type this in the terminal:

```
sudo aptitude install ubuntu-restricted-extras
``` 
(replace "ubuntu" if you are using kubuntu, xubuntu, etc., with the appropriate version)


If you want a meda player that does just about everything but isn't the prettiest... get VLC bye typing this:

```
sudo aptitude install vlc
```

If you use ubuntu but like amarok try Exaile

```
sudo aptitude install exaile
```

---

### Post by TrakerJon on 2008-06-05
> **anotherdisciple said:**
> I'm not trying to be a jerk or anything, but Taurus' link would eliminate a lot of this post. By typing sudo aptitude install ubuntu-restricted-extras you get the M$ fonts, flash-nonfree, all of the codecs that I can think of, a pdf reader(i don't think it's adobe though),and java.

Wine was a good suggestion for new people. To my knowledge... all linux distros already come with the C shell, K shell, Vim, spell, and sed... so those aren't much help. I'm not so sure that the debian repos will due any good over the ubuntu repos.

Anti-virus seems like bloat to me. Linux is amazingly secure. Firestarter confuses me because from what little I know about IP tables... linux is really really secure from default.

So, to make your post more simple for noobs.... 

For just about everything you'll need multi-media... type this in the terminal:

```
sudo aptitude install ubuntu-restricted-extras
``` 
(replace "ubuntu" if you are using kubuntu, xubuntu, etc., with the appropriate version)


If you want a meda player that does just about everything but isn't the prettiest... get VLC bye typing this:

```
sudo aptitude install vlc
```

If you use ubuntu but like amarok try Exaile

```
sudo aptitude install exaile
```

_______________________________________________________________________

Well, I followed your suggestions and ran into issues with transcode when I tried to use it. Unfortunately, csh, ksh and zsh are not included, I guess most folks simply use the bash shell but every once in a while you may find the need for the others. Firestarter is easy to use, guarddog is a little more complex, maybe that's what you meant? I'll stick to gradually installing what I need or want...thanks for trying to help though. There are viruses for linux out there in the wild, better safe than sorry I say....Avast! makes a good anti-virus product too [http://www.avast.com](http://www.avast.com). The instructions for the gui are here [http://www.howtoforge.com/virus-protection-with-avast-on-ubuntu-gutsy-gibbon](http://www.howtoforge.com/virus-protection-with-avast-on-ubuntu-gutsy-gibbon)

Traker

---

### Post by bodhi.zazen on 2008-06-05
TrakerJon: I understand what you are doing, learning, and that is great.

Some small pieces of advice, start with "official" methods first. They are supported and will be less likely to cause problems.

Second, if at all possible stay with the Ubutnu repos. Not all .deb are equal and you may have problems if pull in Debian .deb. Better, IMO, to learn to install from source. You can make a .deb from source code with checkinstall.

I have a similar problem with some multimedia. My wife listens to a certain stream and the only way it works is to install mplayer then realplayer. There is a generic deb for realplayer.

Take a look at the links provided:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It will guide you through most multimedia and you will be less likely to break you system.

---

### Post by TrakerJon on 2008-06-06
> **bodhi.zazen said:**
> TrakerJon: I understand what you are doing, learning, and that is great.

Some small pieces of advice, start with "official" methods first. They are supported and will be less likely to cause problems.

Second, if at all possible stay with the Ubuntu repos. Not all .deb are equal and you may have problems if pull in Debian .deb. Better, IMO, to learn to install from source. You can make a .deb from source code with checkinstall.

I have a similar problem with some multimedia. My wife listens to a certain stream and the only way it works is to install mplayer then realplayer. There is a generic deb for realplayer.

Take a look at the links provided:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It will guide you through most multimedia and you will be less likely to break your system.

____________________________________________________________


Well, "official methods" broke my java install and gave me issues with transcode. Thanks for the link and please note I was careful to add disclaimers to the third party Debian links. What I'm looking for is an almost flawless workstation install and I think I've got what I'm looking for so far.

---

### Post by bodhi.zazen on 2008-06-07
> **TrakerJon said:**
> ____________________________________________________________


Well, "official methods" broke my java install and gave me issues with transcode. Thanks for the link and please note I was careful to add disclaimers to the third party Debian links. What I'm looking for is an almost flawless workstation install and I think I've got what I'm looking for so far.

I am sorry to hear that, I have had problems with "official" methods as well, but not the one you describe.

FYI: if "official methods" broke your install, you should file a bug report (official methods are supported and bug reports are the way to initiate official channels, lol).

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by Sealbhach on 2008-06-07
I found Firefox and Open Office apps were very slow starting up so I just installed this with one click. It's like Prefetch in Windows. It keeps your most used applications ready for startup.

It may use up memory, I don't know. Works great for me.

[http://www.ubuntu-unleashed.com/2008/03/tweak-ubuntu-boot-speed-and-application.html](http://www.ubuntu-unleashed.com/2008/03/tweak-ubuntu-boot-speed-and-application.html)

Read about it and install it if you want it.



.

---

### Post by TrakerJon on 2008-06-17
If you have kids (2-10 years old) GCompris, TuxType, TuxPaint and TuxMath are awesome learning tools...

**sudo apt-get install gcompris gcompris-sound-en tuxpaint gnucap tuxmath tuxtype**

Gnome Games too...

**sudo apt-get install gnome-games**

It will keep them busy for hours :)

---

### Post by TrakerJon on 2008-08-24
Some late additions...

**Frozen Bubble** is fun but you can loose a couple of hours if you're not careful hahaha

**sudo apt-get install frozen-bubble**

**Dia** is a Linux app similar to Visio

**sudo apt-get install dia**

**Scribus** is a very nice desktop publishing application

**sudo apt-get install scribus**

Last but not least **Inkscape**

**sudo apt-get install inkscape**

---

### Post by TrakerJon on 2008-09-18
When prorgamming in C or C++ you'll need the environment files...

**sudo apt-get install build-essential**

gedit is a very good pre-installed editor 

gcc is already included as well, remember after compiling your program to execute the program by using ./filename

---

### Post by TrakerJon on 2008-11-18
Procedure to enable WPA Wireless in Ubuntu

To update the source list run the following command

sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system 

Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new “keyring”.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

