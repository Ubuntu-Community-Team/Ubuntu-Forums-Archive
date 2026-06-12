---
title: "Installing VLC"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Elect GMax on 2012-12-03
I got tired of switching between my Ubuntu hard drive and my Windows drive every time I wanted to watch and attempt to replicate another 10 seconds of a Youtube video explaining how to install and use ndiswrapper, so I downloaded the video in question and copied it to my Ubuntu drive. Unfortunately, the media player that comes with 12.04 doesn't like flv files, so I decided to install VideoLAN Client. The website has a little button to click on in order to download the version that works with 12.04, but unfortunately, the button doesn't work... at least not when I'm in Windows. According to Google, I can also install VLC by opening the terminal and typing this:
[INDENT] 
[LIST]
[*][COLOR=red]sudo add-apt-repository ppa:videolan/stable-daily[/COLOR]
[*][COLOR=red]sudo apt-get update[/COLOR]
[*][COLOR=red]sudo apt-get install vlc[/COLOR]
[/LIST]
 [/INDENT]But how are these commands supposed to do anything if I haven't downloaded anything and can't get on the Internet because I have no wireless drivers?

---

### Post by Cheesehead on 2012-12-03
You're right. Those commands won't help you without network access.

Also, those instructions are for downloading a PPA (development/testing) version of VLC. Unsupported. Unstable.

1) Open a terminal and type in: [FONT="Courier New"]apt-cache depends vlc[/FONT] That big list is all the packages VLC directly needs *in addition to the VLC package itself* to work. There may be secondary dependencies, too.

2) You can download all those packages to a Win machine at [http://packages.ubuntu.com](http://packages.ubuntu.com). I've done it, and it takes a while.

3) Copy all those packages into /var/cache/apt/archive , then use the command [FONT="Courier New"]sudo apt-get install vlc[/FONT] to see what's missing...or it will install.

Honestly, though, it's probably faster to search and ask here about your hardware problem, or to find a friend with a wired connection for a few minutes. Manually copying packages wastes a lot of time.

Even better, search around for a Linux User Group in your area, and take your system to their next meeting. Good chance a guru can fix it in minutes for free.

---

### Post by ibjsb4 on 2012-12-03
Sounds like you may be skipping a few steps.  If you haven't been on line with Ubuntu then you haven't updated your install and thats a must do.  Also theres a package you need to install for playing A/V, its called restricted extras and once again you need the internet.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And last, VLC.  You can use the method in your post to download it or you can just install the version thats in the software center.

---

