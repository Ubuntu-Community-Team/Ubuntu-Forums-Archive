---
title: "Cannot get wifi ASUS TP500LA-DH71T"
date: 2015-11-02
forum: New to Ubuntu
---

### Post by Thomas_Alexander on 2015-11-02
*I tried searching the forums for the answer but could not find an easy walkthrough. I'm using 14.04 currently. Everything works except wifi. I can get internet through Ethernet. I tried doing all the updates and went the the additional drivers app and no luck. I came across this page that tells me how to get wifi working, however I would like it dumbed down as I am still fairly new to Linux. Any help would be greatly appreciated. I'm not sure if I should post a link to that site or not. Thanks for your time.*

---

### Post by nevets68 on 2015-11-02
Like you i'm also new to linux. :)    Anyways i googled and found this  -  [http://askubuntu.com/questions/539650/no-wireless-connection-on-ubuntu-14-04-of-my-asus-laptop-tp500la-cj059h-with-wir](http://askubuntu.com/questions/539650/no-wireless-connection-on-ubuntu-14-04-of-my-asus-laptop-tp500la-cj059h-with-wir)

---

### Post by Thomas_Alexander on 2015-11-02
Yeah that's the same site I found but I don't understand what "cd into" means and don't know but little sudo commands in terminal, if someone could dumb down this info for me that would be great. Thanks for the reply. [SIZE=2]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125
that's the site where the info is and seemed to work but I just don't understand it.

[/SIZE]

---

### Post by grahammechanical on 2015-11-02
> **Thomas_Alexander said:**
> *I tried searching the forums for the answer but could not find an easy walkthrough. I'm using 14.04 currently. Everything works except wifi. I can get internet through Ethernet. I tried doing all the updates and went the the additional drivers app and no luck. **I came across this page that tells me how to get wifi working,** however I would like it dumbed down as I am still fairly new to Linux. Any help would be greatly appreciated. **I'm not sure if I should post a link to that site or not.** Thanks for your time.*

Unless we know the instructions that you wish to follow then we cannot explain what they mean.

Regards.

---

### Post by Thomas_Alexander on 2015-11-02
Sorry I forgot to post them, wasn't sure if I was allowed to post links from other sites in here. But I just posted them. Thanks for these fast replies I appreciate it!!

---

### Post by eddiefiggie on 2015-11-02
Hello Thomas!

I too have had some recent wifi issues.  I'll get you caught up on what I've been directed to do.  So far, it has solved my issue.  That being said, there's a "Networking & Wireless" forum on this website which might give you more targeted support.  Here's a sticky thread that might help you get up to speed:  [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

After hitting those recommendations if you still have an issue you'll want to post the result of this command within the terminal:
```
sudo lshw -short
```

From there it will help identify your wifi adapter, etc.

---

### Post by Thomas_Alexander on 2015-11-02
thanks so much, will look into that. My wifi never worked only lan. Its weird I have been using Linux for a while with other computers and unlike windows Ubuntu has always had the correct drivers for me that's why I was shocked when Ubuntu couldn't detect my wifi card. I also had issues with the touchpad but I was able to correct that.

---

### Post by Thomas_Alexander on 2015-11-02
I ran that command and my wifi network card was determined as mt7630e 802.11bgn wireless network ad

---

### Post by eddiefiggie on 2015-11-02
Assuming you already went through this:  [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

There seems to be a known issue with that device.  I found this link.  See if it helps:

[http://askubuntu.com/questions/504718/wlan0-not-showing-up-mediatek-corp-mt7630e-802-11bgn-wireless](http://askubuntu.com/questions/504718/wlan0-not-showing-up-mediatek-corp-mt7630e-802-11bgn-wireless)

---

