---
title: "Problem with flash plugin non free"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by karthikophobia on 2008-09-15
Hi
I installed tried installing flashplugin-nonfree on my Hardy. But when i try to open a site with flash content, a white block is displayed in the place of the flash content and the browser crashes when I clac on it. I also installed libflsahsupport but it did not work.

plz help

thanq

---

### Post by dhtseany on 2008-09-15
Hi,
I could be wrong but I don't believe you will get a response for this one only because it's a "nonfree" addon. When possible you should try the totally free alternatives first and if they don't work move on the nonfree ones.

Peace
Sean

---

### Post by forger on 2008-09-15
@karthikophobia:
Do you have 32-bit or 64-bit Ubuntu installed?
After you installed flashplugin-nonfree, did you close ALL windows of the browser and restart it?

---

### Post by manishtech on 2008-09-15
> a white block is displayed in the place of the flash content and the browser crashes when I clac on it
You meant you tried to click on it? It crashes? Try uninstalling **flashplugin-nonfree** package and install **gnash**

---

### Post by eru777 on 2008-09-15
try this
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by karthikophobia on 2008-09-15
> **forger said:**
> @karthikophobia:
Do you have 32-bit or 64-bit Ubuntu installed?
After you installed flashplugin-nonfree, did you close ALL windows of the browser and restart it?

I have a 32-bit ubuntu installed. And yes, i restarted my browser.

---

### Post by karthikophobia on 2008-09-15
> **manishtech said:**
> You meant you tried to click on it? It crashes? Try uninstalling **flashplugin-nonfree** package and install **gnash**

sry for the typo, I meant click on it.

---

### Post by Tatty on 2008-09-15
Unfortunately flash support in linux is currently rather poor.  I regularly get problems with white boxes in web pages too.  Usually this happens when more than one page is open which requires flash (myspace and youtube dont work well together for example).

Sometimes though it happens even when no other pages are open, but usually this is fixed by closing all firefox windows and trying again.

Is this the case for you, or is it simply all the time, with any flash?


There is some hope for flash in the future though, as adobe have opened up lots of technical specifications for flash, which should help the open source implementations (such as gnash) get up to speed with the current flash version.  So you may want to try out gnash to see if it suits for you.

---

### Post by karthikophobia on 2008-09-15
> **eru777 said:**
> try this
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I tried it. Now the browser no longer crashes but still only white space is displayed

---

### Post by kauboy on 2008-09-15
I've had the same problem earlier, its quite common. I have the solution on a pdf file, but I'm having my own problems booting Ubuntu now, that I'm unable to help you. Hope I get my Ubuntu back fast, then I'll let you know the exact procedure that got my Firefox display flash.

---

### Post by karthikophobia on 2008-09-15
> **Tatty said:**
> Unfortunately flash support in linux is currently rather poor.  I regularly get problems with white boxes in web pages too.  Usually this happens when more than one page is open which requires flash (myspace and youtube dont work well together for example).

Sometimes though it happens even when no other pages are open, but usually this is fixed by closing all firefox windows and trying again.

Is this the case for you, or is it simply all the time, with any flash?


There is some hope for flash in the future though, as adobe have opened up lots of technical specifications for flash, which should help the open source implementations (such as gnash) get up to speed with the current flash version.  So you may want to try out gnash to see if it suits for you.

I get get the white block all the time.

---

### Post by manishtech on 2008-09-15
> Unfortunately flash support in linux is currently rather poor.  I regularly get problems with white boxes in web pages too
Exactly, once people used to face more problems on 64-bit since flash for 64-bit linux wasnt available. I had heard people using ndiswrapper for installing it (god knows how, havnt used ndiswrapper).
I think its time for Adobe to open up specs and relax its license even more, otherwise silverlight will catch up in the long run.

---

### Post by Bucky Ball on 2008-09-15
Check out my post on this thread (second one) to download and install flash10:

[http://ubuntuforums.org/showthread.php?t=917488](http://ubuntuforums.org/showthread.php?t=917488)

---

### Post by karthikophobia on 2008-09-15
> **Bucky Ball said:**
> Check out my post on this thread (second one) to download and install flash10:

[http://ubuntuforums.org/showthread.php?t=917488](http://ubuntuforums.org/showthread.php?t=917488)

Still does'nt work

---

### Post by Bucky Ball on 2008-09-15
You tried both, line by line not copy and paste all at once?

---

### Post by Tatty on 2008-09-15
Adobe have changed the download link since your post Bucky :)

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz)

This is the new one from the [download page]("http://labs.adobe.com/downloads/flashplayer10.html").

---

### Post by philinux on 2008-09-15
> **dhtseany said:**
> I could be wrong but I don't believe you will get a response for this one only because it's a "nonfree" addon. When possible you should try the totally free alternatives first and if they don't work move on the nonfree ones.

Non of the free ones work for me or ever have. The non-free from synaptic works ok but occasionally I get a no show. Closing and reopening the browser fixes it. I think it's better in Intrepid with the version 10 - 525 version.

---

### Post by Bucky Ball on 2008-09-15
Thanks Tatty. Should it look like this?

```
cd /tmp
wget -c [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz)
tar -xvzf flashplayer10_install_linux_081108.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

Cos that is what I have on that link in case the first one doesn´t work.

[http://ubuntuforums.org/showthread.php?t=917488](http://ubuntuforums.org/showthread.php?t=917488)

---

### Post by karthikophobia on 2008-09-15
> **Bucky Ball said:**
> You tried both, line by line not copy and paste all at once?

I tried both, i pasted it line by line

---

### Post by philinux on 2008-09-15
In firefox use Tools>addons>plugins. Maximise the window and print screen it.
Post the result.

---

### Post by vethunt on 2008-09-15
Had the same problem, couldn't find a fix - installed opera - everything fine - not a fix, but a workround in the meantime.

---

### Post by karthikophobia on 2008-09-15
Sry for the wrong screensht

---

### Post by forger on 2008-09-15
> **karthikophobia said:**
> I have a 32-bit ubuntu installed. And yes, i restarted my browser.

Try purge it completely and then reinstall it:
```
killall -9 firefox
sudo apt-get purge flashplugin-nonfree
rm -rf $HOME/.macromedia
sudo apt-get install flashplugin-nonfree

```

---

### Post by philinux on 2008-09-15
> **karthikophobia said:**
> Sry for the wrong screensht

As you can see you got flash installed twice this will cause conflict.

You need to purge all flash and then reinstall just the one. Non-free.

If you type

```
about:plugins
```

Into the address bar of firefox it will show in detail which flash you got installed.

---

