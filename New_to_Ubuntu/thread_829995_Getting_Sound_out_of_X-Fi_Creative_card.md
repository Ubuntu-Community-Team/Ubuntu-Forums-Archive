---
title: "Getting Sound out of X-Fi Creative card"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by pfrancke on 2008-06-15
Hi,  I'm very newbie to Ubuntu.  I have a Vista system that I threw Ubuntu 8.04 on dual boot separate drive.  Messed up my system, but between the Ubuntu install CD, and Windows repair, managed to make it all work.  I am very excited about Ubuntu and dream of a world w/o MS...

Anyway, I've got a creative X-Fi sound card.  I downloaded the XFIDRV and tried to install and got the below error:

====================================================================
Installation is in progress. Please wait...
         checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful



I am interested in any and all info (presented at the idiot level please, if possible -- I couldn't even find the config.log for example) about how I can get my card to produce sound.

Thanks so much!!  Piet

---

### Post by pfrancke on 2008-06-15
Also, for what it is worth, under sound preference, no sound device shows up and if I do any sound test, I get get the following alert:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by Nepherte on 2008-06-15
> **pfrancke said:**
> Also, for what it is worth, under sound preference, no sound device shows up and if I do any sound test, I get get the following alert:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
If you don't have any sound card installed, then this is normal behaviour. So no need to worry about that yet.

Are you installing the drivers from the website? You'll need the build-essential package, most likely. I never got them to work on my system. When I use OSSv4, I get my x-fi working. This is a guide on how to install OSSv4:
[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

### Post by pfrancke on 2008-06-15
Thank you -- I now have sound.  I struggled a little bit as I first had to take steps to remove a broken oss installation, but after that it ran clean.  Thank you very much for pointing me in the right direction.

---

