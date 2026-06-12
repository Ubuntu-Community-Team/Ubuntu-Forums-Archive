---
title: "Dell D620 wireless problem"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by carldhickman on 2012-07-16
I am a complete novice with Linux being a Windows lemming for years. I have just loaded Ubuntu 12.04 LTS on my Dell D620 laptop. I have a problem in that I have no idea how to get the wireless to work. Wired internet is fine...and the laptop wireless worked with Windows 7. Bearing in mind I only know Windows can someone help with baby steps????:(

---

### Post by Daveth on 2012-07-16
Welcome to the Ubuntu Forum then. A quick net trawl suggests your laptop has a Broadcom 4312 chip on-board. Can you confirm? If so, I think you need to install the "b43-fwcutter package from the Software Centre- it grabs the drivers etc to get the chip working properly.
Be helpful if others can confirm this though.

---

### Post by Lega11yblonde on 2012-07-16
If it's any consolation, I had a Dell D620 and I could never get the Ubuntu wireless to work.  Some suggested that I find a new wifi card that would take Ubuntu.  I decided to get a newer computer that would likely have drivers already installed.  I'm still working on my new install, but the wireless works great!

---

### Post by Risclab on 2012-07-17
Hello,

I really got a problem setting up wlan 
on my Dell Latitude D620, too.

```
lspci 
```revealed that my D620 has the 
Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

Already tried to activate the broadcom STA driver 
via Dash->Additional Drivers which I did. In other
forums I found the suggestions to reinstall the driver
via:

sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install bcmwl-kernel-source 

This still has no effect. Would be very pleased if somebody
could help me. Thanks in advance.

---

### Post by Redblade20XX on 2012-07-17
> **Risclab said:**
> Hello,

I really got a problem setting up wlan 
on my Dell Latitude D620, too.

```
lspci 
```revealed that my D620 has the 
Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

Already tried to activate the broadcom STA driver 
via Dash->Additional Drivers which I did. In other
forums I found the suggestions to reinstall the driver
via:

sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install bcmwl-kernel-source 

This still has no effect. Would be very pleased if somebody
could help me. Thanks in advance.

Have you tried updating the BIOS?

- Red

---

### Post by carldhickman on 2012-07-17
Have lost the thread here...so what is suggested? Alter Bios or b43-fwcutter package...? Or is it a case of this chipset does not work with wireless. In any case I have no knowledge of how to use the b43-fwcutter package. Can someone please enlighten?

---

### Post by Risclab on 2012-07-17
Thank you for your reply. Well I just updated the BIOS from revision A08 to A10. But this takes no effect. I just don't get I mean it worked with maverick perfectly. Yeah I will join the statement from the last post. Could someone explained step by step how to use the b43 package. Would be great. Thanks

---

### Post by bkratz on 2012-07-17
See posts 6 on down of this thread, it will help you

[http://ubuntuforums.org/showthread.php?t=2023302&highlight=bcm4311](http://ubuntuforums.org/showthread.php?t=2023302&highlight=bcm4311)

---

### Post by carldhickman on 2012-07-17
Well I'll give it a go and see what happens...watch this space. From trawlling the web it seems this is a common problem.

---

### Post by Daveth on 2012-07-18
sorry, left you in the lurch.
This is useful for you
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)
- read about half way down and it explains what the package does, but also allow you to see exactly what chip you have, and whether the solution will work or not.

---

### Post by anewguy on 2012-07-18
> **bkratz said:**
> See posts 6 on down of this thread, it will help you

[http://ubuntuforums.org/showthread.php?t=2023302&highlight=bcm4311](http://ubuntuforums.org/showthread.php?t=2023302&highlight=bcm4311)

+1 - it should solve your problem.

---

### Post by carldhickman on 2012-07-19
As a back-up plan does anyone know of a USB wireless adaptor that I can buy that will work with Ubuntu 12.04 with no mucking about?

---

### Post by Risclab on 2012-07-19
I'm either too stupid or it simply wont work. However I followed the thread suggested by bkratz. I did the following:

```

lspci -nn | grep 0280
Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

rfkill list all
0: dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

```

However when I'm doing:
lsmod | grep -e wl -e b43 nothing happens!

In addition this thread suggested to do:
sudo apt-get remove --purge bcmwl-kernel-source sudo apt-get install linux-firmware-nonfree
which I did. Still getting no signal. 
Well I will try the b43 as explained in the link by Daveth.

Thanks

---

### Post by Risclab on 2012-07-19
Ok I did this:

```
Step 1. 
To install b43-fwcutter issue the following command in a terminal (under the desktop menu Applications > Accessories > Terminal) and follow the prompts: 
~$ sudo apt-get install b43-fwcutterSince Ubuntu 11.04 Natty Narwhal additional installation of the package firmware-b43-installer can be helpful and/or necessary, respectively: 
~$ sudo apt-get install b43-fwcutter firmware-b43-installeror, if you need a legacy driver, use: 
~$ sudo apt-get install firmware-b43legacy-installerStep 2. 
Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use. 
```

But I cant choose b43 driver in additional drivers. I can only activate the STA.

---

### Post by Risclab on 2012-07-19
Hi Guys,

I did it. Thanks for your help. Well what I did was installing STA via additional drivers
an then I did:

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

Then detached the wire and restart. Now it works. Awesome. I was getting frustrated. 
Now I can begin to solve my sound problem:P

---

### Post by bkratz on 2012-07-19
Glad you got something working, congratulations!  Please return and use the thread tools above and mark as solved (in case it helps someone else)




Note: Ignore the comment about mark as solved since I just noticed you are not the op.

---

### Post by Risclab on 2012-07-19
No problem.  Anyway thanks again. Hopefully the creator will solve his wlan problems too. 

cheers

---

### Post by Hadaka on 2012-07-19
Hi, The Hawking HWUG1 usb wireless stick works out of the box with dell
laptops, no drivers to load,no tweaking,plug it in and it just works. They
are not cheap and they are not pretty but i have used it to test wireless
access on several different dell laptops, including the D620. you already
know your internal wifi broadcom card works, try again to issue the commands
in post #15 of this thread, from a terminal while hard wired to the net. Also if
you have installed dual boot, try again to access the internet wireless and see
if the function key..Fn/F2 will toggle your wireless on and off.

---

### Post by carldhickman on 2012-07-28
I have found a fix...I have purchased a USB-N10 ASUS WIRELESS-N USB adaptor from Amazon ([http://www.amazon.co.uk/ASUS-USB-N10-Wireless-Adapter-Warranty/dp/B002VGQQAE/ref=sr_1_1?ie=UTF8&qid=1343502519&sr=8-1](http://www.amazon.co.uk/ASUS-USB-N10-Wireless-Adapter-Warranty/dp/B002VGQQAE/ref=sr_1_1?ie=UTF8&qid=1343502519&sr=8-1)) It works straight out of the packet with Ubuntu 12.04 WITHOUT using the installation disc...hurrah! Not solving the original problem bun for £15, a great work around. Any D620 users I suggest going for this:P:P

---

