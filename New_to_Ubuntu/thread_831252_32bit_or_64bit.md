---
title: "32bit or 64bit"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by balanovich on 2008-06-16
Hi
I recently installed Ubuntu 8.04, but I don't know if I have the right release.

Before downloading, I was asked to choose:
What type of computer do you have?
-Standard personal computer (x86 architecture, Pentium, Celeron, Athlon, Sempron)
-64bit AMD and Intel computers

I choose the 64bit AMD and Intel one becaus my computer has:
Mobo: M2A VM-HDMI (I don't use the HDMI module)
AMD Dual-core 5600+
EVGA's GeForce 8600 GTS
2 gig of RAM 

I read that there is a 32bit release and a 64bit. Wich one do I have ?
Is the one for standrd PC the 32bit one?
If so can I use the 32bit even is my PC doesn't have any of Pentium, Celeron, Athlon, Sempron ?
I eventually wanted to get the codecs for GXine (to pay DVDs) but I couldn't because of compatibility problems (AMD64). The "(AMD64)" was there to tell me that it is my CPU or my Ubuntu release that is the problem?

While trying to install libdvdcss2 I read this : "If you are using Ubuntu 8.04 "Hardy Heron" (AMD64)" ([https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs))
and then instruction followed.
Again the "(AMD64)", this time, it must be referring to the release and not my CPU. So then, someone using the release for standard PC couldn't have libdvdcss2 (there were no instruction other Hardy releases) and therefor couldn't watch DVDs ? It doesn't make sense.

I am a little bit confused. I'd apreciate it if you could help me.
Thanks

---

### Post by drs305 on 2008-06-16
If you have the 64-bit hardy version installed, when you run the following command you will see: **x86_64**
```
uname -m
```

---

### Post by waspbr on 2008-06-16
from your post, I would say you have a 64 bit ubuntu aka amd64.  ubuntu comes in two types 32 bit (Standard personal computer) and 64bit (amd64). Actually you could have installed the 32 bit version without any problems, however you wouldn't be able to fully use your computer's capacity, for the 64 bit version is considerably faster.

Personally I would prefer the 64 bit version since I have to run some simualtions in programs like matlab. though there are some minor quirks in it, pretty much almost everything available for 32 bit  si available for amd64, of course most people still use 32 bit systems but this is slowly changing.

for the DVD thing, I haven't looked into it myself, but it should be fixed by now...

---

### Post by cotcot on 2008-06-16
I got libdvdccs from the medibuntu repository.(add [COLOR="Blue"]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free[/COLOR] to /etc/apt/sources.list)

To get the key : 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

then 
```
sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by JoshuaRL on 2008-06-16
Also, install the Ubuntu restricted extras for various codecs needed.
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by drs305 on 2008-06-16
The medibuntu site recently changed the way they want users to add their repository to the sources.list  Their recommended method now installs a /etc/apt/sources.list.d/medibuntu.list file (for whatever reason).

Here are the commands for adding the medibuntu repository from the [Ubuntu_Medibuntu_Documentation]("https://help.ubuntu.com/community/Medibuntu"):
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
Then add the GPG Key and update the list:
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Note: If you have a medibuntu line in /etc/apt/sources.list you may receive a warning about duplicate entries. If this is the case, comment out or remove the entry in sources.list

Finally, the apps you see in the repositories when you open synaptic are all 64-bit versions. It is possible to force install 32-bit apps with the appropriate additional libraries if you really need a 32-bit app for which there is no 64-bit alternative.

---

### Post by balanovich on 2008-06-16
I checked my Ubuntu version. I have the 64bit.
Waspbr, did I understand you well?
There are 2 32bit version, one of them called AMD64, and there is a 64 bit version also called AMD64 ?
isn't that very confusing, not to say a little stupid?

When I try to download the xine extra plugins the exact error message I get is :
"Xine extra plugins cannot be installed on your computer type (amd64)

Either the application requires special hardware features or the vendor decided to not support your computer type."
Are these plugins important?

I redid all that you told me to fix my video problem, but it's still not working. 

Since, at some point, I updated something after updating the kernel, without rebooting, I think I screwed up a little.
I also downloaded the 7.10 codecs for gxine. Now the colors are inverted. (it's better than not working :p)

Anyways, I'm going reinstall, it's easier than fixing. And now that I know what I have, I'll probably do it better.


Thanks for your help.

P.S. There are a bug that intrigue me.

 I followed : [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
when I typed this:sudo /usr/share/doc/libdvdread3/install-css.sh
this happenned :
No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

--20:45:20--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz)
           => `libdvdcss_1.2.5.orig.tar.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.29.100
Connecting to [www.dtek.chalmers.se|129.16.29.100|:80](www.dtek.chalmers.se|129.16.29.100|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
20:45:20 ERROR 404: Not Found.

I've installed debhelper and fakeroot, I'm sure. When I do it again, It says that I already have the latest versions available.
Is this relevent to my problem?

Why is something that's for "absolute beginner" "higly experimental" ?

---

