---
title: "ATI unsupported cards in Jaunty:  full effects"
date: 2009-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by airspirit on 2009-05-19
I hate the breakage in the open source drivers.  You know what I mean:  the artifacts, flashing, white lines everywhere, etc.  The latest open source git drivers seem to have a lot of this fixed.  While I'm sure you can wait until the next release when we get newer drivers, here is how to do this in Jaunty and get your system fixed now.  Worst case scenario of doing this is that on your particular card all the cleanup hasn't been done yet, but on my x1200 this worked wonderfully.

Open up a terminal and do the following:

```
sudo apt-get install build-essential autoconf automake libtool pkg-config git-core

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev

git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-ati

cd xf86-video-ati

sudo ./autogen.sh --prefix=/usr --enable-dri

sudo make

sudo make install
```

Now restart your machine and you're using the new drivers.  Try bumping up your visual effects to max and see what happens.  If you're lucky like me, everything will work flawlessly.  If not, then you may want to wait a couple weeks and try it again, but you're no worse off then you were before.

Enjoy!

---

### Post by Hypersonic on 2009-05-27
Thanks!  My X1200 flickers a lot less now.

Is there a way to get 3D working?  I miss the games that used to work in Wine under Hardy.

---

### Post by ssri on 2009-05-28
> **Hypersonic said:**
> Thanks!  My X1200 flickers a lot less now.


How much flickering is left?  And when does it happen?

---

### Post by BooDaddy on 2009-05-28
Well, this didnt work for me. When I boot, I see the ubuntu logo, then the screen flashes a few times, but then eventually goes dark.

I am using an ATI Radeon x1200. 

Any suggestions?

---

### Post by Makrin on 2009-05-28
You can try the following
maybe they'll work ?

#Xorg Drivers
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main
```

Working flawlessly on my x1300 t60 :-)
I've attached a script(not mine) to download the keys automatically

---

### Post by BooDaddy on 2009-05-28
So, should I run those commands Makrin, and then re-run all of the commands that airspirit posted at the first?

---

### Post by Makrin on 2009-05-28
I assumed you had tried the commands on the 1st post already.
The ones on the ppas are newer (i think)
In terminal type;

```
gksudo gedit /etc/apt/sources.list
```
add the following lines at the bottom;
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
```

then extract launchpad-update.tar.gz file. 
launch script by typing;

```
sudo ./launchpad-update
```

after script is done downloading keys
type;

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by four o two on 2009-05-28
> **Makrin said:**
> I assumed you had tried the commands on the 1st post already.
The ones on the ppas are newer (i think)
In terminal type;

```
gksudo gedit /etc/apt/sources.list
```
add the following lines at the bottom;
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
deb http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main main
```

then extract launchpad-update.tar.gz file. 
launch script by typing;

```
sudo ./launpad-update
```

after script is done downloading keys
type;

```
sudo apt-get update && sudo apt-get upgrade
```

I get: "E: Malformed line 57 in source list /etc/apt/souces.list (dist parse)"

talking about:
```
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty
```

---

### Post by BooDaddy on 2009-05-28
> **four o two said:**
> I get: "E: Malformed line 57 in source list /etc/apt/souces.list (dist parse)"

talking about:
```
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty
```


What you will need to do is add main at the end of that line.  so that it looks like:

```
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu jaunty main 
```

that let me do the apt-get update as well as the apt-get upgrade

I am booting it up now to see what happens.

---

### Post by BooDaddy on 2009-05-28
Wow. This worked great for me. not 100% but its a good 90%!!! and thats alot better than what I had (which was 0% heh)  Compiz is actually running pretty nicely. 

Heres a step by step of what I did:

1- I followed the steps mentioned in this first thread (Thanks Airspirit!) . I will post them again below:
 
```

sudo apt-get install build-essential autoconf automake libtool pkg-config git-core

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev

git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-ati

cd xf86-video-ati

sudo ./autogen.sh --prefix=/usr --enable-dri

sudo make

sudo make install

```Then I rebooted my computer. I had to use the recovery mode and then drop to root with networking in order to perform the next steps as my video wasnt displaying anything at all.

After I rebooted I followed these instructions (Thanks Markin!!!) I will post them below:

 ```

     gksudo gedit /etc/apt/sources.list 

```Add the following lines at the bottom;
 
```


deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
deb [http://ppa.launchpad.net/tormodvolden/ppa/ubuntu](http://ppa.launchpad.net/tormodvolden/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tormodvolden/ppa/ubuntu](http://ppa.launchpad.net/tormodvolden/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main main 


```I did it a little differently here as I had to drop to root to get going. So I uploaded the file Markin posted in this thread and unzipped it on my server so I could wget it on my laptop.

You can use this if you need to wget the file:

```
 wget http://gigahype.net/files/launchpad-update 
```Then after the file downloads do the following:

```

sudo sh ./launchpad-update 

```After script is done downloading keys
type;

   ```

     sudo apt-get update && sudo apt-get upgrade

```Then reboot the computer one more time and you should have video!!

Thanks again to Airspirit and Markin for these suggesstions. This got me going again, and running alot better than I was!

Oh, and if your in root like I was, you can omit the sudo from the commands.

---

### Post by Hypersonic on 2009-05-28
> **ssri said:**
> How much flickering is left?  And when does it happen?

None that I see now.  Very nice after the problems with the stock Jaunty drivers.  It's worth making the change.

---

### Post by yoshiki2 on 2009-11-23
Any updates? It's not working on ubuntu 9.10
> **airspirit said:**
> I hate the breakage in the open source drivers.  You know what I mean:  the artifacts, flashing, white lines everywhere, etc.  The latest open source git drivers seem to have a lot of this fixed.  While I'm sure you can wait until the next release when we get newer drivers, here is how to do this in Jaunty and get your system fixed now.  Worst case scenario of doing this is that on your particular card all the cleanup hasn't been done yet, but on my x1200 this worked wonderfully.

Open up a terminal and do the following:

```
sudo apt-get install build-essential autoconf automake libtool pkg-config git-core

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev

git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-ati

cd xf86-video-ati

sudo ./autogen.sh --prefix=/usr --enable-dri

sudo make

sudo make install
```Now restart your machine and you're using the new drivers.  Try bumping up your visual effects to max and see what happens.  If you're lucky like me, everything will work flawlessly.  If not, then you may want to wait a couple weeks and try it again, but you're no worse off then you were before.

Enjoy!

---

