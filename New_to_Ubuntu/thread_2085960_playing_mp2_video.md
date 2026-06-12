---
title: "playing mp2 video"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by keithmac on 2012-11-19
laptops using Ubuntu Linux 11.04 dual-booted with either W7 or Vista

I have many video files recorded in mp2      Windows Media Player plays them fine. Banshee can't, offers to look for codecs but fails to find any when it looks.  

I need a simple, alternative player that will do the biz for mp2 video and audio, something I can leave to install itself with minimum input from me as I'm not sufficiently Linux savvy to be fannying around with anything complicated or tricky.

Can anyone help please?

---

### Post by dannyboy79 on 2012-11-19
what codec is the file made of? can you install mediainfo and tell me?

---

### Post by keithmac on 2012-11-19
> **dannyboy79 said:**
> what codec is the file made of? can you install mediainfo and tell me?

I don't understand either of those questions.

---

### Post by dannyboy79 on 2012-11-19
if you're unaware of what a codec is then you could have googled it ([http://en.wikipedia.org/wiki/Codec](http://en.wikipedia.org/wiki/Codec)). mediainfo is a program you install and then run so that you can see information about the mp2 video files you have. Banshee should be able to play anything as long as you have the correct decoders installed. Try to install ubuntu-restricted-extras. issue this command in a terminal session:
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by keithmac on 2012-11-19
> **dannyboy79 said:**
> if you're unaware of what a codec is then you could have googled it ([http://en.wikipedia.org/wiki/Codec](http://en.wikipedia.org/wiki/Codec)). mediainfo is a program you install and then run so that you can see information about the mp2 video files you have. Banshee should be able to play anything as long as you have the correct decoders installed. Try to install ubuntu-restricted-extras. issue this command in a terminal session:
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

I do know what codecs are - I didn't know what mediainfo is as I'm familiar with Windows software but not for Linux.  I didn't know there'd be any need to know anything about the mp2 files - I thought mp2 video was just mp2 video....

OK then, I ran that command line and a load of info was displayed as it completed but I can't understand any of the messages and there were several like this:  * "Failed to fetch http://ubuntu.virginmedia.com/archive/dists/natty-security/multiverse/binary-i386/Packages"*

---

### Post by dannyboy79 on 2012-11-19
i am not sure if updates are still supported for 11.04, which would be why it's erroring out. Did it at least install the ubuntu-restricted-extras package?

Did you try to play the file again? I actually use vlc or totem movie player to play my video files.

---

### Post by andrew.46 on 2012-11-19
In fact Natty Narwhal has only recently lost support on 28 October 2012:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

So perhaps before troubleshooting too much you might be best to upgrade at least to Precise Pangolin 12.04 LTS. BTW mediainfo comes in a windows version if you want to have a look:

[http://mediainfo.sourceforge.net/en/Download/Windows](http://mediainfo.sourceforge.net/en/Download/Windows)

---

### Post by keithmac on 2012-11-19
> **dannyboy79 said:**
> i am not sure if updates are still supported for 11.04, which would be why it's erroring out. Did it at least install the ubuntu-restricted-extras package?

Did you try to play the file again? I actually use vlc or totem movie player to play my video files.

Based on the several 'Failed' messages it appeared things didn't work and I couldn't play the videos either after trying your suggestion.  I'd use another player but haven't seen any on offer when I looked at the available downloads.  Maybe I'll just have to use Windows to play these videos which is a pain because Vista is as slow to start up as treacle and that's on the computer I'm wanting to play the videos on.... :(

---

### Post by newb85 on 2012-11-19
Natty is an EOL release, so its repositories have been moved.

Edit your /etc/apt/sources.list file.  Wherever it says "http://ubuntu.virginmedia.com/...", replace it with "http://old-releases.ubuntu.com/...".

---

### Post by keithmac on 2012-11-20
> **newb85 said:**
> Natty is an EOL release, so its repositories have been moved.

Edit your /etc/apt/sources.list file.  Wherever it says "http://ubuntu.virginmedia.com/...", replace it with "http://old-releases.ubuntu.com/...".

I'd love to be able to try the above but I don't have the understanding about how to go about all this - it's your bread-and-butter but I'm just a basic user and more familiar with Windows - it's hard for me to understand what goes where and then what I need to do next...

---

### Post by cwsnyder on 2012-11-20
**Before you attempt anything else:**
Install either Ubuntu 12.04.1 which is a long term support release and will be the same until April 2017, or install the latest release Ubuntu 12.10, good until April 2014.

Your version of Ubuntu is no longer supported, just like Windows 95, Windows 98, Windows ME and Windows 2000 are not supported by Microsoft or most vendors.

Once you have a supported version installed, find Software Center, open it and install ubuntu-restricted-extras package.  You should then be able to play your MP2 videos.

---

### Post by dannyboy79 on 2012-11-20
> **keithmac said:**
> I'd love to be able to try the above but I don't have the understanding about how to go about all this - it's your bread-and-butter but I'm just a basic user and more familiar with Windows - it's hard for me to understand what goes where and then what I need to do next...he couldn't have written it any simplier IMO. First open your sources.list file which is located within the /etc/folder, use the following command (i am assuming you're using Ubuntu, which has Gedit)
```
gksudo gedit /etc/apt/sources.list
```
enter your users password when it asks
once that file is open, use the find/replace function of Gedit, for find, enter 
[http://ubuntu.virginmedia.com/](http://ubuntu.virginmedia.com/)
for replace, enter
[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
Hit enter so it replaces all the [http://ubuntu.virginmedia.com/](http://ubuntu.virginmedia.com/)
locations with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
then save the file and close.
then issue
```
sudo apt-get update && apt-get upgrade
```

---

### Post by cwsnyder on 2012-11-20
**@keithmac:**
Dannyboy79's reply and mine must have happened at close to the same time.

Either follow his advice or mine.  Don't do both!

---

### Post by andrew.46 on 2012-11-21
Looking back I see that the main point of your post has not been addressed :). When you get the repository problem sorted out you could do worse than install SMPlayer and MPlayer to play these files (and perhaps vlc as well). Paste the following into a Terminal window:

```
sudo apt-get install smplayer mplayer vlc
```

If you have a 32bit Ubuntu installation it would not hurt to also install the so-called win32 codecs, but this will not be necessary for these particular files.

---

### Post by keithmac on 2012-11-22
> **andrew.46 said:**
> Looking back I see that the main point of your post has not been addressed :). When you get the repository problem sorted out you could do worse than install SMPlayer and MPlayer to play these files (and perhaps vlc as well). Paste the following into a Terminal window:

```
sudo apt-get install smplayer mplayer vlc
```If you have a 32bit Ubuntu installation it would not hurt to also install the so-called win32 codecs, but this will not be necessary for these particular files.

thank you, Andrew!  Now that's what I call EASY.   I simply copied your text into a terminal window and it ran almost by itself.  Your help was invaluable.  (thanks too to my other helpers)

 I now have functioning SMP  for playing .mp2 video.   I don't know where all the files for that installation came from but if they were acquired via an online source, can I download them as a discrete package to take with me to install on my other laptop?  I may not have a reliable Internet connection where I use that one.

thanks again, Keith   :)

---

### Post by keithmac on 2012-11-22
> **cwsnyder said:**
> **Before you attempt anything else:**
Install either Ubuntu 12.04.1 which is a long term support release and will be the same until April 2017, or install the latest release Ubuntu 12.10, good until April 2014.

Your version of Ubuntu is no longer supported, just like Windows 95, Windows 98, Windows ME and Windows 2000 are not supported by Microsoft or most vendors.

Once you have a supported version installed, find Software Center, open it and install ubuntu-restricted-extras package.  You should then be able to play your MP2 videos.

I *did try* 12.04 but reverted to 11.04 as there were features in the older one I preferred.  I use Ubuntu Linux almost expressly as a quick way to get online for email and browsing - fast start-up, reliable sleep, quick shut-down.  Totally unlike Vista and W7.  11.04 is fine for my simple needs now I can play the video I've recorded from the TV on my Vista computer when we're away in winter.

thanks for your suggestions

---

### Post by keithmac on 2012-11-22
> **dannyboy79 said:**
> he couldn't have written it any simplier IMO. First open your sources.list file which is located within the /etc/folder, use the following command (i am assuming you're using Ubuntu, which has Gedit)
```
gksudo gedit /etc/apt/sources.list
```enter your users password when it asks
once that file is open, use the find/replace function of Gedit, for find, enter 
[http://ubuntu.virginmedia.com/](http://ubuntu.virginmedia.com/)
for replace, enter
[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
Hit enter so it replaces all the [http://ubuntu.virginmedia.com/](http://ubuntu.virginmedia.com/)
locations with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
then save the file and close.
then issue
```
sudo apt-get update && apt-get upgrade
```

There's nearly always a simpler way to explain things.... 

 I couldn't follow the original instructions because I didn't understand fully - I'm a simple user and not familiar working in the terminal page and for me there were a lot of unfamiliar terms.   Your instructions appear less hard for me to but Andrew's suggestion worked fine so I've stuck at that.

thanks for your help  :)

---

### Post by andrew.46 on 2012-11-22
> **keithmac said:**
> thank you, Andrew!  Now that's what I call EASY.   I simply copied your text into a terminal window and it ran almost by itself.  Your help was invaluable.  (thanks too to my other helpers)

Good to hear that the issue is resolved :)

---

