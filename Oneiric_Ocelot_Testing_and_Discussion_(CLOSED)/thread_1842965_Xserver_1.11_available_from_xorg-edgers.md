---
title: "Xserver 1.11 available from xorg-edgers"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-12
First of all, a word of warning, if upgrading.
If you do not want to end up into a console (recovery mode) with no graphics at all,
 be sure what you are doing.

You have to successfully upgrade xserver packages, correct graphics driver and appropriate input drivers before rebooting.

For the time being, this is not possible using proprietary drivers.
With Nvidia-current patched to depend on xorg-video-abi-11, the xserver 1.11 seems to work well after all, at least with Gnome DE (like gnome-shell).
But because the driver does not officially support this, you need to add these lines into the file /etc/X11/xorg.conf

> 
Section "ServerFlags"
    Option         "IgnoreABI" "True"
EndSection


Xserver 1.11 and nvidia-current (video abi 11) can be downloaded from xorg-edgers PPA.

---

### Post by lucazade on 2011-09-12
have you already tried it? noticed any improvement or differences?

---

### Post by paul_in_london on 2011-09-12
> **Harry33 said:**
> First of all, a word of warning, if upgrading.
If you do not want to end up into a console (recovery mode) with no graphics at all,
 be sure what you are doing.

You have to successfully upgrade xserver packages, correct graphics driver and appropriate input drivers before rebooting.

For the time being, this is not possible using proprietary drivers.

+1

Box 1 (32 bit) - without proprietary drivers, xorg-edgers ppa enabled is ok with all updates applied.

Box 2 (64 bit) - 1x32 bit install, 1x64 bit install, both with nvidia-current. No packages held back, but all is "fscked up"! Can boot ok in recovery mode, otherwise system just hangs. Purged xorg-edgers temporarily on the 32 bit install and all is back to normal. Will see what edgers updates come along in due course. I forgot that you mentioned something in another post somewhere about ABI breakage with Xserver 1.11!

---

### Post by paul_in_london on 2011-09-12
@Harry33 - Hello again. Forgot to ask if you'd tried it using an xorg.conf with **Option     "ignoreABI" " on**"? I know I don't *need* an xorg.conf any more, but I'm using one for a couple of other reasons - one being to stop my display going to sleep :)

---

### Post by Harry33 on 2011-09-12
Proprietary drivers really do not work with xserver 1.11 final.
With xserver 1.11 rc1 you could set "IgnoreABI" "True" in the /etc/X11/xorg.conf,
but the data structure of the server did change when the final version was released.

This is what Nvidia's Aaron Plattner said (29th August 2011):
> Unfortunately, there was a change to a data structure without a corresponding change to the extension module ABI version that breaks GLX. It's not exactly clear whether this structure counts as part of the extension ABI, so I need to get to the bottom of that before a driver with official xserver 1.11 support can be released. It may be that we need to skip xserver 1.11.0 if my hunch is correct and this is a bug in the X server.

---

### Post by paul_in_london on 2011-09-12
> **Harry33 said:**
> Proprietary drivers really do not work with xserver 1.11 final.
With xserver 1.11 rc1 you could set "IgnoreABI" "True" in the /etc/X11/xorg.conf,
but the data structure of the server did change when the final version was released.

This is what Nvidia's Aaron Plattner said (29th August 2011):
Unfortunately, there was a change to a data structure without a corresponding change to the extension module ABI version that breaks GLX. It's not exactly clear whether this structure counts as part of the extension ABI, so I need to get to the bottom of that before a driver with official xserver 1.11 support can be released. It may be that we need to skip xserver 1.11.0 if my hunch is correct and this is a bug in the X server.

Ah, ok. Thanks for that info Harry. Yes, sorry I forgot the correct syntax was  "IgnoreABI" "**True**". I thought I'd try it on my 64 bit install anyway, just to see what happened. No joy though. Oh well. I do actually have some xserver-related packages held back on that install compared with the 32 bit one (none held back there with xorg-edgers enabled so I was somehow more minimalist when I set that one up and/or the 64 bit builds are lagging behind).

---

### Post by paul_in_london on 2011-09-12
Ok, after these updates:

```
paul@oneiric-64:~$ tail -30 /var/log/apt/term.log
Preparing to replace mutter 3.1.90.1+git20110908.fb10910e-0ubuntu1~11.10~ricotz0 (using .../mutter_3.1.90.1+git20110912.7223c4e1-0ubuntu1~11.10~ricotz0_amd64.deb) ...
Unpacking replacement mutter ...
Preparing to replace xserver-xorg-video-all 1:7.6+7ubuntu7 (using .../xserver-xorg-video-all_1%3a7.6+7ubuntu7edgers1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-all ...
Preparing to replace xserver-xorg-input-all 1:7.6+7ubuntu7 (using .../xserver-xorg-input-all_1%3a7.6+7ubuntu7edgers1_amd64.deb) ...
Unpacking replacement xserver-xorg-input-all ...
Preparing to replace xserver-xorg 1:7.6+7ubuntu7 (using .../xserver-xorg_1%3a7.6+7ubuntu7edgers1_amd64.deb) ...
Unpacking replacement xserver-xorg ...
Preparing to replace xorg 1:7.6+7ubuntu7 (using .../xorg_1%3a7.6+7ubuntu7edgers1_amd64.deb) ...
Unpacking replacement xorg ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Setting up libcogl2 (1.7.9+git20110912.9082dd0d-0ubuntu1~11.10~ricotz1) ...
Setting up gir1.2-cogl-1.0 (1.7.9+git20110912.9082dd0d-0ubuntu1~11.10~ricotz1) ...
Setting up libmutter0 (3.1.90.1+git20110912.7223c4e1-0ubuntu1~11.10~ricotz0) ...
Setting up gir1.2-mutter-3.0 (3.1.90.1+git20110912.7223c4e1-0ubuntu1~11.10~ricotz0) ...
Setting up libgtk-3-common (3.1.18-0ubuntu3) ...
Setting up libgtk-3-bin (3.1.18-0ubuntu3) ...
Setting up mutter (3.1.90.1+git20110912.7223c4e1-0ubuntu1~11.10~ricotz0) ...
[COLOR="Red"][B]Setting up xserver-xorg-video-all (1:7.6+7ubuntu7edgers1) ...
Setting up xserver-xorg-input-all (1:7.6+7ubuntu7edgers1) ...
Setting up xserver-xorg (1:7.6+7ubuntu7edgers1) ...
Setting up xorg (1:7.6+7ubuntu7edgers1) ...[/B][/COLOR]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2011-09-12  22:02:29
paul@oneiric-64:~$
```

I can boot to a desktop again on 64 bit with "IgnoreABI" "True" in /etc/X11/xorg.conf.

I still have this situation though:

```
The following packages will be upgraded:

  gnome-shell nvidia-current x11-common xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom 

  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau 

  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion 

  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa 

The following packages are RECOMMENDED but will NOT be installed:

  cups-pk-helper 

29 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Need to get 62.3 MB of archives. After unpacking 160 kB will be freed.

The following packages have unmet dependencies:

  nvidia-current-updates: Depends: xorg-video-abi-10 which is a virtual package.

  xserver-xorg-video-vmware: Depends: xorg-video-abi-10 which is a virtual package.

The following actions will resolve these dependencies:



      Remove the following packages:

1)      libasound2                  

2)      libavahi-client3            

3)      libavahi-common3            

4)      libc6                       

5)      libcairo2                   

6)      libcomerr2                  

7)      libcups2                    

8)      libcurl3                    

9)      libdatrie1                  

10)     libdb5.1                    

11)     libdbus-1-3                 

12)     libexpat1                   

13)     libffi6                     

14)     libfontconfig1              

15)     libfreetype6                

16)     libgcc1                     

17)     libgcrypt11                 

18)     libgnutls26                 

19)     libgpg-error0               

20)     libgssapi-krb5-2            

21)     libice6                     

22)     libidn11                    

23)     libjasper1                  

24)     libjpeg62                   

25)     libk5crypto3                

26)     libkeyutils1                

27)     libkrb5-3                   

28)     libkrb5support0             

29)     libldap-2.4-2               

30)     libnspr4                    

31)     libnspr4-0d                 

32)     libnss3                     

33)     libnss3-1d                  

34)     libpcre3                    

35)     libpixman-1-0               

36)     libpng12-0                  

37)     librtmp0                    

38)     libsasl2-2                  

39)     libselinux1                 

40)     libsm6                      

41)     libsqlite3-0                

42)     libssl1.0.0                 

43)     libtasn1-3                  

44)     libthai0                    

45)     libtiff4                    

46)     libuuid1                    

47)     libx11-6                    

48)     libxau6                     

49)     libxcb-render0              

50)     libxcb-shm0                 

51)     libxcb1                     

52)     libxcomposite1              

53)     libxcursor1                 

54)     libxdamage1                 

55)     libxdmcp6                   

56)     libxext6                    

57)     libxfixes3                  

58)     libxft2                     

59)     libxi6                      

60)     libxinerama1                

61)     libxrandr2                  

62)     libxrender1                 

63)     libxt6                      

64)     nvidia-current-updates      

65)     xserver-xorg-video-vmware   

66)     zlib1g                      

Accept this solution? [Y/n/q/?] q
```

but that's ok. Touch wood, no ill effects so far... :)

---

### Post by paul_in_london on 2011-09-12
Another minor update:

```
paul@oneiric-64:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nvidia-current xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
The following packages will be upgraded:
  gnome-shell mutter-common x11-common
3 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 2,880 kB of archives.
After this operation, 53.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
```

blah blah...

```
Setting up gnome-shell (3.1.91+git20110912.7b407dda-0ubuntu1~11.10~ricotz0) ...
Setting up mutter-common (3.1.90.1+git20110912.7223c4e1-0ubuntu1~11.10~ricotz0) ...
Setting up x11-common (1:7.6+7ubuntu7edgers1) ...
localepurge: Disk space freed in /usr/share/locale: 6404 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 6404 KiB

paul@oneiric-64:~$
```

---

### Post by paul_in_london on 2011-09-12
Checked for updates again and I could live with what synaptic wanted to do:

```
[COLOR="Red"][B]nvidia-current-updates will be removed
xserver-xorg-video-vmware will be removed[/B][/COLOR]
nvidia-current (version 285.03-0ubuntu1~edgers~oneiric2) will be upgraded to version 285.03-0ubuntu1~edgers~oneiric3
xserver-xorg-core (version 2:1.10.4-1ubuntu1) will be upgraded to version 2:1.11.0+git20110912.0caeef61-0ubuntu0sarvatt
xserver-xorg-input-evdev (version 1:2.6.0-1ubuntu13) will be upgraded to version 1:2.6.0+git20110912.070f30e0-0ubuntu0sarvatt
xserver-xorg-input-mouse (version 1:1.7.1+git20110725.93ebeecd-0ubuntu0sarvatt) will be upgraded to version 1:1.7.1+git20110912.b6565197-0ubuntu0sarvatt
xserver-xorg-input-synaptics (version 1.4.1-1ubuntu1) will be upgraded to version 1.5.99+git20110912.bc789cc7-0ubuntu0sarvatt
xserver-xorg-input-vmmouse (version 1:12.7.0+git20110624.fd140bfb-0ubuntu0sarvatt) will be upgraded to version 1:12.7.0+git20110912.fd140bfb-0ubuntu0sarvatt
xserver-xorg-input-wacom (version 1:0.11.0-0ubuntu1) will be upgraded to version 1:0.11.0-0ubuntu1sarvatt1
xserver-xorg-video-ati (version 1:6.14.99+git20110819.64f237a4-0ubuntu0sarvatt) will be upgraded to version 1:6.14.99+git20110912.64f237a4-0ubuntu0sarvatt
xserver-xorg-video-cirrus (version 1:1.3.2+git20110526.e4f80ffd-0ubuntu0sarvatt) will be upgraded to version 1:1.3.2+git20110912.e4f80ffd-0ubuntu0sarvatt
xserver-xorg-video-fbdev (version 1:0.4.2+git20110526.a8721393-0ubuntu0sarvatt) will be upgraded to version 1:0.4.2+git20110912.a8721393-0ubuntu0sarvatt
xserver-xorg-video-intel (version 2:2.16.0+git20110908.afdb8aa8-0ubuntu0sarvatt) will be upgraded to version 2:2.16.0+git20110912.03a7fc16-0ubuntu0sarvatt
xserver-xorg-video-mach64 (version 6.9.0+git20110526.ef55d1f1-0ubuntu0sarvatt) will be upgraded to version 6.9.0+git20110912.ef55d1f1-0ubuntu0sarvatt
xserver-xorg-video-mga (version 1:1.4.13.dfsg-3build1) will be upgraded to version 1:1.4.13.dsfg+git20110912.c083bf0a-0ubuntu0sarvatt
xserver-xorg-video-neomagic (version 1:1.2.5+git20110526.a9d69f6d-0ubuntu0sarvatt) will be upgraded to version 1:1.2.5+git20110912.a9d69f6d-0ubuntu0sarvatt
xserver-xorg-video-nouveau (version 1:0.0.16+git20110823.169512fb-0ubuntu0sarvatt) will be upgraded to version 1:0.0.16+git20110912.169512fb-0ubuntu0sarvatt
xserver-xorg-video-openchrome (version 1:0.2.904+svn920-1) will be upgraded to version 1:0.2.904+svn920-1ubuntu0sarvatt
xserver-xorg-video-qxl (version 0.0.14-1) will be upgraded to version 0.0.14-1ubuntu0
xserver-xorg-video-r128 (version 6.8.1+git20110526.3de85360-0ubuntu0sarvatt) will be upgraded to version 6.8.1+git20110912.3de85360-0ubuntu0sarvatt
xserver-xorg-video-radeon (version 1:6.14.99+git20110819.64f237a4-0ubuntu0sarvatt) will be upgraded to version 1:6.14.99+git20110912.64f237a4-0ubuntu0sarvatt
xserver-xorg-video-s3 (version 1:0.6.3+git20110526.381ace93-0ubuntu0sarvatt) will be upgraded to version 1:0.6.3+git20110912.381ace93-0ubuntu0sarvatt
xserver-xorg-video-savage (version 1:2.3.2+git20110526.d177ae0b-0ubuntu0sarvatt) will be upgraded to version 1:2.3.2+git20110912.d177ae0b-0ubuntu0sarvatt
xserver-xorg-video-siliconmotion (version 1:1.7.5+git20110526.087226bf-0ubuntu0sarvatt) will be upgraded to version 1:1.7.5+git20110912.087226bf-0ubuntu0sarvatt
xserver-xorg-video-sis (version 1:0.10.3+git20110608.94f23a56-0ubuntu0sarvatt) will be upgraded to version 1:0.10.3+git20110913.94f23a56+really0.10.3-0ubuntu0sarvatt
xserver-xorg-video-sisusb (version 1:0.9.4+git20110608.241dd519-0ubuntu0sarvatt) will be upgraded to version 1:0.9.4+git20110912.241dd519-0ubuntu0sarvatt
xserver-xorg-video-tdfx (version 1:1.4.3+git20110526.0c4ffbec-0ubuntu0sarvatt) will be upgraded to version 1:1.4.3+git20110912.0c4ffbec-0ubuntu0sarvatt
xserver-xorg-video-trident (version 1:1.3.4+git20110526.de79bbea-0ubuntu0sarvatt) will be upgraded to version 1:1.3.4+git20110912.de79bbea-0ubuntu0sarvatt
xserver-xorg-video-vesa (version 1:2.3.0+git20110526.0b02c685-0ubuntu0sarvatt) will be upgraded to version 1:2.3.0+git20110912.0b02c685-0ubuntu0sarvatt
```

Installed nvidia-current-updates before I realised that my card isn't quite recent enough to support vdpau. Don't use vmware so didn't mind about xserver-xorg-video-vmware being removed. Not sure if that package is (also) needed for virtualbox, but I'm not actually using virtualbox in this particular install.

Still ok after a reboot btw. Forgot to say that.

---

### Post by Sarvatt on 2011-09-12
nvidia-current-updates just pulls nvidia-current from ppa:ubuntu-x-swat/x-updates, there is no need to have it installed when using xorg-edgers because beta nvidia updates go in here while stable nvidia release series go in x-updates.

---

### Post by paul_in_london on 2011-09-12
> **Sarvatt said:**
> nvidia-current-updates just pulls nvidia-current from ppa:ubuntu-x-swat/x-updates, there is no need to have it installed when using xorg-edgers because beta nvidia updates go in here while stable nvidia release series go in x-updates.

Thanks for that - I'd never installed nvidia-current-updates before (only nvidia-current) until just a few days ago actually. I got the impression somehow from something I read that I should install it along with libvdpau1 to try and get vdpau working, but it sounds as if all I would need is libvdpau1 - if my nvidia card supported vdpau that is!

---

### Post by paul_in_london on 2011-09-12
Ok, off-topic I know but just for <snip> and giggles a couple of screenshots. This box is nothing special and my graphics card can't do vdpau to help me out with hardware acceleration, but the performance/load isn't too bad.

Btw, for any UK tv junkies tvcatchup.com is worth checking out. Totally legit:

[http://forums.tvcatchup.com/forum.php](http://forums.tvcatchup.com/forum.php).

It's a godsend for me because I can't use conventional tv for reasons I won't bore you with.

---

### Post by VinDSL on 2011-09-13
> **Harry33 said:**
> First of all, a word of warning, if upgrading. If you do not want to end up into a console (recovery mode) with no graphics at all, be sure what you are doing.[...]
Thanks, Harry!

Not being one to pass up a chance to crash Oneiric, I took the challenge, upgraded and rebooted.

Of course, you were correct, and I "ended up into a console (recovery mode) with no graphics at all."

Fine!  :D

I took the easy way out, and purged the xorg-edgers PPA.

Oh, well, it was fun while it lasted.  I'll try again later...

---

### Post by paul_in_london on 2011-09-13
> **VinDSL said:**
> Thanks, Harry!

Not being one to pass up a chance to crash Oneiric, I took the challenge, upgraded and rebooted.

Of course, you were correct, and I "ended up into a console (recovery mode) with no graphics at all."

Fine!  :D

I took the easy way out, and purged the xorg-edgers PPA.

Oh, well, it was fun while it lasted.  I'll try again later...

Did you try it with "IgnoreABI" "True" in /etc/X11/xorg.conf before you purged the xorg-edgers ppa? At work right now so can't test if that still works with proprietary graphics - nvidia in my case. Since my previous post last night there may have been some more updates from that ppa so who knows?!

---

### Post by MacUntu on 2011-09-13
Is there anything special about that release (some fancy features to test)?

---

### Post by VinDSL on 2011-09-13
> **MacUntu said:**
> Is there anything special about that release (some fancy features to test)?
Nothing major AFAIK...

Looks mostly like bug fixes and minor improvements:  [http://thread.gmane.org/gmane.comp.freedesktop.xorg.announce/1459](http://thread.gmane.org/gmane.comp.freedesktop.xorg.announce/1459)

---

### Post by MacUntu on 2011-09-13
What bugs? X has no bugs. :D

---

### Post by lucazade on 2011-09-13
> **MacUntu said:**
> What bugs? X has no bugs. :D

Epic lol!

---

### Post by Harry33 on 2011-09-13
> **paul_in_london said:**
> Did you try it with "IgnoreABI" "True" in /etc/X11/xorg.conf before you purged the xorg-edgers ppa? At work right now so can't test if that still works with proprietary graphics - nvidia in my case. Since my previous post last night there may have been some more updates from that ppa so who knows?!

Using "IgnoreABI" "True" in the file /etc/X11/xorg.conf will only force nvidia module to load, but the module will not support this ABI anyway.
You will see a number of strange rendering issues if you try this. At least with KDE.

---

### Post by paul_in_london on 2011-09-13
> **Harry33 said:**
> Using "IgnoreABI" "True" in the file /etc/X11/xorg.conf will only force nvidia module to load, but the module will not support this ABI anyway.
You will see a number of strange rendering issues if you try this.

Hi Harry,

Everything still seems normal actually. I haven't noticed any strange rendering issues - on the other hand I'm not very observant! :lolflag:
The only update from xorg-edgers that I remember seeing so far tonight was nvidia-current:

```
paul@oneiric-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 285.03-0ubuntu1~edgers~oneiric4
  Candidate: 285.03-0ubuntu1~edgers~oneiric4
  Version table:
 *** 285.03-0ubuntu1~edgers~oneiric4 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     280.13-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/restricted amd64 Packages
paul@oneiric-64:~$
```

---

### Post by Harry33 on 2011-09-14
> **paul_in_london said:**
> Hi Harry,

Everything still seems normal actually. I haven't noticed any strange rendering issues - on the other hand I'm not very observant! :lolflag:
...


True, perhaps with Gnome (at least gnome-shell) it is not so bad after all.

---

### Post by VinDSL on 2011-09-14
Hrm...

I got home tonight and had 109 upgrades waiting.  Why not install the xorg-edgers PPA at the same time, yes?  :D

This time, I specified the ol' "IgnoreABI" "True" trick before rebooting.

Still... no joy!

Yes, the desktop came up, but the only thing that was rendered was the wallpaper and Conky.  Otherwise, Unity 3D was as barren as a lunar landscape.

So, I'll try it again tomorrow...  ;)

---

### Post by Harry33 on 2011-09-14
> **VinDSL said:**
> Hrm...

I got home tonight and had 109 upgrades waiting.  Why not install the xorg-edgers PPA at the same time, yes?  :D

This time, I specified the ol' "IgnoreABI" "True" trick before rebooting.

Still... no joy!

Yes, the desktop came up, but the only thing that was rendered was the wallpaper and Conky.  Otherwise, Unity 3D was as barren as a lunar landscape.

So, I'll try it again tomorrow...  ;)

Well did all this happen after installing only nvidia-current and xserver from edgers PPA?
Or was this due to some of the 109 updates?

---

### Post by VinDSL on 2011-09-14
> **Harry33 said:**
> Well did all this happen after installing only nvidia-current and xserver from edgers PPA?
Or was this due to some of the 109 updates?
Non-xorg-edgers updates are working fine. If I purge* the xorg-edgers PPA, my system runs great. (*PPA Purge)

A few hours after I posted the message above, I reinstalled the xorg-edgers PPA, but did not do an update.  Everything was still fine, of course.

Then, I performed all the edgers updates, except for xserver.  But, I ran into dependency problems.  So, I purged the xorg-edgers PPA again.

Finally, I reinstalled the xorg-edgers PPA, and tried to simply update nvidia-current to 285.03.  When I did this, Synaptic said it was going to remove 30-40 packages, including unity-desktop.  LoL!

So, I purged the xorg-edgers PPA again, and that's where it sits, at the moment - no xorg-edgers repo in my lists.

It seems that the ABI bump has been extended across all xorg-edgers packages now...

---

### Post by Harry33 on 2011-09-14
> **VinDSL said:**
> Non-xorg-edgers updates are working fine. If I purge* the xorg-edgers PPA, my system runs great. (*PPA Purge)

A few hours after I posted the message above, I reinstalled the xorg-edgers PPA, but did not do an update.  Everything was still fine, of course.

Then, I performed all the edgers updates, except for xserver.  But, I ran into dependency problems.  So, I purged the xorg-edgers PPA again.

Finally, I reinstalled the xorg-edgers PPA, and tried to simply update nvidia-current to 285.03.  When I did this, Synaptic said it was going to remove 30-40 packages, including unity-desktop.  LoL!

So, I purged the xorg-edgers PPA again, and that's where it sits, at the moment - no xorg-edgers repo in my lists.

It seems that the ABI bump has been extended across all xorg-edgers packages now...

All the drivers (both input and video) of the PPA xorg-edgers have been upgraded to be compatible with the ABI bumb of xserver 1.11.
This is of course necessary for them to be installable into a new xserver environment.

However, the package xorg (7.6+7ubuntu7edgers1) is not generally needed (wmware dropped from a meta package). In addition to that, drm and mesa packages can be upgraded separately. There is no need to do so, however, if proprietary drivers are used).

---

### Post by VinDSL on 2011-09-15
Interesting!

I saw that xorg-edgers updated their mesa package today, so I installed the PPA and tried again.

No soap with Unity, but...

I logged out of Unity, logged into GS, and GS is working just fine (as I type).

So, maybe I'll play around with GS for a while.  Never paid much attention to it, until now...  :D

---

### Post by xeizo on 2011-09-15
Kubuntu works fine using IgnoreABI on Xorg edgers and Nvidia 285.03  ...

---

### Post by VinDSL on 2011-09-15
> **xeizo said:**
> Kubuntu works fine using IgnoreABI on Xorg edgers and Nvidia 285.03  ...
Hrm... This is bizarre!

I logged into Gnome-shell for several hours.  Everything worked fine.

Then, I tried Unity 2D.  No problems.  Looked gorgeous, actually.

Then, "Classic".  100% functional.

Now, I'm logged into E17 Enlightenment, and it's working like a champ too.

The only DE that isn't working with Xserver 1.11 is Unity 3D.  LoL!

I'm gonna have to think about this for a while...

---

### Post by VinDSL on 2011-09-15
Well, it's a new day, and I was greeted with 46 updates at boot - all of them major players.

I was hoping there would be some joy, but... same situation.  Everything works great, except Unity 3D.

Doing a little forensics, it appears that I'm getting a seg fault in the *unity-panel-service*.

Upon further investigation, *g_sprawl_sync()* is failing to get a child, and throwing a *geis_init* error.

So, I judge the reason Xserver 1.11 is not working in conjunction with Unity 3D is due to a conflict with Compiz.

Okay, time for my first pot of coffee... BBL  :D

---

### Post by Sarvatt on 2011-09-16
> **VinDSL said:**
> Well, it's a new day, and I was greeted with 46 updates at boot - all of them major players.

I was hoping there would be some joy, but... same situation.  Everything works great, except Unity 3D.

Doing a little forensics, it appears that I'm getting a seg fault in the *unity-panel-service*.

Upon further investigation, *g_sprawl_sync()* is failing to get a child, and throwing a *geis_init* error.

So, I judge the reason Xserver 1.11 is not working in conjunction with Unity 3D is due to a conflict with Compiz.

Okay, time for my first pot of coffee... BBL  :D

```
sudo apt-get install ubuntu-desktop^
```
That offer any packages?

---

### Post by VinDSL on 2011-09-17
> **Sarvatt said:**
> ```
sudo apt-get install ubuntu-desktop
```
That offer any packages?
Thank you, but no.  ;)

This is encouraging, though:

SOURCE:  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

> 
== New in xserver-xorg-video-intel - **[COLOR="Red"]2011/08/16[/COLOR]** ==

Due to the number of complaints about **[COLOR="Blue"]problems with unity[/COLOR]**, SNA is now disabled in this PPA.


They're starting to recognize that Unity has issues with Xserver 1.11.

Maybe they're come up with a fix for nVidia users too...

I think I'll try the xorg-edgers PPA again, in a few minutes.

What do they say about ppl that do the same thing, over n' over again, expecting a different result?!?!?  LoL!  :D

---

### Post by VinDSL on 2011-09-17
I tried Xserver 1.11 again, and still no joy in Unity.

I'm curious if anyone else has had luck running Xserver 1.11 in Unity, with an nVidia GPU.

Here is how I've been installing & uninstall Xserver 1.11:


```

Source (important - read this page before installing):
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

Install xorg-edgers PPA:
sudo add-apt-repository ppa:xorg-edgers/ppa

Update:
 sudo apt-get update

Upgrade:
 sudo apt-get upgrade

Wash, rinse, and restyle (if Xserver fails):
sudo ppa-purge xorg-edger

```

I've installed & uninstalled (the entire) Xserver 1.11 package so many times, it's like shaving, or brushing my teeth. LoL!  :D

---

### Post by Sarvatt on 2011-09-18
> **VinDSL said:**
> I tried Xserver 1.11 again, and still no joy in Unity.

I'm curious if anyone else has had luck running Xserver 1.11 in Unity, with an nVidia GPU.

Here is how I've been installing & uninstall Xserver 1.11:


```

Source (important - read this page before installing):
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

Install xorg-edgers PPA:
sudo add-apt-repository ppa:xorg-edgers/ppa

Update:
 sudo apt-get update

Upgrade:
 sudo apt-get upgrade

Wash, rinse, and restyle (if Xserver fails):
sudo ppa-purge xorg-edger

```

I've installed & uninstalled (the entire) Xserver 1.11 package so many times, it's like shaving, or brushing my teeth. LoL!  :D

Thats odd, the ^ didn't survive the quoting of sudo apt-get install ubuntu-desktop^, I'll just assumed you pasted what I put and it didn't work :) Do you get a backtrace in /var/log/Xorg.0.log when it crashes? It will be in /var/log/Xorg.0.log.old after. There is another problem with the nvidia packages [1] that I'll fix via an xserver 1.11 upload on monday, I suggest trying again monday evening EST if so.

[1] [http://lists.x.org/archives/xorg-devel/2011-September/025062.html](http://lists.x.org/archives/xorg-devel/2011-September/025062.html)

---

### Post by Sarvatt on 2011-09-18
> **Sarvatt said:**
> Thats odd, the ^ didn't survive the quoting of sudo apt-get install ubuntu-desktop^, I'll just assumed you pasted what I put and it didn't work :) Do you get a backtrace in /var/log/Xorg.0.log when it crashes? It will be in /var/log/Xorg.0.log.old after. There is another problem with the nvidia packages [1] that I'll fix via an xserver 1.11 upload on monday, I suggest trying again monday evening EST if so.

[1] [http://lists.x.org/archives/xorg-devel/2011-September/025062.html](http://lists.x.org/archives/xorg-devel/2011-September/025062.html)

Scratch that, unity definitely isn't working with 285.03.

---

### Post by VinDSL on 2011-09-18
> **Sarvatt said:**
> I'll just assumed you pasted what I put and it didn't work :)
Yes, sorry, for not being more clear!  

I've tried installing ubuntu-desktop many times, before and after your recommendation.  I say "tried" because apt-get always refuses to reinstall it, because I'm already running the latest version.

Accordingly, I've washed, rinsed, and reinstalled ubuntu-desktop several times (before and after installing the Xserver 1.11 package) with no joy.

I *know* what the problem is (at least, in my case).  I'm getting a seg fault in the unity-panel-service when logging into a Unity 3D session.  All other installed DEs are working fine with Xserver 1.11.

My Unity 3D desktop starts to load, but before it's fully populated unity-panel-service crashes.  g_sprawl_sync() fails to get a child, and throws a geis_init error.  So, I end up with a pretty wallpaper and Conky - no menus, no panels, no nothing...  

The only shortcut that works in Unity 3D is alt-ctrl-delete, but it allows me to logout gracefully.  Then, I login to GS, Unity 2D, E17, Classic, or whatever.  When I grow tired of these DEs, I purge the xorg-edgers PPA, reboot, and Unity 3D starts normally, like nothing happened.

Everything points to Compiz as being the problem (with Xserver 1.11).  ;)

---

### Post by Harry33 on 2011-09-18
> **VinDSL said:**
> Yes, sorry, for not being more clear!  

I've tried installing ubuntu-desktop many times, before and after your recommendation.  I say "tried" because apt-get always refuses to reinstall it, because I'm already running the latest version.

Accordingly, I've washed, rinsed, and reinstalled ubuntu-desktop several times (before and after installing the Xserver 1.11 package) with no joy.

I *know* what the problem is (at least, in my case).  I'm getting a seg fault in the unity-panel-service when logging into a Unity 3D session.  All other installed DEs are working fine with Xserver 1.11.

My Unity 3D desktop starts to load, but before it's fully populated unity-panel-service crashes.  g_sprawl_sync() fails to get a child, and throws a geis_init error.  So, I end up with a pretty wallpaper and Conky - no menus, no panels, no nothing...  

The only shortcut that works in Unity 3D is alt-ctrl-delete, but it allows me to logout gracefully.  Then, I login to GS, Unity 2D, E17, Classic, or whatever.  When I grow tired of these DEs, I purge the xorg-edgers PPA, reboot, and Unity 3D starts normally, like nothing happened.

Everything points to Compiz as being the problem (with Xserver 1.11).  ;)

I do not actually understand why the package ubuntu-desktop would be important here, at all. It is only a meta package, pulling in all kinds of "recommended" packages. I said "recommended", because there are hundreds of packages the fully working minimal setup does not need.

We have here issues with xserver 1.11 and proprietary drivers (nvidia). That does not suprise me, nvidia's latest beta does not officially support that ABI.

I do not use Unity, but instead, I can tell you that every now and then my setup refuses to start Gnome-shell and the fallback Gnome-panel is used. This started after upgrading to xserver 1.11 (edgers version). I do use Ricotz Testing PPA for Gnome-shell. That is an excellent PPA. Anyways, simply rebooting brings Gnome-shell session back.
And yes I do use nvidia-current 285.03 (edgers version) for my NVidia GTX285.

---

### Post by Sarvatt on 2011-09-27
This is what the problem is for now:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707)

---

### Post by beew on 2011-09-27
Just updated with xorg-edgers and can no longer start Unity (get blank screen). Need to do a ppa purge later.

---

### Post by VinDSL on 2011-09-27
I tried the new Xserver 1.11.1, last night, and still no joy!

As usual, no panels in Unity, and now GS is acting janky too.

For instance, doing a Search in the GS Dash Home (Activities or whatever they call it) results in an unresponsive desktop.  I have to Crtl-Alt-F1 out & reboot.

Xserver 1.11 was working far better (for me) than 1.11.1, but there have been 100's of changes to Oneiric since last week, soooo... those changes might have goofed things up.

Heh!  I think I'm getting too far ahead of the curve, dabbling with Xserver upgrades.  ;)

---

### Post by Sarvatt on 2011-09-27
Stay away from xserver version updates with proprietary drivers until it's been out for a few months, thats pretty much a given :) There will be a new nvidia driver coming "soon" that works properly though.

---

