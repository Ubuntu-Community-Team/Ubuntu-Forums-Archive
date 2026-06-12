---
title: "Wireless Card"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by elint66 on 2008-04-27
I just installed Hardy Heron, and this is my first experience with Ubuntu (or any Linux for that matter).

My wired-ethernet is working fine, but I am having wireless problems. 

I did lspci, and I'm getting:

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

as my wireless controller. I have Dell E1405.

I tried this already ([http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)), but it didn't work. Either it's not the right one, or I did something wrong.

If it's the latter, let me also say:
-- I copied and pasted the code as shown. Wherever I was supposed to enter a custom directory path, I did not, because I don't even know how to get that in Ubuntu. If that link is indeed the right one for me, could you please also tell me how to clear up any remnants of my previous try so I can try again?

Thanks in advance.

---

### Post by master5o1 on 2008-04-27
This can be considered a last-effort attempt to get your wireless working, but it is a useful method.

You can try using ndiswrapper to 'wrap' your Windows wireless driver into a linux useable driver.

System>Administration>Synaptic Package Manager

Search for `ndiswrapper` and mark all three that apply

Or:

Applications>Accesories>Terminal and type:

```
sudo apt-get install ndiswrapper-common ndisgtk ndiswrapper-utils-1.9
```

---

### Post by Prospero2006 on 2008-04-27
It's a dell laptop?

I had success installing this .deb file on a Latitude d510.
I can't remember where I found it, but it works on my model:



[http://www.imakmud.com/bcm43xx_compwiz18.1-all.deb](http://www.imakmud.com/bcm43xx_compwiz18.1-all.deb)

Let me know if it works. Reboot after install and run:

```


iwlist scan

```

Prospero

---

### Post by elint66 on 2008-05-03
My wireless is down for now, but it seems that I have everything working. Wi-Fi radar detects nearby wireless networks (haven't tried connecting yet because mine doesn't work, and all the neighbors' ones are secure)

So I just used Hardy's recommended downloaded that automatically fetched and ran the necessary firmware after the driver installation.

---

