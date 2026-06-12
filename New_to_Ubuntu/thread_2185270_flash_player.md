---
title: "flash player"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by ron-manley on 2013-11-01
Old fart, lost in an ocean. Trying to install a flash player.  I'm sure it's in here but I can't figure out how to find it. Most of my searches came up 0 , nada.

---

### Post by Impavidus on 2013-11-01
Try installing **flashplugin-installer**. Either use the software centre, synaptic or the terminal, whatever you prefer.

---

### Post by ron-manley on 2013-11-01
I keep getting failed to download (something)

---

### Post by ron-manley on 2013-11-01
I went to applications. put flash installer in search box. starts as if it will work then   failed message

---

### Post by shabuboy on 2013-11-01
Does it have an internet connection? Just wondering the basics...

---

### Post by Mopar1973Man on 2013-11-01
I tend to agree double check you capable of surfing the internet like now during this post. (Personally...) I woud fire up Synaptic package manager and search for flash installer.

---

### Post by Impavidus on 2013-11-02
Also, which Ubuntu version do you use? Can you reach the server? Sometimes servers are down.

---

### Post by protoss96 on 2013-11-02
Do not download flash player from official site. Just run these commands.

First of all be sure you have latest version of Firefox or Google Chrome or Chromium.

```
sudo apt-get update
```
```
sudo apt-get install flashplugin-installer
```

Always keep your repository updated. Thats it.

---

### Post by ron-manley on 2013-11-02
where do I put those commands?  The failed to download message does say "Check internet connection" but I surf and I'm on here.

---

### Post by richardsdma on 2013-11-02
there is an app called "terminal", it is like a cmd for windows.  there you can put those commands. 
you also try to install "ubuntu-restricted-extras" from ubuntu software center, that is the easiest way. 
dont forget, when you type the password in terminal, you won't see anything. just type the pass and hit enter.

---

### Post by syam-nair on 2013-11-02
open up terminal and type

sudo apt-get update
sudo apt-get install flashplugin-installer
please note that "sudo" (known as super user do) is required to give you temporary administrator (root user) privileges.

---

### Post by Impavidus on 2013-11-02
> **ron-manley said:**
> where do I put those commands?  The failed to download message does say "Check internet connection" but I surf and I'm on here.

Then it cannot find the server. What version of lubuntu do you use? Could be relevant. Maybe you can post the contents of **/etc/apt/sources.list**.

---

### Post by protoss96 on 2013-11-03
Just press Ctrl+Alt+T that will open terminal emulator, put that commands in terminal.

---

### Post by durhamwilly on 2013-11-24
After searching half the world for fixes, this is how I got flash plugin working in Lubuntu 13.0.1. Seems lengthly, but really not too bad! Worked for me. And I am no Lubuntu expert, trust me! This is just something I found that worked:

1.) Using Synaptic, do a “complete” uninstall of all flashplayer programs including the flashplayer-installer if it is installed. (This will also remove all flash plugins in any browser on your system).

2.) Install the adobe flash player plugin using terminal:
sudo apt-get install adobe-flashplugin

3.)Now go to this site:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)
and download the following file:
“fp_11.1.102.55_archive.zip” (it’s about 174 MB, and contains the ONE file that you
are going to need .... "libflashplayer.so”). Kinda overkill to have to download the whole zip file just to get one little file, but hey! It’s worth it! 

4.) This "libflashplayer.so” is located in the “flashplayer11_1r102_55_linux.i386.tar.gz” file inside this zip file. (In my case, I need the 32 bit version, so it was in THIS directory inside the archive file: “fp_11.1.102.55_archive/11_1r102_55_32bit/”)

5.) Now we need to replace the existing "libflashplayer.so" file that was installed when you added the flashplugin above using “sudo apt-get install adobe-flashplugin”  .....  In my case, I found the installed "libflashplayer.so" file in my “/usr/lib/adobe-flashplugin” directory.

6.) You need to rename this "libflashplayer.so" to  "libflashplayer.so.backup". However, you must be “Root” to make this change. In my case, I just used  FileManager PCMAN that came installed with Lubuntu. I went to my “/usr/lib/adobe-flashplugin” directory, then clicked  “Open Current Folder As Root” Under “Tools”

7.) Finally, copy the "libflashplayer.so" file from the archive that you downloaded and extracted, into the “/usr/lib/adobe-flashplugin” directory.

That’s it! ...... Flash should now work in any browser on your system. (Well, it did with mine!)
Seems the whole problem was being caused by this one .so file, so getting an older version of it, and replacing the one that was installed was the fix, at least for my system! I'm sure there are other 'fixes' out there, but thought I'd throw the one in that worked for me.

_Where I got most of this info_:

[http://richardappleby.wordpress.com/2012/07/03/getting-adobe-flash-to-work-on-ubuntu-12-04/#comment-1869](http://richardappleby.wordpress.com/2012/07/03/getting-adobe-flash-to-work-on-ubuntu-12-04/#comment-1869)

In part, he says.....
&#65279;"To do this, I downloaded the archive of previous Adobe Flash plugins, which can be found here: [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html). I chose the v11.1.102.55 releases (174 MB), and extracted the Linux version, which is packaged as a shared library called libflashplayer.so. By searching the /usr tree I found that (in my case) there was a single copy of this library already installed in /usr/lib/flashplugin-installer/libflashplayer.so, which I then replaced with the back-level version.”

---

### Post by thatredbird on 2013-11-25
> **protoss96 said:**
> Do not download flash player from official site. Just run these commands.

```
sudo apt-get install flashplugin-installer
```


Just wanted to say thanks, worked great for lubunto 13:10 

redbird

---

### Post by crazypj10 on 2013-11-29
> **protoss96 said:**
> Just press Ctrl+Alt+T that will open terminal emulator, put that commands in terminal.

I've only been using Ubuntu a couple of weeks (although I've had it installed loger)
 The first thing you need to learn is how to open a terminal using  Ctrl/Alt/t (or T)
I used to use the GUI for updates but I read it's faster to use " sudo apt-get update" so I tried it and it seems to be quite true 
Still learning how to do almost anything else though, keep getting error messages as I don't know what I'm doing :wink:
I think I just updated flash player to the latest version (11.2 or something?) I'll have a look at You tube on Firefox and se if I still have quarter screen

---

