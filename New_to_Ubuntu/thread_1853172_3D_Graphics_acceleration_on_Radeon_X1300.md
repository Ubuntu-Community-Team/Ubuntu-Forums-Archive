---
title: "3D Graphics acceleration on Radeon X1300"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by dlpenguinlover on 2011-10-01
Hello. I am running Ubuntu 10.04 on a P4 2.0Ghz, with 1GB RAM, 40GB w/ Windows XP Pro with Ubuntu installed via WUBI.

I am having trouble with getting the graphics to work. When i installed ubuntu, it came set with normal Desktop Effects which made it really slow.

I plan to set it for Extra desktop effects, (My windows 7 runs 3D no problem, even on the most extreme tasks.)  but can't since my video driver is screwed up.

I do not want to use the ATI driver since that crashed my previous build.

What  should I do to fix this?

---

### Post by angryfirelord on 2011-10-01
Unfortunately, you have what is deemed a "legacy card". ATI at the time in 2009 decided that all cards that were below the Radeon X2000 series would no longer be getting support from the Catalyst package. Therefore, you're stuck with the open-source driver.

The good news is that there has been great progress made on it. However, you're not going to see it in 10.04. You'll have to run at least 11.04 to see the improvements. There were also some speed boosts made with the driver in August, so 11.10 should be even better in that regard.

---

### Post by dlpenguinlover on 2011-10-01
Is this new open source driver caked into 11.04/11.10 os, or is it available as an installable package?

---

### Post by dlpenguinlover on 2011-10-01
Also, Is there anyway that I could keep all of the features/GNOME enviroment features that were removed in 11.04? (Visual effects tab in Appearence)

I downloaded 11.04 and ran it in a virtual machine to try it out and might upgrade when 11.10 comes out.

If I do upgrade, your saying that the driver (open-source) should be able to handle my X1300?

---

### Post by angryfirelord on 2011-10-02
> **dlpenguinlover said:**
> Is this new open source driver caked into 11.04/11.10 os, or is it available as an installable package?
It's already bundled in with Ubuntu. In fact, you should have to do absolutely nothing to use it. 
> **dlpenguinlover said:**
> Also, Is there anyway that I could keep all of the features/GNOME enviroment features that were removed in 11.04? (Visual effects tab in Appearence)

I downloaded 11.04 and ran it in a virtual machine to try it out and might upgrade when 11.10 comes out.

If I do upgrade, your saying that the driver (open-source) should be able to handle my X1300?
The Visual Effects tab was removed because (I'm assuming) that it would have created conflicts with Unity. You may be able to get some of it back by installing the Simple Compiz Config Settings Manager, but I'm not sure.

As for you card, yes, it should work and you should be a lot better performance with 11.04 and 11.10 than in 10.04.

---

### Post by Krytarik on 2011-10-02
> **angryfirelord said:**
> The Visual Effects tab was removed because (I'm assuming) that it would have created conflicts with Unity. You may be able to get some of it back by installing the Simple Compiz Config Settings Manager, but I'm not sure.
In fact, whether Compiz is run or not is now controlled by the session settings. In the case of Unity, since it's a Compiz plugin, Compiz must obviously be run. So, it simply makes no sense to offer an option to disable those, as by doing so, you would kill Unity.

And the other options are - as of Natty 11.04 - "Ubuntu Classic", in which Compiz is enabled, and "Ubuntu Classic (No effects)", in which it's not. Plain simple.

In Oneiric 11.10, things are a bit different, there you got the 'real' Unity session, with Compiz running, and the fallback Unity 2D session. And you can install Gnome Shell, with effects provided by Mutter; and the Gnome Fallback Sessions, in one of which you can run Compiz, the other is with no effects.

And when it comes to changing the settings of Compiz, CompizConfig Settings Manager (package "compizconfig-settings-manager") is the way to go, as Simple CCSM doesn't work with the current version of Compiz anymore.

Greetings.

---

### Post by rakete on 2011-10-07
> If I do upgrade, your saying that the driver (open-source) should be able to handle my X1300? 	

I just installed the daily build (11.10) from yesterday on a Thinkpad T60 with ATI X1300 Graphics...

For now I can say: Desktop Effects work like a charm out of the box. It happens now and then that compiz is not loaded correctly at startup or at userchange and therefore no Unity shows up, I have to restart when this happens. 

I am not planning to install the prop. Driver, since the open-source one does really well.

And just a tip: Newer dist-upgrade, always do a clean install but keep your homefolder.

---

### Post by Krytarik on 2011-10-07
> **rakete said:**
> For now I can say: Desktop Effects work like a charm out of the box. It happens now and then that compiz is not loaded correctly at startup or at userchange and therefore no Unity shows up, I have to restart when this happens.
Nice to hear, generally! :D

And you don't need to reboot, or even relogin, if Compiz isn't run properly at login; just create and keep a launcher for the command
```
compiz --replace
```... on your desktop. I have it like that, for cases in which Compiz crashes, or if I'm playing around with the window managers.

Regards.

---

### Post by Mark Phelps on 2011-10-08
> **rakete said:**
> ...I am not planning to install the prop. Driver, since the open-source one does really well.


That's good -- because there is NO proprietary driver that will work with the ATI X-series and any Ubuntu newer than 8.10.  As already said, these cards have been moved to "legacy" status, meaning, AMD does not write proprietary drivers for them anymore.

---

