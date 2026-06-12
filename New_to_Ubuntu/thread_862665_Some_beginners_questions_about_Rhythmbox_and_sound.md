---
title: "Some beginners questions about Rhythmbox and sound?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by gabriella on 2008-07-17
Hi,

I've recently installed Hardy and am getting to figure thing out...slowly. So I thought I try Rhythmbox. I noticed there are some radio stations preloaded already. Why these? just curious.

Then I tried entering the URL of a station I've listened to in windows. I get the error:
"couldn't start playback--A text/html decoder plugin is required to play this stream but not installed" 

OK no suprise but how do I locate and get the particular codec I need to play this? not just for this station but others too? I tried going to the website of the station concerned but of course the only options for live streaming are either Windows MP or Real Player. So how do I get arround all this?

More generally what are my options to listen? In windows I've used Real Alternative for some streams. I know there's a FireFox version but will it work under Linux? I gues what I'm asking is this; is Rthymbox my only option?

Thanks for answering these basic questions!

---

### Post by hansdown on 2008-07-17
Hi gabriella, and welcome. Firefox has a music browser callrd foxytunes. If you click tools>addons you will be able to browse for lots of goodies.

---

### Post by Raistlin82 on 2008-07-17
I prefer to use amarok rather than rythmbox, its also great for syncing my ipod, not too sure on where to get the codecs from....  There is a real player for linux  [http://www.real.com/linux](http://www.real.com/linux)

---

### Post by AndyCooll on 2008-07-17
Seems like you need to install some codecs.

I've recently been getting my head around Rhythmbox and radio stations too. 

What worked for me was going to the radio stations website and clicking on play. This would then open a box asking whether you want to save or play a .pls file. It initially defaulted to opening with "Movie Player", however I chose "Other" and navigated to Rhythmbox (filesystem > usr > bin > rhythmbox). This then attempted to open but requested to install additional codecs. I selected the codecs suggested ...and voila I'm now listening to the Internet radio station.

If you're installing them manually you usually need to go to Applications > Add/Remove and do a search for "gstreamer". The codecs you typically need are the "ffmpeg", "extra plugins", "mms, wavpack, quicktime, musepack" and "aac, xvid, mpeg2, faad". Also known as gstreamers good, bad and ugly packs.

And when choosing live streaming options I've always found choosing the Windows Media Player option to work best. 

:cool:

---

### Post by gabriella on 2008-07-18
I down loaded Foxytunes without problem.

Yes I guess I need the codecs. I had the same experience when I went to the radio station website. It too defaulted to Movie Player when clicked on play  and promted to let it search for codecs. I did that and it works fine as long as I listen in Movie Player (the psyco visualisation drives me nuts!!) I try what you sugested for RhythmBox next.

I have no experience of using Amorok but as I said I'm just starting. The one thing I'd like to know is if there's a Real Player for Linux  what about Real Alternative. I've used RA under windows XP and there's a version with Firefox plugins but am confused if that still limits it to windows or can be used under Firefox in Linux?

---

### Post by hansdown on 2008-07-18
Hi gabriella. If you click system> administration> synaptic package manager you can then use the search function. Simply type in quicktime to see some good downloads. Hope that helps.

---

### Post by SunnyRabbiera on 2008-07-18
also try the medibuntu repository
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by hansdown on 2008-07-18
Hi gabriella. There is a thread on realplayer with a link for it. Look for a post by dben.

---

### Post by HDave on 2008-07-18
You only need to install ubuntu-restricted-extras and you should be fine.

---

### Post by Raistlin82 on 2008-07-19
Real Player  for Linux  [http://www.real.com/linux](http://www.real.com/linux)

---

### Post by silkstone on 2008-07-19
Taken from an excellent tutorial on these forums...

The following steps show how to install Real Player 11 and Mozilla Plugin for Firefox 3.0 browsers running on Hardy Heron.

Download Real Player 11 from:

  [www.real.com](www.real.com)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

Open Firefox and type about: plugins (without the space) in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

If found, your Real Plugin is installed properly!

---

