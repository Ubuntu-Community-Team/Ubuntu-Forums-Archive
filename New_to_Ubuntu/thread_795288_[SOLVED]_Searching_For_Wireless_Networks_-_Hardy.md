---
title: "[SOLVED] Searching For Wireless Networks - Hardy"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by dconstruct on 2008-05-15
Hi,

I have an HP 530 laptop, running the latest release of Hardy on Ubuntu Studio and I have the unfortunate Broadcom 4311 (rev 01) wireless chipset with which I have never really been able to work with successfully and easily in previous versions of Ubuntu.

After so much work that I probably couldn't even tell you what ended up being the successful attempt, I finally got my little blue light on.  So, my wireless is active.  I did the Restricted Drivers Manager and enabled the BCM driver that I guess I had installed and it says it's In Use and Enabled.

So.

In Ubuntu Studio, it didn't come with the Network Selector applet so I installed Network Selector from the Add/Remove programs menu.  And, when I go into Network Manager, and click on Wireless Connections, I click Enable Connection and then it asks me for settings information.  And, I don't know the ESSID or the connection configurations for the wireless networks I'm attempting to connect to.  I just want to be able to search for a network and connect to it.  But, it forces me to input an ESSID and whatnot before it will allow me to click OK.  So, I have to cancel it, leaving my Wireless Connections checkbox permanently disabled.  

And, with the Network Selector applet opened and running, I click on Wireless and it never finds an available connection, even when I know one that exists.

Any ideas, or suggestions on how to get this to work properly?  Anything would be greatly appreciated.

Thanks,

Adam

---

### Post by drs305 on 2008-05-15
I am using the dreaded broadcom 43XX without any trouble on hardy using the standard network managers. I had wireless working fine in gutsy and just updated to hardy.  Have you tried installing synaptic's bcm43xx-fwcutter (or b43-fwcutter) to get the firmware?

If that doesn't work, check out the last 3 or 4 posts (# 975 + ) from here:
[http://ubuntuforums.org/showthread.php?t=185174&page=13](http://ubuntuforums.org/showthread.php?t=185174&page=13)

---

### Post by dconstruct on 2008-05-15
The main problem is that Synaptic Package Manager won't open for me.  It says "Starting Synaptic blah blah blah" but it never opens.  Any ideas on how to fix that so I can try to get the b43-fwcutter?

---

### Post by drs305 on 2008-05-15
> **dconstruct said:**
> The main problem is that Synaptic Package Manager won't open for me.  It says "Starting Synaptic blah blah blah" but it never opens.  Any ideas on how to fix that so I can try to get the b43-fwcutter?

If you are working from that machine, have an internet connection but can't use synaptic, try:
```
sudo aptitude install bcm43xx-fwcutter
```
That's the one I have installed on 64-bit hardy

If that one doesn't work, 
```
sudo aptitude install b43-fwcutter
```

---

### Post by dconstruct on 2008-05-15
Wait a sec! I may have done something.  Now, under Wireless Connections, it says "Enable Roaming Mode" so it may be working fine.  Let me reboot and verify.  But needless to say, I'm pretty excited about what the next five minutes will bring.

---

### Post by dconstruct on 2008-05-15
yes yes yes! it worked! thanks so much!  :)

---

