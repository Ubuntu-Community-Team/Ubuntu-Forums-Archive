---
title: "Howto: Open Sound System in ubuntu feisty"
date: 2007-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Akre on 2007-10-14
First thing first: 
Why should I use OSS instead of ALSA? Alsa is far more superior!

Well thats simply not true. OSS has evolved, now it is open source -> [http://ubuntuforums.org/showthread.php?t=467914](http://ubuntuforums.org/showthread.php?t=467914)
and what most important, sound on my sound blaster live card (7 yers old I would say) is amazing. Twice as good as with ALSA. ALSA simply didn't manage to get my bass boost, and proper loudness. It always start cracking and make noises. I can use external amplifier for that but for headphones it is overkill. And why my 200$ card (7 years ago) behave as some cheap, crappy one?

With OSS sound is simply amazing. That's why I'm writing this howto, so others could have proper sound under linux, you are worth it :)

Dificulty level:** intermediete - advanced** i would say (one simple compile required - many thing could not work as previously, so you are willing to experiment.
**EDIT:** I will try on gutsy soon
Enviroment: Fesity Fawn, i386, kernel 2.6.20-16, kubuntu (should work in ubuntu as well - but I cannot guarantee - I do not know if gnome server can use oss - probably it can - I can confirm it can)

What will work: Sound under kde, sound in xine, kaffeine, amarok. Sound in flash in your browser
Problems: flash in firefox seems to block sound system. Not like this happend on alsa too? (at least in 6.10)
I'm only using this since yesterday, so perhaps more things will be broken or sth :)
[B]
What will not work[/B]: Skype - I was not able to get it working, nor in flash 1 .4. and 1 .3 - perhaps I did not tried enough hard

So let's get started:

First we install prereqrusites:

```
sudo apt-get install linux-headers-generic linux-source build-essential
```

Then we go to the oss website and download oss:

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

We choose linux 2.6 - deb - x86 (or amd if your are running 64 bit)

Once downloaded we install it with right click, Kubuntu package menu - > install package

Instalation will compile modules, find our sound card, and try to make it active.
On my machine last phase didnt worked out as alsa modules cannot be unloaded as they were in use. Restart did help. Only OSS modules came up.
If alsa were starting somehow still, remove any refrences to alsa in /etc/rc.dX and/or blacklist appropriete modules.

So now OSS modules work, but still we don't have sound.

Go to KDE Control center to the sound system, hardware: and choose OSS (automatic detection should work as well)
Sound shoud work. In Amarok you do the same: change output from alsa to oss - it is in the config: amarok -> module -> output plugin.

Now there are only two problems to work out: Kmix didnt start, and flash wont play sound.

First KMix:
OSS just overwrite library, that KMix is not able to work with. We need to preload old lib
LD_PRELOAD=/usr/lib/libasound.so.2.0.0 kmix

Then Kmix should work. There were not so many options compared to alsa, and perhaps diffrent layout.

Try start ossxmix and there you can adjust almost everthing (my favorite bass bost for the headphones :)

If you have many soundcards (that was my case) try:
```
ossinfo -x
```
and then
```
ossxmix -dX
```
where X is number of the card you would like to adjust.

Okay, so nowe everything but flash movie works.

[http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux](http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux)

There you find manual and source file, manual was kind off so thats how I did this:

Download:
[http://www.kaourantin.net/flashplayer/flashsupport.c](http://www.kaourantin.net/flashplayer/flashsupport.c)
 go to the file and comment OPENSSL on line 52:
make sure it looks like this:
```
[lines between 52 and 56]
//#define OPENSSL
//#define GNUTLS
//#define ALSA
#define OSS
//#define V4L1
```

Alternativly just find openssl dev package, which in ubuntu repo I was unable to find. I do not need ssl anyway.

So when your are done with hacking sources in this directory where sources are do:
```
 cc -shared -O2 -Wall -Werror flashsupport.c -o libflashsupport.so
 ldd libflashsupport.so
 sudo cp libflashsupport.so /usr/lib
```

Done, flash sound should work!

**UNINSTALL:**
I've upgraded to gutsy and I'm still on alsa here so I can only guess that you should remove start script in /etc/rc2.d
It is called oss or something like that.

It is end of the how-to. Many things could go wrong, I've just installed this yesterday, but suffice to say I thnik I will never use alsa again. Sound quality with OSS is simply twice as good, and I do not want my SB Live card play like some cheap software s*** :)

Feedback is welcome - i will update how to accordingly.

I really hope ubuntu will change from alsa to oss some time for now. In my opinion it is right way. People dont like when they hardware works bad under linux.

---

### Post by mufflon on 2008-01-08
Thanks for the guide!
The openssl-dev is in the repos. apt-cache and grep is your powerful allies! To locate the package just:
```
apt-cache search openssl | grep dev
```

aaaaHAAA! Found it! Now install:
```
apt-get install libssl-dev
```
(or use synaptics or aptitude or whatever you prefer when installing)
Now flashsupport.c compiles without deactivating OpenSSL. Nice.


Now, I got some weird issues on Ubuntu Studio 7.10 when using oss-linux_v4.0-1012_i386.deb.
So I downloaded the tarball instead and decompressed it.
```
cd /
sudo tar jxvf oss-linux-v4.0-1012-i386.tar.bz2
```
Blacklisted a bunch of ALSA-related modules in  /etc/modprobe.d/blacklist to be sure that ALSA wouldn't come back from the dead. In fact, I blacklisted all the modules I could find that begins with snd. To locate which ones you have loaded:
```
lsmod | grep snd
```

After that I rebooted, and activated OSS:
```
sudo soundon
```

It seems to work just fine. I haven't tried a lot yet, but it seems like I finally got rid of ALSA. Yay!

---

### Post by Hitchhiker427 on 2008-01-14
When I do this all of my system sounds refuse to play.  Is there a way to fix that?

---

### Post by mufflon on 2008-01-15
I'm still struggling with OSS, but I don't have a lot of spare time.
Testing it on Ubuntu and Ubuntu studio. Gutsy Gibbon.

Does any other sound play?
Did you try ```
osstest
```

If you get sound with osstest, here's a workaround that did
the trick for me.
Softlink one of the OSS-devices to /dev/dsp, which I think many 
of the sound applications are trying to use:
```
sudo ln -s /dev/dsp0 /dev/dsp
```
or even better, check which device /dev/dsp0 links to and avoid
softlinking to a soft link if you believe it to be an abomination... ;-)


Mind you, I'm NOT recommending this to anyone! 
You never know where you end up when you're using workarounds a lot.
Other than with an unstable system that is...
I still think OSS is better than ALSA.

I'm on a lookout for a better/cleaner solution, and would be glad for
all the help we OSS-lovers could get.

---

### Post by jrusso2 on 2008-01-15
I would love to see OSS back in Linux.  Alsa has never worked as well for me.

---

### Post by mufflon on 2008-01-15
It IS back in linux, AFAIC. It's been there all the time, IF you bought it.
But now it's open source again. Guess you could  say OSS is OSS... :D

Now, I'd love to get OSS back in Ubuntu. That would be at treat.
This whole mucking-around-business we're discussing here is for
the enthusiasts. Not for the average user. And certainly not as user-
friendly as Ubuntu strives to be. :rolleyes:

Check the blog of the man behind the first version of OSS:
[http://www.4front-tech.com/hannublog/](http://www.4front-tech.com/hannublog/)

And a comment on my workaround, for those of you who would like to
try it out:
It appears as if the softlink disappears when rebooting. I should've seen
that one coming. Just be sure to put the softlinking into /etc/rc.local. 
You can drop the sudo in front. The rc.local-script executes as root.

---

### Post by dyntryx on 2008-03-02
I had trouble getting Flash sound to work, even after following [the steps outlined by Akre]("http://ubuntuforums.org/showthread.php?p=3530203#post3530203").  After perusing a few blogs and the [4Front forums]("http://www.4front-tech.com/forum/"), I saw a comment suggesting that someone install the latest version of Flash.  Realizing my Flash was probably outdated, I followed the advice and was able to get my sound to work.

You should actually be able to do this with a simple...
```
sudo apt-get install flashplugin-nonfree
```

However, this was producing an md5 sum mismatch error, so I did it manually.  Here is a short guide for how I got my sound working:

Remove Flash if it's installed:
```
sudo apt-get purge flashplugin-nonfree
```

Download the latest version, extract the gzipped tar file, and enter the installation directory:
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -zxf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
```

**Close any open browser windows!**

Run the installation script and follow the instructions (this should locate your browser plugin directory and place the file there--you could do this manually if you know where it's at):
```
./flashplayer-installer
```

On my machine, the installation script placed *libflashplayer.so* in *~/.mozilla/plugins*.

Many threads recommended to place the file in */usr/lib* as well:
```
cp libflashplayer.so /usr/lib
```

**This last part may vary depending on your configuration--if you're unsure you may want to leave this out!**

Finally, I cleaned up my old flash plugins that were unnecessary; I checked the following locations and removed the file if it existed:
```
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/flashplayer.xpt
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox/plugins/flashplayer.xpt
~/.mozilla/plugins/flashplayer.xpt
```

**IMPORTANT**

You can try starting your browser now and see if you get sound from Flash--browse to [youtube.com]("http://www.youtube.com") if you need a test site.

However, if this does not work, **try restarting your machine**.  My sound would not work until after a reboot.

Hope that helps if anyone is having problems. :)

---

### Post by SoulSmasher on 2008-04-10
does this guide also work for gutsy and hardy ? (are the steps same?)

---

### Post by mufflon on 2008-04-11
Yep.
I tried it on Gutsy, as posted above... ;-)
Everything did not work flawlessly. If I recall it correctly the new and shiny
OSS did not work with gstreamer/volume control in the panel. I had to use
the OSS-mixer.
Comments anyone?

The steps were the same. Haven't tried it on Hardy yet.
But with pulseaudio I suppose it will be easier to change from ALSA to
OSS or whatever.

Has anyone tried Hardy+PulseAudio+OSS? I'll give it a go on my laptop if
I can find some spare time. In a month or so. Or a year... :-/
Would be interesting if PulseAudio solves the few remaining problems I had.

---

### Post by art2003 on 2009-03-12
Success, thanks a lot.
As far as I know this is the ONLY way to get sound over HDMI with an ABIT A-N78HD motherboard (chipset ACL888)

If somebody else tries this you need:

NVIDIA 177.82 driver

sudo rm /dev/dsp
sudo ln -s /dev/oss/oss_hdaudio0/spdout1 /dev/dsp

then you will get sound over HDMI

With ALSA it just says everything is fine and should be working but the sound never makes it to the TV

---

