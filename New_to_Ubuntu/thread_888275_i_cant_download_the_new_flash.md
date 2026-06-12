---
title: "i cant download the new flash"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Kedster on 2008-08-13
like i can select what type of file i want and then does nothing just nothing

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)


like how can i download it

---

### Post by pikabuntu on 2008-08-13
this is much easier :
**sudo apt-get install flashplugin-nonfree**

---

### Post by aysiu on 2008-08-13
What do you mean by *new Flash*? Are you trying to install Flash 10 beta? Or do you just want the most recent official release (Flash 9)?

---

### Post by Kedster on 2008-08-13
kedster@kedster-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for kedster: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java libakonadiprivate0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kedster@kedster-laptop:~$

---

### Post by pikabuntu on 2008-08-13
That means that it is already installed.  Are you not able to watch flash 
videos or are you wanting the newest version?

---

### Post by Kedster on 2008-08-13
yes please that would be awesome please andthank you

---

### Post by Nepherte on 2008-08-13
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) Just run the installer file, that is if you use 32 bit ubuntu.

---

### Post by Kedster on 2008-08-13
i still cant watch youtube videos like one minute i could ant then i couldn't and it told me i needed the new one so i whet but it wouldn't let me so

---

### Post by aysiu on 2008-08-13
Are you using Firefox? Konqueror? Opera? Epiphany?

If you're using Firefox, are you using the Ubuntu repositories version of Firefox, or did you download Firefox from the Mozilla website yourself?

Are you using 64-bit Ubuntu or the normal Ubuntu?

---

### Post by Kedster on 2008-08-13
on the repos version of firefx on a 32 bit

---

### Post by famous3warriors on 2008-08-13
check your about:plugins in fire fox if it shows shockwave flash then you have it isntalled if not then you might have to do is go to synaptic package manager uninstall flashplugin-nonfree and reinstall it.

---

### Post by Kedster on 2008-08-13
well i think it might be firefox because it bean slow and like the buttons on the forum don't work anymore  and it always loggin me out of ubuntu forums and doesn't log into site correctly some times and like i just noticed all this and ohh some java stuff stoped working

---

### Post by alienexplorers on 2008-08-13
Go into terminal and enter:
> sudo apt-get remove flashplugin-nonfree
then goto [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html") and download flash player plugin version 10. Un-tar the file and run the installer.  This will put the flashplugin in your ~/.mozilla/plugins folder in your home directory.

---

### Post by Kedster on 2008-08-13
ok so the plugin is in "add ons" i made a screen shot but i cant add it on here because none of the forums buttons work (code, hyperlink,attachment smilies, and the font stuff) like lots of stuf seems to be goin wrong latly

---

