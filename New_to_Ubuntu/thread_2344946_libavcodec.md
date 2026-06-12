---
title: "libavcodec?"
date: 2016-11-29
forum: New to Ubuntu
---

### Post by Daveski17 on 2016-11-29
Hello,

What is the libavcodec, why is it vulnerable, and why hasn't it updated?


[IMG]http://i386.photobucket.com/albums/oo307/Davebucket17/libavcodec_zps2ahcpsfb.jpg[/IMG]



Thanks.

---

### Post by slickymaster on 2016-11-29
There's a thorough explanation in [this AskUbuntu thread]("http://askubuntu.com/questions/851190/how-to-update-libavcodec-on-ubuntu-14-04").

---

### Post by vasa1 on 2016-11-29
This plays just fine with Google Chrome: [http://www.imdb.com/list/ls053181649/videoplayer/vi3940333081?ref_=hm_hp_i_1](http://www.imdb.com/list/ls053181649/videoplayer/vi3940333081?ref_=hm_hp_i_1)

Please provide the actual link you want people to check.

Edit: posted without reading slickymaster's response!

Second edit: also plays in Firefox 50.0.1 (for I don't have any flash plugin installed).

---

### Post by Daveski17 on 2016-11-29
OK thanks for the replies. I guess there isn't really a fix then.

---

### Post by Frogs Hair on 2016-11-29
Try the following from webupd8

```
sudo apt install libavcodec-extra
```

---

### Post by vasa1 on 2016-11-29
Is there an issue with 16.04 as well? Firefox 50.0.1. Doesn't display that message on 16.04 for me.

Anyone have a video link to share that **does** display the message on 16.04?

---

### Post by yetimon_64 on 2016-11-29
> **Frogs Hair said:**
> Try the following from webud8

```
sudo apt install libavcodec-extra
```

I have both libavcodec-extra and libavcodec-extra-54 installed in 14.04 and still get the notice the OP mentions (Edit: I get them on Facebook). Though my libavcodec packages are supplied by the mc3man ppa for ffmpeg.

I finally got rid of the notice by going into about:config, searching for libavcodec, and then toggling the media.libavcodec.allow-obsolete value to true. Though that is not ideal security wise it will get rid of the notice on the next start of firefox.

@ vasa1, can you check what version of libavcodec 16.04 uses, I think it uses the libavcodec56 package from memory? I am posting from 14.04 at the moment, I will check later by booting into 16.04 though myself, but I think the notice only affects the libavcodec54 package in 14.04. I see there is one fix suggested on askubuntu to use a ppa in 14.04 to upgrade to libavcodec56 (which i THINK 16.04 already uses but not 100% sure on that until it is further checked).
[B]
Edit:[/B] just booted into 16.04 and the versions available are libavcodec-ffmpeg56 or libavcodec-ffmpeg-extra56 and I've never gotten the notice on Facebook in 16.04 like I do in 14.04.

---

### Post by Dennis N on 2016-11-29
> **vasa1 said:**
> Is there an issue with 16.04 as well? Firefox 50.0.1. Doesn't display that message on 16.04 for me.

Anyone have a video link to share that **does** display the message on 16.04?

I did see it once several days ago*, but revisiting that same web site, it no longer appears. Never saw it anywhere else. The only libavcodec on my Xubuntu 16.04 is:

```
dmn@Kayleigh:~$ dpkg-query --list libavcodec*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-=======================================================================
un  libavcodec-ffmpeg-extra56         <none>                <none>                (no description available)
ii  libavcodec-ffmpeg56:i386          7:2.8.8-0ubuntu0.16.0 i386                  FFmpeg library with de/encoders for audio/video codecs - runtime files

```

*update: I believe this was on Linux Mint 17, so not relevant - not seen on Xubuntu 16.04.

---

### Post by SeijiSensei on 2016-11-29
Upgrading to libavcodec56 fixed the problem for me on 14.04.

---

### Post by vasa1 on 2016-11-29
> **yetimon_64 said:**
> ...
@ vasa1, can you check what version of libavcodec 16.04 uses, I think it uses the libavcodec56 package from memory? I am posting from 14.04 at the moment, I will check later by booting into 16.04 though myself, but I think the notice only affects the libavcodec54 package in 14.04. I see there is one fix suggested on askubuntu to use a ppa in 14.04 to upgrade to libavcodec56 (which i THINK 16.04 already uses but not 100% sure on that until it is further checked).
Here we are:
```
09:39 PM ~ $ apt list --installed | grep libavcod

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libavcodec-ffmpeg56/xenial-updates,xenial-security,now 7:2.8.8-0ubuntu0.16.04.1 amd64 [installed,automatic]
libavcodec54/now 6:9.18-0ubuntu0.14.04.1+fdkaac amd64 [installed,local]
09:39 PM ~ $ 
```
Please note that my 16.04 was an upgrade from 14.04 and not a clean install, if that matters.

---

### Post by yetimon_64 on 2016-11-29
> **vasa1 said:**
> Here we are:
```
09:39 PM ~ $ apt list --installed | grep libavcod

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libavcodec-ffmpeg**56**/xenial-updates,xenial-security,now 7:2.8.8-0ubuntu0.16.04.1 amd64 [installed,automatic]
libavcodec**54**/now 6:9.18-0ubuntu0.14.04.1+fdkaac amd64 [installed,local]
09:39 PM ~ $ 
```
Please note that my 16.04 was an upgrade from 14.04 and not a clean install, if that matters.

You do seem to have a version from both 14.04 and 16.04. Both my installs are fresh installs. 14.04 uses the libavcodec54 version and 16.04 the libavcodec-ffmpeg56 version (or the "extra" version if selected for either).

---

### Post by Donnie Love on 2016-12-07
The explanations and solutions in this thread are far above my level of understanding.
Also: I don't know why, but I cannot paste into the terminal. I tried typing in some of the code, but nothing seemed to help.

---

### Post by &amp;KyT$0P# on 2016-12-07
> **Donnie Love said:**
> The explanations and solutions in this thread are far above my level of understanding.
Perhaps it would help to explain it in a way that doesn't require techie knowledge to parse and figure.

See where it says [FONT=Courier New]ubuntuforums.org/showthread.php?t=[/FONT]... near the top of Firefox?  Delete all that, then type [FONT=Courier New]about:config[/FONT] in there, just like you would type in a website.  Hit Enter.

You'll now have a silly warning in front of you.  Click that you accept the risk.  In that textbox where it says "Search:", type: [FONT=Courier New]libavcodec.allow-obsolete[/FONT]

The number of entries listed below should now be much reduced.  See the entry named [FONT=Courier New]media.libavcodec.allow-obsolete[/FONT]?  Double-click that one to change its value from false to true.

Then restart Firefox, and you're done. :)

---

### Post by yetimon_64 on 2016-12-07
> **Donnie Love said:**
> ...Also: I don't know why, but I cannot paste into the terminal. I tried typing in some of the code, but nothing seemed to help.

If you are using the keyboard key combinations for copying or pasting in the terminal, make sure you use **ctrl + shift +v** for pasting not the usual ctrl + v. 

Both the copy and paste combinations for the terminal require the shift key used as well.

Also you can use the right click context menu in the terminal for both copying and pasting, which is much easier than using the keyboard.

---

