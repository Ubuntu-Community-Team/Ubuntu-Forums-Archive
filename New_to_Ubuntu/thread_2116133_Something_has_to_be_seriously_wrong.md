---
title: "Something has to be seriously wrong"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by ballzeh on 2013-02-14
Right, I have a high end gaming PC, it is well over the requirements to run Ubuntu, and I am only intending on installing it for a while to obtain some limited edition items in a game (only obtainable through having Linux installed, you see) so I installed Ubuntu (the newer version on the website) and it seemed to have problems running, even simple tasks such as moving windows made the PC freeze.

I gave up and uninstalled Ubuntu, then I thought that I would give it another go on the older long time support version, assuming it was more stable, I was wrong and am having the same experience.

Also, I was trying to download Skype and Steam, for whatever reason both only offer i3 32 bit versions of their programs, and Ubuntu 64 bit doesn't seem to be backwards compatible with 32 bit programs. I am running on an AMD processor as well, if that helps.

---

### Post by ballzeh on 2013-02-14
Another thing, every so often the whole screen changes to console, and it displays three lines of text, saying something along the lines of checking battery (it is a desktop PC) and it switches to the logon screen. When I log in a message box appears saying that there has been an internal system error.

---

### Post by Nr90 on 2013-02-15
Are you installing through WUBI or from disc/usb?
Does a live cd / usb install work?

---

### Post by mastablasta on 2013-02-15
> **ballzeh said:**
> Right, I have a high end gaming PC, it is well over the requirements to run Ubuntu, .
 
doesn't really say much.
 
here is how to post system specs and get help: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
i suspect you need proprietary graphcis drivers installed (since you say it's a gaming PC) and you didn't do that. also do you perhaps have multiple GPU or multiple monitor setup?
 
>  
Also, I was trying to download Skype and Steam, for whatever reason both only offer i3 32 bit versions of their programs, and Ubuntu 64 bit doesn't seem to be backwards compatible with 32 bit programs. I am running on an AMD processor as well, if that helps.
not true. 64 bit ubuntu runs 32 bit application just fine. though perhaps you need certain 32 bit libraries installed to run them. both skype and steam are 3rd party programmes and are not maintained by Ubuntu as far as i know. you can post separate thread for these two applicaitons and people will help you run them. as i know you need to enable partner repositories and install skype from them and it should run fine.
 
[http://askubuntu.com/questions/139279/skype-on-12-04-x64-does-not-start-even-after-purging-and-reinstalling-it](http://askubuntu.com/questions/139279/skype-on-12-04-x64-does-not-start-even-after-purging-and-reinstalling-it)

---

### Post by lisati on 2013-02-15
> **ballzeh said:**
> (the newer version on the website)
<aside>
For the record, the "latest" is currently 12.10.
</aside>

---

### Post by DuckHook on 2013-02-15
> **ballzeh said:**
> Right, I have a high end gaming PC, it is well over the requirements to run Ubuntu...

This is an erroneous assumption. It doesn't matter how "high end" you think your box is--if it has unsupported incompatible components, then it won't run Linux. There are many components built with only Windows in mind whose vendors don't give a hoot about compatibility with Linux. They release no drivers, no low-level specs, and refuse to cooperate with Linux developers. If your box contains such components, you are just out of luck.

This may or may not apply in your case, but it is impossible to determine without proper info. @mastablasta has pointed you to an excellent link with respect to requesting help on these forums.

---

