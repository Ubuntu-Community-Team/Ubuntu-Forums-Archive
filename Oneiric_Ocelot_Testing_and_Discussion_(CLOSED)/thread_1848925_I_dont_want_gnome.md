---
title: "I dont want gnome"
date: 2011-09-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-09-23
Hey Friends
I have installed ubuntu-desktop in my xubuntu 11.10 . now i dont want any type of ubuntu desktop application , i mean what are the application and everything i got by installing ubuntu-desktop in my system , i wanna remove of all of them . is there any way to do it ? 

thanks in advance

---

### Post by philinux on 2011-09-23
> **raja.genupula said:**
> Hey Friends
I have installed ubuntu-desktop in my xubuntu 11.10 . now i dont want any type of ubuntu desktop application , i mean what are the application and everything i got by installing ubuntu-desktop in my system , i wanna remove of all of them . is there any way to do it ? 

thanks in advance

There is a way but this guide is only applicable to 11.04.

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by ronacc on 2011-09-23
open synaptic and rt click on ubuntu-desktop , select properties then dependencies and you will see all the packages it installed , then uninstall any not needed by xubuntu , just uninstalling the metapackage ubuntu-desktop will not do it .

---

### Post by raja.genupula on 2011-09-23
Hey philinux , thanks for quickly picking up my thread . But i already googled for answer to this issue and tried that . no success . 

is there any other way to do this ? 

thanks in advance .

---

### Post by raja.genupula on 2011-09-23
> **ronacc said:**
> open synaptic and rt click on ubuntu-desktop , select properties then dependencies and you will see all the packages it installed , then uninstall any not needed by xubuntu , just uninstalling the metapackage ubuntu-desktop will not do it .

Hey ronacc
        i am seeing a large list , removing all those things sounds  like a large time eating and complex job . is there any other way to make this ? 

thanks in advance

---

### Post by philinux on 2011-09-23
> **raja.genupula said:**
> Hey ronacc
        i am seeing a large list , removing all those things sounds  like a large time eating and complex job . is there any other way to make this ? 

thanks in advance

Quick way is to reinstall xubuntu especially if you have home on it's own partition.

---

### Post by ronacc on 2011-09-23
sadly there is no easy way , philinux is right the fastest way is reinstall and leave out ubuntu-desktop .

---

### Post by drawkcab on 2011-09-23
> **ronacc said:**
> sadly there is no easy way , philinux is right the fastest way is reinstall and leave out ubuntu-desktop .

Nowadays the graphical installer will let you install over your current installation while preserving /home and many installed applications.

---

### Post by seeker5528 on 2011-09-23
After the ubuntu-desktop metapackage in uninstalled do the things it pulled in show in the package list when you have 'Status' selected on the lower left, then click on 'Installed (auto removable)'?

Later, Seeker

---

### Post by ronacc on 2011-09-23
> **drawkcab said:**
> Nowadays the graphical installer will let you install over your current installation while preserving /home and many installed applications.

he wants to get rid of packages not preserve them . and preserving home is what philinux suggested .

---

### Post by raja.genupula on 2011-09-23
> **philinux said:**
> Quick way is to reinstall xubuntu especially if you have home on it's own partition.

Hi

    I can do it,but everything i need to re-configure.
    I can't take backup.

---

### Post by mocoloco on 2011-09-23
Actually this is cake because our good friend psychocats has gone through and listed them out for us.  check out
[http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by raja.genupula on 2011-09-23
> **mocoloco said:**
> Actually this is cake because our good friend psychocats has gone through and listed them out for us.  check out
[http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce")

Hey
      Man I am using 11.10 not 11.04 and that trick i had already tried .Its give up . not worked for me .Thanks for picking up my thread .

---

### Post by cariboo on 2011-09-23
If you don't want to backup your configuration files, and do a fresh install, and you don't want to follow the advice already given in this thread, you can do an inplace installation. Boot from the xubuntu live CD and select the installation option, once you get to the partitioning section, select manual partitioning, and mark which partition to use, **Do not mark the partition for formatting**, then just continue on like it was a regular installation.

Also please don't create another post thanking me for my input, just let us know if my suggestion was successful.

---

### Post by raja.genupula on 2011-09-23
Hi
    Its not going to success , because by doing that also gnome files going to be exist and this new installation will be done at same partition . I mean old installation and new installation both are going to exist in same partition with different boot locations .thanks for picking up my thread .

---

### Post by raja.genupula on 2011-09-23
Thanks to all .I think its not going to be possible . so I am closing this , but if you got any information please post here . 

once again thanks to all . 
raja

---

### Post by cariboo on 2011-09-23
> **raja.genupula said:**
> Hi
    Its not going to success , because by doing that also gnome files going to be exist and this new installation will be done at same partition . I mean old installation and new installation both are going to exist in same partition with different boot locations .thanks for picking up my thread .

When doing a fresh inplace install. it overwrites all the old installation files. Please quit assuming we are giving you bad advice, and at least try some of the solutions given.

---

### Post by seeker5528 on 2011-09-23
My command-fu isn't quite good enough to get a list you could just copy and paste, but what about doing.....

```
apt-cache depends ubuntu-desktop > ubuntu.txt && apt-cache depends xubuntu-desktop > xubuntu.txt && diff -y ubuntu.txt xubuntu.txt | grep '<' | less
```

Does that get it close enough to make the rest of the manual labor tolerable and a complete enough listing that you don't mind leaving whatever additional packages ubuntu-desktop may have pulled in on your system? Some of that additional stuff would probably then show in Synaptic in the list of installed stuff that is auto removable.

you might first have to install apt-cache and type the command ```
apt-cache gencaches
```

Later, Seeker

---

### Post by dava4444 on 2011-09-23
to OP

well sometimes.. you may have to cut it as a loss.

get your files on usb. then do a fresh is my advice.

---

### Post by Is Mise on 2011-09-23
Or how about this to do it all in one line using apt-cache and apt-get:

```
(apt-cache depends ubuntu-desktop; apt-cache depends xubuntu-desktop; apt-cache depends xubuntu-desktop) | cut -d ':' -f 2 | tr -d [:blank:] | sort | uniq -u | tr [:space:] ' ' | xargs sudo apt-get purge 
```

---

### Post by raja.genupula on 2011-09-24
> **dava4444 said:**
> to OP

well sometimes.. you may have to cut it as a loss.

get your files on usb. then do a fresh is my advice.

Sorry man , i cant go for backup . 
i will try the remaining things 

thanks for picking this .

---

### Post by raja.genupula on 2011-09-24
Submitted two posts as same , please delete this

---

### Post by raja.genupula on 2011-09-24
> **seeker5528 said:**
> My command-fu isn't quite good enough to get a list you could just copy and paste, but what about doing.....

```
apt-cache depends ubuntu-desktop > ubuntu.txt && apt-cache depends xubuntu-desktop > xubuntu.txt && diff -y ubuntu.txt xubuntu.txt | grep '<' | less
```

Does that get it close enough to make the rest of the manual labor tolerable and a complete enough listing that you don't mind leaving whatever additional packages ubuntu-desktop may have pulled in on your system? Some of that additional stuff would probably then show in Synaptic in the list of installed stuff that is auto removable.

you might first have to install apt-cache and type the command ```
apt-cache gencaches
```

Later, Seeker

What i can delete from the list ? Dependencies or Recommended or all .

---

### Post by raja.genupula on 2011-09-24
> **Is Mise said:**
> Or how about this to do it all in one line using apt-cache and apt-get:

```
(apt-cache depends ubuntu-desktop; apt-cache depends xubuntu-desktop; apt-cache depends xubuntu-desktop) | cut -d ':' -f 2 | tr -d [:blank:] | sort | uniq -u | tr [:space:] ' ' | xargs sudo apt-get purge 
```

Hi man your code gonna work but small problem its not waiting for my response & automatically aborting , i will bold that area , just look at there .

```
assassin@raju-xubuntu:~$ (apt-cache depends ubuntu-desktop; apt-cache depends xubuntu-desktop; apt-cache depends xubuntu-desktop) | cut -d ':' -f 2 | tr -d [:blank:] | sort | uniq -u | tr [:space:] ' ' | xargs sudo apt-get purge
[sudo] password for assassin: 
Sorry, try again.
[sudo] password for assassin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-nettool is not installed, so not removed
Package ubuntu-desktop is not installed, so not removed
Package ubuntuone-client-gnome is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libmono-addins-gui0.2-cil libstlport4.6ldbl libpth20 libunity5 libraptor2-0
  libgnome-media-profiles-3.0-0 libgdata1.7-cil librdf0 libcamel-1.2-28
  libdbus-glib1.0-cil libgconf2.0-cil libhyphen0 libmono-zeroconf1.0-cil
  libgkeyfile1.0-cil libgpod4 librasqal3 libgtk-sharp-beans-cil duplicity
  liblaunchpad-integration1.0-cil libmono-addins0.2-cil libebook1.2-11
  uno-libs3 libmythes-1.2-0 python-speechd liblouis2 libtaglib2.0-cil
  python-louis libedataserver1.2-14 libappindicator0.1-cil media-player-info
  libtextcat0 libgpod-common libgudev1.0-cil ure libtextcat-data libyajl1
  libgpgme11 python-wnck libmhash2 adium-theme-ubuntu libdbus1.0-cil
  xfonts-mathml liblouis-data librsync1 libneon27-gnutls libnotify0.4-cil
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  at-spi2-core* banshee* banshee-extension-soundmenu*
  banshee-extension-ubuntuonemusicstore* baobab* bluez-gstreamer*
  branding-ubuntu* brasero* checkbox-gtk* deja-dup* empathy* eog*
  example-content* gbrainy* gedit* ginn* gnome-bluetooth*
  gnome-control-center* gnome-disk-utility* gnome-media* gnome-menus*
  gnome-orca* gnome-power-manager* gnome-screensaver* gnome-screenshot*
  gnome-search-tool* gnome-session* gnome-session-canberra* gnome-system-log*
  gnome-system-monitor* gnome-terminal* gnome-user-guide* gnome-user-share*
  gstreamer0.10-pulseaudio* gwibber* ibus-gtk3* indicator-datetime*
  indicator-power* indicator-sound* indicator-sound-gtk2*
  launchpad-integration* libatk-adaptor* libcanberra-pulse* libgail-3-common*
  libgail-common* libreoffice-base-core* libreoffice-calc* libreoffice-common*
  libreoffice-core* libreoffice-draw* libreoffice-emailmerge*
  libreoffice-gnome* libreoffice-gtk* libreoffice-help-en-us*
  libreoffice-impress* libreoffice-math* libreoffice-style-human*
  libreoffice-writer* libsdl-image1.2* libsdl1.2debian*
  libsdl1.2debian-pulseaudio* libwmf0.2-7-gtk* mousetweaks* nautilus*
  nautilus-sendto* nautilus-share* notify-osd* overlay-scrollbar*
  plymouth-theme-ubuntu-logo* pulseaudio* pulseaudio-esound-compat*
  pulseaudio-module-bluetooth* pulseaudio-module-gconf* pulseaudio-module-x11*
  python-uno* qt-at-spi* seahorse* shotwell* sni-qt* ssh-askpass-gnome*
  telepathy-idle* thunderbird-gnome-support* tomboy* totem* totem-mozilla*
  totem-plugins* ubuntu-artwork* ubuntu-docs* ubuntu-sounds*
  ubuntuone-control-panel-gtk* unity* unity-2d* vino* vlc* xdiagnose* yelp*
0 upgraded, 0 newly installed, 96 to remove and 2 not upgraded.
[B]After this operation, 371 MB disk space will be freed.
Do you want to continue [Y/n]? Abort.[/B]
assassin@raju-xubuntu:~$ 

```

there i am trying to enter yes but automatically its aborted , tried many times . but same thing repeating .

---

### Post by VinDSL on 2011-09-24
> **cariboo907 said:**
> Also please don't create another post thanking me for my input [...]
The more beans the better, yes?

[http://ubuntuforums.org/showthread.php?t=1838278](http://ubuntuforums.org/showthread.php?t=1838278)

---

### Post by mc4man on 2011-09-24
> there i am trying to enter yes but automatically its aborted , tried many times . but same thing repeating try adding a -y option to the apt-get section of your command
 ...... | xargs sudo apt-get -y  purge

---

### Post by raja.genupula on 2011-09-24
> **VinDSL said:**
> The more beans the better, yes?

[http://ubuntuforums.org/showthread.php?t=1838278](http://ubuntuforums.org/showthread.php?t=1838278)

Excuse me, what do you mean by this ? you mean I am trying to make beans ? 

what do you know about me ? Who are you to say this ? 

Ok,I am not a expert or programmer or what ever as you ? 

what is my thread and what is your post ? this is showing who are trying to make more beans & trying to get impression.I am not like you .

is there any relation between yours and mine posts ?

if you know the answer post here , other wise simply watch it.

thats it .

---

### Post by VinDSL on 2011-09-24
> **raja.genupula said:**
> if you know the answer post here [...]
The answer to that question lays in YOUR hands.

Let's just drop it, okay?!?!?  ;)

Have fun...

---

### Post by raja.genupula on 2011-09-24
> **vindsl said:**
> the answer to that question lays in your hands.

Let's just drop it, okay?!?!?  ;)

have fun...

who are you man ? You are not posting anything which is helpful to solve this thread and simply throwing mistake on me .why are you doing like this ?

---

### Post by raja.genupula on 2011-09-24
> **mc4man said:**
> try adding a -y option to the apt-get section of your command
 ...... | xargs sudo apt-get -y  purge

@mc4man , @Mise

thank you very much friends . i have solved my issue with that script .really thank you very much . 

Thanks to all for helping me on this issue .

---

