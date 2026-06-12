---
title: "unable to install pepperflash in Ubuntu Studio"
date: 2016-10-15
forum: New to Ubuntu
---

### Post by neophyte4 on 2016-10-15
Hello,..I'm new to Ubuntu, just downloaded it and installed it 4 days or so ago,.I also installed the Opera web browser,as I prefer it to Mozilla ff.
Now I find that I can not get flash content to play in some sites,..I've read several posts at different places,including here,.as to how to download,
and install something called Pepperflash.I even removed Opera,.and separately
and alternately,.installed,..Chrome,.Chromium,.and found out that flash is not bundled with neither of those???,
Now this is what I did to install Pepperflash with Opera installed....


sudo apt-get install pepperflashplugin-nonfree


seemed like quite a few things were downloaded at the time.
After the download and install was complete,.I saw the following..


/tmp/Pepperflashplugin-non free.vGzgdc8rsq/google-chrome-stable_54.0.2840.59.1 amd64.deb' saved [45527232/45527232]
mv: can not stat' unpackchrome/opt/google/PepperFlash/libpepflashplayer.so':
No such file or directory      :confused:




as I said this is my first time trying Ubuntu Studio,or any flavour of Ubuntu for that matter.
I've ticked on the canonical thing in settings,.changed to main server as opposed to US sever for updates,..enabled non free
software,.etc etc. followed what I've found in all my google searches,.all to no avail.
Any assistance would be greatly appreciated;...
thanks in advance.


MJS


PS. I'd like to stick with Opera if at all possible,...private VPN and all that.

---

### Post by howefield on 2016-10-15
Open the Software & Updates application and enable the *Partners* repository from the *Other Software tab*. (You don't need the sources option).

Close out and you'll be asked to reload your software sources, do so and then from the terminal use the following command.

```
sudo apt install adobe-flashplugin
```

If Opera is open, you'll need to close it and relaunch it for flash to become effective.

---

### Post by neophyte4 on 2016-10-15
> **howefield said:**
> Open the Software & Updates application and enable the *Partners* repository from the *Other Software tab*. (You don't need the sources option).

Close out and you'll be asked to reload your software sources, do so and then from the terminal use the following command.

```
sudo apt install adobe-flashplugin
```

If Opera is open, you'll need to close it and relaunch it for flash to become effective.



Hello howefield first of all thanks for your reply,..now,I've done that, in software and updates settings ,I've ticked on the following....Canonical free and open software(main), community, free and open(universe),..Proprietary drivers(restricted)
Software restricted by copyright(multiverse)
in "Other software"...I've ticked on;...Canonical Parters(software packaged by canonical partners),..using the commands suggested I get something like not found,  ](*,)
thanks again for your help

---

### Post by howefield on 2016-10-15
Ok, well let's see what you have done with the repositories, can you give us the output of the following terminal command..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Always best to copy/paste the terminal output back here between code tags so that others can see the full story.

If you didn't reload your software sources when you closed out the Software & Updates application, you would need to do a 

```
sudo apt update
```

in order for the system to be aware of what is in the repository that you just added.

PS. I just noticed that you didn't mention which release of Ubuntu Studio you were using, if it is earlier than 16.04 you would need to use apt-get rather than the simpler apt..

```
sudo apt-get install adobe-flashplugin
```

---

### Post by neophyte4 on 2016-10-15
howefield, here's what I get when entering that particular command,..


```
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list.d/opera-stable.list:deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)
```


sorry forgot to mention the Ubuntu  version....Distributor ID:	UbuntuDescription:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

---

### Post by howefield on 2016-10-15
That's fine, so now do the..

```
sudo apt update
```

and then

```
sudo apt install adobe-flashplugin
```

should do it, but if not, post back any errors.

---

### Post by neophyte4 on 2016-10-15
howefield,..that seemed to have worked,..the only worry that I have now,.is weather Adobe will update this plugin in the future,..which is why I wanted to install Pepeerflash,
But since this is working,.I'll take it for now,as it will allow me to catch up on my online lectures.
Thanks a lot for your time and help,.very much appreciated indeed,...hope you have a pleasant weekend.
MJS

---

### Post by howefield on 2016-10-16
> **neophyte4 said:**
> howefield,..that seemed to have worked,..the only worry that I have now,.is weather Adobe will update this plugin in the future,..which is why I wanted to install Pepeerflash,

Yes the player will be updated as required.

If you go to this page : [http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/) you will note that you have Flash version 23,0,0,185 installed which corresponds with the Chromium based browsers (which is what you'll compare with). This will be updated along with your system updates as they become available. There should be no worry about falling behind.

Incidentally the package also gives you a separate flash player version which Firefox can make use of, I appreciate you don't use Firefox but just mentioning it so that you are aware Firefox would have flash already available.

> But since this is working,.I'll take it for now,as it will allow me to catch up on my online lectures.

Cool, have fun :)

> Thanks a lot for your time and help,.very much appreciated indeed,...hope you have a pleasant weekend.

You're welcome and hoping the same for you.

---

