---
title: "DVD Drive doesn't work"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by bizghetto2 on 2008-07-26
Hi, I just recently made the move to linux. My computer had a DVD/ Cd Burner prior to the change. I can burn CD's fine but for some reason I can't watch DVDs. I have that Totem Music player, dragon movie player and VLC all on this computer and DVD'S still don't work.... what am I doing wrong? On windows you simply downloaded vlc itself and it played practically eveything. When I put a DVD in the totem movie player comes up and I get a blank screen until it says

error: could not read source or something like that.... VLC just freezes when you try to drop the vobs into it and dragon player plays the first 5 seconds then stops.

---

### Post by bobbob94 on 2008-07-26
You may still need to install some software to watch DVDs. Have you tried the instructions on the ubuntu wiki [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")?

---

### Post by northern lights on 2008-07-26
Have you tried with more than one DVD (i.e. it's not a physical problem with the disc)?

Is the package "ubuntu-restricted-extras" installed? Run ```
aptitude search restricted
```to verify (is there an "i" flag to the left of the package name?). 

If not, run ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by bizghetto2 on 2008-07-26
Thank You!!! The wiki tutorial worked! I already downloaded the restricted package thing and had tried several different dvd's but thank you guys for the help!!!

---

### Post by SpikeBzzz on 2011-10-06
Hello!

I have the same problem. 

I installed **libdvdread4** package and ubuntu-restricted-extras, then rebooted the system with Audio CD in Dvd/CD-Drive. Oh miracle, it worked.. after more than a half year i could hear music playing by DVD/CD Drive. Then I put another CD and it didn't work... neither the first audio cd, which worked a minute a go. I rebooted again but still no results. 

PLEASEE! Help me to make my Drive work again!

---

### Post by proxy.qtz on 2011-10-06
You may need to update the restricted-extras package.

---

### Post by proxy.qtz on 2011-10-06
That, or the disc is region locked to a different region.

---

### Post by bspymaster on 2011-10-06
I'm willing to bet it's the first option.

---

### Post by proxy.qtz on 2011-10-06
> **bspymaster said:**
> I'm willing to bet it's the first option.
Which first option?

---

### Post by arochester on 2011-10-06
Add the Medibuntu Repository and install: libdvdcss2

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by SpikeBzzz on 2011-10-06
> **arochester said:**
> Add the Medibuntu Repository and install: libdvdcss2

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)


nee, dosn't work(

---

### Post by SpikeBzzz on 2011-10-06
> **proxy.qtz said:**
> You may need to update the restricted-extras package.

the system says: ubuntu-restricted-extras is already the newest version.

---

### Post by pqwoerituytrueiwoq on 2011-10-06
try this:```
sudo apt-get install libdvdread4;sudo /usr/share/doc/libdvdread4/install-css.sh
```then try to play it

---

### Post by SpikeBzzz on 2011-10-07
Thanks for your responses. 

The problem is still there. 

I noticed, that CD-Drive react somehow on CD, when I reboot with CD in drive. After that no reaction on any CD or DVD. 

Now I got a new message: 

> **Unable to mount Audio Disc**

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)Yesterday it said: No mount point cdrom0 is found. 

I created  mount point in media folder (via mkdir, what is in fact just another folder, don't know really, how mount points work). But then the system "thought out" some other reason, why it cannot play the audio CD. 

Does anybody know, how to make it work? SOS!

---

