---
title: "Webcam is not working on skype with Ubuntu 12.04"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by JLeite on 2012-05-04
I have a Philips SPC700NC web camera that does not work on Skype in  Ubuntu 12,04. It worked on 10.04 but after the  update it is not  working. The camera is ok with Cheese as it was before the update, but  not on Skype.
Any help to solve this problem is welcome.
Thank you.

---

### Post by NikTh on 2012-05-04
Hi , 
please try this command from terminal and see if your cam wokrs with skype 
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```
Thanks

---

### Post by JLeite on 2012-05-04
Greetings
I've already done that and keeps not working.
It works fine with Cheese, but not with skype.
Thank you, NikTh

---

### Post by JLeite on 2012-05-06
Any new ideas?
Thank you.

---

### Post by Morate on 2012-05-07
In your Skype call settings, make sure that the correct webcam is selected. For some reason, every once in a while, Skype will screw things up and all you have to do is reselect things. (It sometimes does this for microphones too.) Good luck!

---

### Post by JLeite on 2012-05-07
I've been careful about that, with no results.
Thank you, Morate.

---

### Post by verymadpip on 2012-05-07
Hi there.

have you tried

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
```
Which works for me.

Oops, I should say that's on a 32bit system.

---

### Post by JLeite on 2012-05-08
Right now the contents of my skype.desktop is:

[Desktop Entry]
Name=Skype
Comment=Skype Internet Telephony
Exec=bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'
Icon=skype.png
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;Application;




So, you sugest that the 4th line should be:
Exec=bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2covert.so skype'


Is that what you mean?
Thank you, Verymadpip

---

### Post by NikTh on 2012-05-08
Hi ,
try to purge skype and reinstall it from site --> [http://www.skype.com/intl/en/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/)
Thanks

---

### Post by JLeite on 2012-05-08
@NikTh:
I've already had done a few days ago after the upgrade from 10.04 to 12.04 and since then the skyke version is:
Skype (Beta) Version 2.2.0.35

---

### Post by verymadpip on 2012-05-08
Hi JLeite.

What I'm suggesting is you try to launch Skype from a terminal with the command I suggested.  (I got it from another thread, so it's not all my own work :)).  I'd maybe copy & paste the line to avoid any spelling errors & what have you.  Here's the thread that helped me:

[http://ubuntuforums.org/showthread.php?t=1937857&highlight=video+skype](http://ubuntuforums.org/showthread.php?t=1937857&highlight=video+skype)

Launching from the terminal with the command suggested was the first thing I tried & I haven't modified any of my files.  I may give it a try as for some reason I find the launching from terminal thing less than elegant, but I have Skype with video so perhaps I should just leave well enough alone.

---

### Post by JLeite on 2012-05-08
Not working too.
Shouldn't the 4th line in skype.desktop be equal to the command you sugested?
Best regards

---

### Post by verymadpip on 2012-05-08
Sorry that hasn't helped.

In truth I don't know about the skype.desktop - I actually can't find that file or folder or whatever it is.  I have looked, not very hard, but I've looked :)

I launch skype from a terminal with that command & all is well.

There's a bunch of other stuff in the thread I linked, I'm guessing you've probably tried all of that.  Really, I've reached the end of my usefulness on this one.  I was kind of hoping it would all work for you as easily as it did for me, alas no such luck.

Sorry, I should have asked are you running a 32 bit or 64 bit system?  I don't run Skype on my 64 bit rig, so I've no idea if the workaround I'm using works on 64 bit.

---

### Post by JLeite on 2012-05-08
Thank you for your effort. It was very kind of you to bothered with my problem.
You can see your skype.desktop with:[B]
gksudo gedit /usr/share/applications/skype.desktop
[/B]Ahh! I'm running a 32 bit system
Thank you anyway.
JLeite

---

### Post by verymadpip on 2012-05-09
Aha, found the file.  If I mess with it Skype breaks, so I'll stick to my messy method.  Thanks for the pointer there :)

Sorry I can't be of more help to you.

---

### Post by JLeite on 2012-05-18
I have the solution.
Instead of:
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
 The solution is:
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
 Now my webcam is ok.

---

### Post by kjaspan on 2012-07-19
I tried this on Xubuntu 12.04 with 64 bit AMD and my video freezes, then unfreezes only if I move something near the camera.

I read somewhere on this or the Skype forum that you can't use 64 bit libraries. With many of the libraries I tried a got an error message, like:

bash -c 'LD_PRELOAD=/usr/lib//usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype "$@"'
ERROR: ld.so: object '/usr/lib//usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Cheese works perfectly for me so I have to suspect a library problem. I have downloaded the latest v4l libraries, but to no avail.

---

### Post by kjaspan on 2012-07-31
Would someone please mark this unsolved. Video is still not working properly, even after a new Skype update today.

---

### Post by flint_ on 2012-08-26
Greetings,

Gonna try downloading the latest Skype from [http://www.skype.com/intl/en/get-skype/on-your-computer/linux/downloading.ubuntu32](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/downloading.ubuntu32).  The command line fix:
```

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype

```

Works not either as a user or root, giving The following error:
```

ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

Will get back with the results of install of Skype 
skype-ubuntu_4.0.0.8-1_i386.deb from Skype site, which apparently only supports 10.4 LTS.

Or maybe someone could tell me how to move my Skype contacts to Google, so I can have a consistent user experience?

---

### Post by flint_ on 2012-08-26
Sun 26 Aug 2012 10:02:19 AM EDT 

The good news is the install of skype-ubuntu_4.0.0.8-1_i386.deb did the trick.  Skype video is back.  Apparently  skype-ubuntu_2.2.0.35-1_i386.deb will not work with Ubuntu 12.04 LTS

---

### Post by kjaspan on 2012-08-26
flint_:

Unfortunately the install after download using the Ubuntu Software Center failed with:
Package Operation Failed 

Selecting previously unselected package skype:i386.
dpkg: error processing /tmp/skype-ubuntu_4.0.0.8-1_i386.deb (--install):
 skype:i386 4.0.0.8-1 (Multi-Arch: no) is not co-installable with skype:amd64 4.0.0.8-0oneiric1 (Multi-Arch: no) which is currently installed


I have a 64 bit AMD desktop, with Ubuntu 12.04 Precise.

---

