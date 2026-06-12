---
title: "Problems with newly installed Linux"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Castian on 2008-04-30
I recently got rid of Windows and installed Linux (thank god).  Anyway, I'm completely new to Linux, and I have no idea how to do pretty much anything.  My problem right now is that whenever I encounter Flash files on the internet, I get this gigantic play button, and everything lags really bad.  I don't know what's wrong, and I was hoping to get some help.

---

### Post by TheLions on 2008-04-30
you probably don't have flash installed...

to install it open terminal(Programs-->tools-->Terminal)

and paste this (with CTRL+SHIFT+V)

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Castian on 2008-04-30
I tried doing just what you said, and it said it installed flash.  However, I still get the GIANT play button.  :-(

---

### Post by TheLions on 2008-04-30
can you put the screenshot??

also do you have x32 or x64 version of Ubuntu???

---

### Post by Castian on 2008-04-30
I'm going to sound like a noob for this, but I don't know how to do/find out either of those things.

---

### Post by jorik42 on 2008-04-30
for a screenshot, hit the print screen button, located above the backspace button.

---

### Post by Castian on 2008-04-30
Thanks a lot.  Here's the screenshot.

---

### Post by iSplicer on 2008-04-30
When you downloaded the .iso file to burn to disc, did it say amd64 anywhere?

---

### Post by Castian on 2008-04-30
.iso file?  I never downloaded an .iso file to my knowledge.

---

### Post by jken146 on 2008-04-30
scrub that.  sorry.

---

### Post by Castian on 2008-04-30
2.6.24-16-generic

---

### Post by Absorbed on 2008-04-30
I don't suppose you installed gnash? I believe it's a open source version of flash. Perhaps that can be removed and then reinstall flashplugin-nonfree.

---

### Post by master5o1 on 2008-04-30
run `uname -a` in terminal and post out put... This will tell us: kernel version, cpu architecture.

If it has x86_64 on there then ...uh oh XD

---

### Post by randomnick on 2008-04-30
Yep. Thats exactly what my flash looks like in Epiphany browser. You click the giant button, and even if the flash loads, it loads with no picture / no sound, etc. :(

---

### Post by Castian on 2008-04-30
So, I put in the 'uname -a' code, and got this:
2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by jorik42 on 2008-05-01
thats pretty much the same as mine is; i think (though others may want to correct me) that thats an x86 system.  

as for flash, download the plugin from the adobe site
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
thats worked for me on several different computers (though ive never had the exact problem that youre having, but its worth a shot).

---

### Post by Castian on 2008-05-01
I've tried reinstalling flash multiple times now, and I still have the same giant play button problem.

---

### Post by seshomaru samma on 2008-05-01
did you install Flash from the Adobe website?

---

### Post by Castian on 2008-05-01
Yes, I did.  Still doesn't work.

---

### Post by doorknob60 on 2008-05-01
try this:
```
sudo apt-get remove gnash && sudo apt-get autoremove
```

---

### Post by Castian on 2008-05-01
This is what I got when I entered doorknob's code:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Castian on 2008-05-01
Should I uninstall Hardy and then reinstall?  If so, how do I do that?

---

### Post by jorik42 on 2008-05-02
well if you wanted to do that, all youd have to do is put the cd back in the drive and re-install to the same partition that ubuntu is on now.  i dont know if that would solve your problem or not, however.

---

