---
title: "Firefox &amp; Flash Player Plugin"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by cordy74 on 2008-10-17
I know this topic has been done to death but I'm still having trouble viewing flash content in Firefox (mostly want to watch TV show episodes online).  Using about:plugins in the address bar of Firefox shows that I have Adobe Flash 9.0 installed in Firefox.  However, looking in the Synaptic Package Manager I see that Adobe Flash 10 plugin is installed....what's going on here?  I can't figure out which one I am actually using.  Also, no matter which one I might be using I still cannot watch videos online.  Anyone have any ideas?

---

### Post by JeeZiTsDave on 2008-10-17
Well, you are going to have to go to:

[The Flash Player Website]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")

And download the tar.gz file.  Extract it and run the installer.pl file in terminal and follow the instructions.  Any problems, feel free to PM me.

---

### Post by eternalnewbee on 2008-10-17
> **cordy74 said:**
> I know this topic has been done to death but I'm still having trouble viewing flash content in Firefox (mostly want to watch TV show episodes online).  Using about:plugins in the address bar of Firefox shows that I have Adobe Flash 9.0 installed in Firefox.  However, looking in the Synaptic Package Manager I see that Adobe Flash 10 plugin is installed....what's going on here?  I can't figure out which one I am actually using.  Also, no matter which one I might be using I still cannot watch videos online.  Anyone have any ideas?

Try this and see if it solves your problem:

sudo apt-get install libflashsupport

---

### Post by kansasnoob on 2008-10-17
If you're using either Hardy or Intrepid just download the apt install here:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

You'll have to restart Firefox when you're done.

Just FYI the new flash shows up as adobe-flashplugin in synaptic whereas the old version was flash-plugin-nonfree.

---

### Post by cordy74 on 2008-10-17
Thanks for the advice.  I installed the tar.gz file from the flash site as well as the libflashsupport.  Firefox now shows that I am running flash 10.  Unfortunately I still cannot view video online from the major networks.  I don't get an error message or anything, it just gives me a screen where I know the video should be playing and I see nothing.

---

### Post by eternalnewbee on 2008-10-17
> **cordy74 said:**
> Thanks for the advice.  I installed the tar.gz file from the flash site as well as the libflashsupport.  Firefox now shows that I am running flash 10.  Unfortunately I still cannot view video online from the major networks.  I don't get an error message or anything, it just gives me a screen where I know the video should be playing and I see nothing.

Have you tried clicking on it?
Worked on another computer...

---

### Post by cordy74 on 2008-10-18
There's nothing to click on.  For example, on NBC.com I get a mostly black screen with the NBC logo in the top right corner along with some links to HOME, SHOWS, SCHEDULE and COMMUNITY but nothing else on the screen.  I know there should be video as well as play and volume controls on this screen because I have browsed to the same spot using my XP desktop computer.

---

### Post by Settler on 2008-10-19
hello,

i have followed every single tutorial but nothing happens. You can see the image in the .zip file of what a flash website looks like to my pc.

Thanks in advance.

---

### Post by fooman on 2008-10-19
> **cordy74 said:**
> Thanks for the advice.  I installed the tar.gz file from the flash site as well as the libflashsupport.  Firefox now shows that I am running flash 10.  Unfortunately I still cannot view video online from the major networks.  I don't get an error message or anything, it just gives me a screen where I know the video should be playing and I see nothing.

do you still have libflashsupport installed?  ...you *should not* have it installed if it is.

go to synaptic,  find "libflashsupport" and "flashplugin-nonfree" in the list.  right click on them and choose "mark for complete removal".  if you have "gnash" installed...do the same for that.

go to the adobe site ([http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)) and download the ".deb for ubuntu 8.04".

double click the file to install it.

see if that helps.

---

### Post by kagashe on 2008-10-19
> **cordy74 said:**
> I know this topic has been done to death but I'm still having trouble viewing flash content in Firefox (mostly want to watch TV show episodes online).  Using about:plugins in the address bar of Firefox shows that I have Adobe Flash 9.0 installed in Firefox.  However, looking in the Synaptic Package Manager I see that Adobe Flash 10 plugin is installed....what's going on here?  I can't figure out which one I am actually using.  Also, no matter which one I might be using I still cannot watch videos online.  Anyone have any ideas?I did a fresh install of Hardy on my daughter's dekstop yesterday and videos on some site did not work. Then I installed Totem (xine backend) from Add/Remove and it works.

I have also tested on nbc.com just now and it works. I have Flash Player 9.

kagashe

---

### Post by Christmas on 2008-10-19
I think the simplest method to get Flash Player 10 in Firefox is to download the .tar.gz compressed file from their official website, [here](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=DXLUJ), then uncompress it:
```
tar -xzf install_flash_player_10_linux.tar.gz
```
Create the directory ~/.mozilla/plugins/, where ~ is your home directory (e.g. /home/your_user/), then copy the libflashplayer.so library inside that directory. Restart Firefox to take effect.

The last Flash library for Linux is 10.0.12.36, so you this way you will have the last release installed.

If I recall correctly (I'm on Debian), on Ubuntu you can also install it from their repositories using:
```
sudo apt-get install flashplugin-nonfree
```
After you enabled the non-free repositories in /etc/apt/sources.list (or using Synaptic). But it may not be the latest version if you install it this way. I always use the first method, copying it manually.

---

