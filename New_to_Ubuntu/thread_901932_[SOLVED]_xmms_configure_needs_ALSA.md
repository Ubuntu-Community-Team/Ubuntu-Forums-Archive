---
title: "[SOLVED] xmms configure needs ALSA"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by mdecler2 on 2008-08-26
I compiled xmms 1.2.11 from source with the following dependencies:
libogg-dev, libvorbis-dev, libgtk1.2-dev, and libalsaplayer-dev.

This was my configure line:
./configure --prefix=/usr --with-ogg-prefix=/usr/lib --with-vorbis-prefix=/usr/lib --with-alsa-prefix=/usr/lib

But it says that the ALSA plugin will not be installed after configuring.
Where is ALSA, and how can I get xmms to work?

When I continued compilation anyway, XMMS would zip through the songs in my playlist with no sound whatsoever. I am guessing it doesn't have access to the sound device through ALSA.

---

### Post by nicedude on 2008-08-26
Why compile from source when there are debs of xmms to be had, I am using xmms right now and I don't need anything extra and also alsa is installed by default in Ubuntu. Try "sudo alsamixer" without quotes to see the alsamixer sound control volume levels ( if those are down then turn them up ). If alsamixer levels look OK then I would suggest a simple google search for "ubuntu hardy xmms deb" and follow that to get a deb package of xmms to install as it works just fine here.


Why did everyone try to foresake xmms, what is wrong with it. Its small and light on resources while at the same time takes care of business. Come on Linux community what did xmms ever do to you to deserve abandonment :-)

---

### Post by mdecler2 on 2008-08-26
> **nicedude said:**
> 
Why did everyone try to foresake xmms, what is wrong with it. Its small and light on resources while at the same time takes care of business. Come on Linux community what did xmms ever do to you to deserve abandonment :-)

Actually, the answer is that the Ubuntu team dropped XMMS from Hardy's repositories. I needed to do a clean install from Dapper. I tried doing the release upgrade via synaptic to Hardy, and it didn't quite finish. There were several library problems, and they kept compiling on top of each other the more packages I installed from the repos.

Anyway, I found the answer to my problem:
> **sartek said:**
> First Step:
We need to download the required packages to compile XMMS
# sudo apt-get install autotools-dev automake1.9 libtool gettext libasound2-dev libaudiofile-dev \
libgl1-mesa-dev libglib1.2-dev libgtk1.2-dev libesd0-dev libice-dev libmikmod2-dev libogg-dev \
libsm-dev libvorbis-dev libxxf86vm-dev libxml-dev libssl-dev build-essential make
...
Download XMMS sources:
# wget [http://xmms.org/files/1.2.x/xmms-1.2.11.tar.gz](http://xmms.org/files/1.2.x/xmms-1.2.11.tar.gz)
Unpack it:
# tar xvf xmms-1.2.11.tar.gz
Change the working directory to the source directory:
# cd xmms-1.2.11/
Third Step:
Compiling it:
This generates the necessary files, and checks your system:
# ./configure --prefix=/usr
The actually compiling
# make
Fourth Step:
Install it:
# sudo make install


The full instruction set for source installation of XMMS in Ubuntu Hardy is at [http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

---

### Post by nicedude on 2008-08-26
The real answer is still to just find a deb of xmms to keep as I use one and it works just fine with click-click bang windows installation ease. And I knew everyone cut xmms out of their repos that is why I was sad :-( 

Glad you found some answer though :-)

---

### Post by mdecler2 on 2008-08-29
After I installed xmms from source, I had an issue where xmms was "playing too fast". It was not really playing at all, but cycling through the songs _very_ quickly without sound. I search for this on Google and found the problem to be that xmms is fixed on the incorrect output device:

Go to the menu (button on top left-hand corner) Options -> Preferences. In the Preferences menu, under Output Plugin, make sure that the ALSA output plugin is being used (or the correct sound output device).

Also, instead of installing from source, you have the option, as nicedude has said, to install the precompiled xmms for Hardy. The follwing URL is for xmms version 1.2.10 on an i386 system:
[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)
Like the URL says, this is build2. The first i386 build failed for me because I could not find the correct libglib1.2 dependencies. I followed the directions for the build2 and am running xmms now with few problems.

For precompiled xmms version 1.2.10 builds for other systems besides i386, and for the first xmms i386 build go to: [https://launchpad.net/ubuntu/hardy/+package/xmms](https://launchpad.net/ubuntu/hardy/+package/xmms)

In order to install a package (with the .deb extension), you need to run
```
sudo dpkg -i xmms-package-xxxx.deb
```
where xmms-package-xxxx.deb is the file downloaded from one of the above URL's.

Hope that helps!

---

### Post by mdecler2 on 2008-09-15
> **mdecler2 said:**
> I compiled xmms 1.2.11 from source with the following dependencies:
libogg-dev, libvorbis-dev, libgtk1.2-dev, and libalsaplayer-dev.

This was my configure line:
./configure --prefix=/usr --with-ogg-prefix=/usr/lib --with-vorbis-prefix=/usr/lib --with-alsa-prefix=/usr/lib

But it says that the ALSA plugin will not be installed after configuring.
Where is ALSA, and how can I get xmms to work?

When I continued compilation anyway, XMMS would zip through the songs in my playlist with no sound whatsoever. I am guessing it doesn't have access to the sound device through ALSA.

I must answer my original question: the reason why XMMS was "playing too fast" was because the wrong output plugin was selected.
Once XMMS is installed, click the top left hand corner menu button, go to Options -> Preferences. Make sure that the Output Plugin selected is ALSA, or whatever output plugin is appropriate for your system.

---

