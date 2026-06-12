---
title: "Need Help For Playing 3gp with Sound in Intrepid"
date: 2009-01-18
forum: Philippine Team
---

### Post by wygee on 2009-01-18
Need help with getting 3gp to play with sound on intrepid. was able to get it going in gutsy before but i cant remember how i did it. as far as i know i have the latest gstreamer codecs which were downloaded through synaptic. but when i play 3gp vids i dont get the sound. videos ok but thats it. thanks in advance. :)

---

### Post by loell on 2009-01-18
you could install totem-xine / gxine / xine then install w32codecs from [Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). then you can play 3gp.

---

### Post by wygee on 2009-01-19
was able to install totem-xine succesfully. but unable to get w32codecs. 
came up with: 

"Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

what the heck? :confused:

---

### Post by dannybuntu on 2009-01-19
Have you tried this:

> Install libdvdcss2 and w32 video codecs in Ubuntu 8.10 (Intrepid Ibex)

Support for WMV, RealMedia and other formats has been bundled into the w32codecs package. This package is not available from the Ubuntu repositories due to licensing and legal restrictions.

For Ubuntu 8.10 (Intrepid Ibex) Users run the following command

    sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then, add the GPG Key using the following commands

    sudo apt-get update

    sudo apt-get install medibuntu-keyring

    sudo apt-get update

For i386 Users install Codecs using the following command

    sudo apt-get install w32codecs libdvdcss2

For amd64 Users install Codecs using the following command

    sudo apt-get install w64codecs libdvdcss2

From: http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html</blockquote>

Then try this:

> sudo apt-get install vlc

If it still doesn't work, I don't know.

---

### Post by wygee on 2009-01-19
thanks dannybuntu and thanks din loell for your inputs. im currently acquiring VLC and it says it will take a few minutes to compile everything. hope your suggestion works dannybuntu.

keeping my fingers and toes crossed. :grin:

---

### Post by wygee on 2009-01-19
crap. no go. vlc still wouldnt play the damned 3gp files with sound. did i mention that i was running 64bit intrepid? well i forgot, but i was also running 64bit gutsy and i got 3gp to play with sound. shouldn't have switched to intrepid. anyway, i followed the steps like a good boyscout. still didnt work. :(

---

### Post by HavocXphere on 2009-01-19
VLC should be working. Does the freshly compiled VLC do sound with other media files?

---

### Post by wygee on 2009-01-19
yep.. it plays sound. just not with 3gp.. n i dont know why. i might do a reinstall. just not now, im using intrepid to surf eh. hehehe:P

---

### Post by andrew.46 on 2009-01-19
Hi,

One issue can be that 3gp containers can hold either amr or aac sound. Do you know which sound is involved with your files? If you can post a link to a typical file or place a small one on these forums that might help.

Andrew

---

### Post by daxumaming on 2009-01-20
you need the real player binary installed to be able to play 3gp. it'll even play 3gps' on VLC as long as it's installed. you can find the binary here: [http://www.real.com/linux](http://www.real.com/linux)
execute it as root (via sudo) so the codecs would install globally

---

### Post by wygee on 2009-01-21
thanks for the suggestions and help guys! means a lot to me. :D haven't tried your suggestion yet dax, will do once i get home and get to play with my box. i'll post an update on the results.

---

### Post by wygee on 2009-01-22
finally! i was able to get to play 3gp vid's with sound by using mplayer. :D only drawback with mplayer is that the player controls are not locked with the player screen. any way that i could get them locked so that when i drag the screen one way the controls go with it?

---

### Post by andrew.46 on 2009-01-22
Hi,

> **wygee said:**
> finally! i was able to get to play 3gp vid's with sound by using mplayer. :D only drawback with mplayer is that the player controls are not locked with the player screen. any way that i could get them locked so that when i drag the screen one way the controls go with it? 

Good to see the files are finally playing :-). There may be a way with gmplayer but could I suggest you install smplayer as well? This is a front-end for MPlayer which is much more feature rich and is under constant development, unlike the gmplayer (the default gui player of MPlayer). SMplayer will be much easier to adapt to your needs and is available from synaptic.

All the best,

Andrew

---

