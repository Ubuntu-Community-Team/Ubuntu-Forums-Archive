---
title: "It worked in PCLOS, but not in Ubuntu 8.04"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Koffee Kid on 2008-05-27
Hi, In frustration of Internet Sharing intermittently breaking down, I downloaded and installed 8.04. I find I can't share my internet connection to 2 XP machines.I use two NICs, 1 for internet, 1 for LAN network.

 I use Wine and like to run Steinbergs Wavelab and Winamp. Both aren't functioning properly. In Wavelab, anytyhing recorded, plays back fast and is full of clicks, and now I've lost recording ability. Winamp, installed 20mins ago, doesn't open now, after opening twice.

 Oh, and I have Untitled window in my panel bar at the bottom of the screen. Which won't Close unless I log out and back in again.

Mike:confused::confused:

---

### Post by sayakb on 2008-05-27
Give a try to [XMMS]("http://www.xmms.org/") and [Audacious]("http://audacious-media-player.org/index.php?title=Main_Page") as Winamp replacements. [Here]("http://appdb.winehq.org") is a list of apps Wine can run.

---

### Post by sayakb on 2008-05-27
> **Koffee Kid said:**
> Oh, and I have Untitled window in my panel bar at the bottom of the screen. Which won't Close unless I log out and back in again.

Can you post a screenshot for that?

---

### Post by Koffee Kid on 2008-05-27
Hi LinuxIsInnovation, I loaded audacious and tried to record its stream and audacious kept buffering. I like to record streams now and again, I tried streamtuner, but it wouldn't stream anything????
XMMS has not installed???

I think I need some sort of understanding of my soundcard mixer. I have a Creative Soundblaster live 24bit 96 khz card. In Micro$oft, I was able to record what you hear, what would be the equivalent to that?

Snapshot included, thanks.

Mike:guitar:

---

### Post by Koffee Kid on 2008-05-27
Now I can't get Audacious to work, it keeps fadeing dark???

Mike:confused:

---

### Post by Koffee Kid on 2008-05-27
Audacity closed by itself.

Mike:confused:

---

### Post by Koffee Kid on 2008-05-27
I take it this Linux is buggy??

Mike:mad:

---

### Post by Koffee Kid on 2008-05-27
help centre has opened up twice. do i have to reinstall? AGAIN:mad::mad::mad::mad:

---

### Post by brcre on 2008-05-27
Not that this helps with your problem:
   But I can't record with Audacity and Sound Recorder.  My issue sounds the same as what you are experiencing.  Program fades dark and constantly tries to start, but never does.  I've never had it crash or exit out on it's own it just stays dark until I finally force it to quit.  I've tried adjusting it's settings and that doesn't help.  I had an error similar to this once before and it turned out to be the kernel, but I've recently installed the updated *.24-17 Generic Kernel and that didn't change anything from the *.24-16 Kernel.  I guess I could try building and installing my own...
   I hope you find an answer and it works for me too!

---

### Post by Koffee Kid on 2008-05-27
Anyone?

Mike

---

### Post by brcre on 2008-05-29
Mike,
  I have audacity working on my system again.  Maybe this will help you.
First thing I did was compile my own audacity-src-1.3.5.tar.bz2 and after a lot of package installations...it doesn't work so if you were thinking that might be an answer for you I would suggest not doing that.  Go back to the last stable version and download that: audacity_1.2.4b-2.1_i386.deb (I couldn't get a source version of the file-bad luck at the time I tried or maybe it's not available.  I don't know for sure)

Before audacity would install I was required to download and install these two packages in this order:
[http://packages.debian.org/etch/i386/libflac7/download](http://packages.debian.org/etch/i386/libflac7/download)
[http://packages.debian.org/etch/i386/libflac++5/download](http://packages.debian.org/etch/i386/libflac++5/download)
  Once those were installed audacity did install and my initial recording test worked, so it appears to be working.
[http://packages.debian.org/etch/i386/audacity/download](http://packages.debian.org/etch/i386/audacity/download)

Once you have these files downloaded, use Nautilus to go to where they are downloaded and right click on the files one at a time and choose Open with GDebi Package Installer.

Now that I have it working I didn't try a lot of troubleshooting to see if I could get the beta version working.  Such as the possibility that having libflac7 and libflac++5 installed now might make the beta version either work, or compile different and then work.  I'm just happy that what I have now works just like it use to.

Ubuntu Release: 8.04
Kernel Linux 2.6.24-17-generic
GNOME 2.22.2
Memory: 2.0 GiB
Processor: AMD Athlon(tm)
Brent

7/3/2008: Try installing this package: libgtk2.0-dev in synaptic package manager.  This should be the missing link to make Audacity work without building it yourself.

---

