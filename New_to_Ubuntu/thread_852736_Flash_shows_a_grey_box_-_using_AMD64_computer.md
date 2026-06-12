---
title: "Flash shows a grey box - using AMD64 computer"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by g2bandrew on 2008-07-07
When i go on some websites which use flash, the part of the site where
the flash content should be is instead replaced with a grey box. From
searching around, i havn't found a solution to this problem anywhere but
other people seem to have this problem and it seems to relate back to
the fact that i have a AMD64 computer. Reinstalling flash is a quick
temporary fix but its always the same flash applications that break it
and they break it for every other flash application too. Avoiding them
or reinstalling the entire operating system isn't really a realistic way
of solving this problem so does anybody have some idea of what i could
do to fix this?

---

### Post by tjwoosta on 2008-07-07
i use 64 bit on two different machines and 32bit on one

i have no problems with flash on the 64bit machines that dont also occur on the 32bit machine

(sometimes flash will randomly blank out, requiring me to restart firefox but that only happens once in a while and it happens on both 32bit and 64bit)

which flashplayer are you using?

the one that i use and it works is flashplugin-nonfree

you could use the ad block plus add-on for firefox to block the problematic flash apps  (just when you find one click the little block tab that shows up)

---

### Post by samjh on 2008-07-08
I also suffer from this problem, but only on Linux.  On Windows, Flash works flawlessly.

It's probably just a flaw in Adobe Flash player's Linux implementation.

---

### Post by g2bandrew on 2008-07-08
it doesn't happen to everybody on a AMD64 machine, just some. I've had ubuntu before and it didnt happen then.

---

### Post by philinux on 2008-07-08
Try the flash version 10 from adobe.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Seems to work better than version 9. I know it's beta but it's running for me just fine.

Maybe you can post an example of a website that is causing grief and I can check them out.

---

### Post by g2bandrew on 2008-07-08
I think i had flash player 10 anyway but maybe what you've given me is a beta which ubuntu doesn't have yet? I dunno. Could you give me clear instructions on where to put the file or what to i need to type into the terminal exactly to get it working. Just imagine for examples sake that i've put the file they give me on my desktop which is home\andrew\Desktop.

---

### Post by philinux on 2008-07-08
Well lets check first.

In firefox use

Tools>Addons>Plugins

What version flash does it say.

---

### Post by g2bandrew on 2008-07-08
shockwave flash 9.0 r124. So it is that i'm using flash 9, i see.

---

### Post by philinux on 2008-07-08
Download the tar file from adobe.
Extract below for flash 10 install taken from this thread by Kilz
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Flash 10 Beta
Adobe has released a beta of flash 10, and get ready to fall backwards. The Linux version has been released at the same time as the Windows version of the beta.
Beta 2 has been released, and from my limited testing it is way better than Flash 9 is right now. Menu's are no longer hidden behind graphics on some pages, and full screen isn't as slow. Its still poor quality, but at lease it moves.

Before we start, let me make something perfectly clear.
1. This is a beta plugin, expect problems.
2. I will not troubleshoot issues relating to running a beta plugin. Report all bugs here.
3. The instruction are only for Hardy.
4. After reading the above, Click Here acknowledging you understand the above.

Next
1. Save the file to your desktop, if you save files to a different location, drag it to your desktop.
2. Open a terminal and execute the following commands
Removal
```
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
cd ~/Desktop
tar -xzvf flashplayer10_install_linux_070208.tar.gz install_flash_player_10_linux
sudo mv -f ~/Desktop/install_flash_player_10_linux/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```

Restart the browser.

---

### Post by g2bandrew on 2008-07-08
Ok, i done all that but the second last line (sudo nspluginwrapper -i /usr/lib/firefox-addons/plugins/libflashplayer.so) returned the following error:

sudo: nspluginwrapper: command not found

I put your code into that notepad program and closed firefox before i done it. I opened it up when i was done, tried a youtube video and it says:


Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. Flash now doesn't show up in the plugins menu neither.

---

### Post by philinux on 2008-07-08
sudo apt-get install nspluginwrapper

---

### Post by g2bandrew on 2008-07-08
Ok, i done that and it still says i need to install the latest version of flash player.

---

### Post by philinux on 2008-07-08
Close FF

Go into your home folder, press ctrl h to show hidden files.

Go to .mozilla then firefox folder and then the one marked xxxxxxx.default.

Delete the file xpti.dat

Restart FF.

---

### Post by g2bandrew on 2008-07-08
I done that now and it still breaks. Also, the file which i deleted is back again.

---

### Post by stchman on 2008-07-08
> **g2bandrew said:**
> When i go on some websites which use flash, the part of the site where
the flash content should be is instead replaced with a grey box. From
searching around, i havn't found a solution to this problem anywhere but
other people seem to have this problem and it seems to relate back to
the fact that i have a AMD64 computer. Reinstalling flash is a quick
temporary fix but its always the same flash applications that break it
and they break it for every other flash application too. Avoiding them
or reinstalling the entire operating system isn't really a realistic way
of solving this problem so does anybody have some idea of what i could
do to fix this?

This happens every few days on my 64 bit machines.  Just restart Firefox and it should go away.

Remember Flash is buggy on Linux.  Adobe know about it and won't fix it.

---

### Post by g2bandrew on 2008-07-08
> **stchman said:**
> This happens every few days on my 64 bit machines.  Just restart Firefox and it should go away.

Remember Flash is buggy on Linux.  Adobe know about it and won't fix it.

I know a website to test it on is [www.sliderocket.com](www.sliderocket.com) - press login and see what happens. That's one of the sites that breaks flash and for me, it always turns the page completely grey. Does it work for others?

---

### Post by gunashekar on 2008-07-08
Apparently Linus Torvalds himself has the problem on a 64 bit install of Fedora/Redhat
Check this out
[https://bugzilla.redhat.com/show_bug.cgi?id=439858](https://bugzilla.redhat.com/show_bug.cgi?id=439858)

---

### Post by philinux on 2008-07-09
> **g2bandrew said:**
> I done that now and it still breaks. Also, the file which i deleted is back again.

Firefox re-creates it, this is expected behaviour.

Make sure you have libflashsupport installed.

Synaptic or sudo apt-get install libflashsupport

---

### Post by RonKZ on 2008-07-12
Phil, you have been so helpful, but
here running 32-bit Hardon on AMD64, Firefox 3 updated which remains buggy.
sudo apt-get install libflashsupport is a nogo
sudo apt-get install nspluginwrapper is a nogo

would be great if somehow linux had it's own flash-player.  I get nutso with friends who send me to youtube and nothing works.  awwwwwwwww!

---

### Post by vanwarantion on 2009-02-26
bump?

---

