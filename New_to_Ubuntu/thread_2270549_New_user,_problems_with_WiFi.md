---
title: "New user, problems with WiFi"
date: 2015-03-23
forum: New to Ubuntu
---

### Post by CoolishPrune on 2015-03-23
So I am new to Lubuntu. I have 14.10 installed on a Dell Inspiron B130. I have no problems getting wired connectivity until now. I went to Software and Updates and then over to the Drivers tab and tried to Apply Changes to the WiFi hardware. It seemed like the process fail and I did a reboot and the second time the bar completed but never finished. I gave it about 15 minutes and rebooted again. However, now I cant even connect wired or Revert. And that's where Im at.

---

### Post by papibe on 2015-03-23
Hi CoolishPrune.

Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=370108") to download, and run a script that evaluates you network drivers.

After that we can take a look at a lot of details of your network situation.

Regards.

---

### Post by SeijiSensei on 2015-03-23
I'd give the Additional Drivers application a try first.  Lots of Dells use Broadcom hardware which often require proprietary drivers.  The Additional Drivers app will examine your hardware and determine if it needs to download a driver.

---

### Post by CoolishPrune on 2015-03-24
How do I install this 'Additional Drivers'?

I tried the iwconfig after installation. Apparently my Wifi needs configuration.

---

### Post by wildmanne39 on 2015-03-24
I will see if I can make this easy for you since your ethernet quit to.
Open the terminal and copy and paste this command:
```
sudo apt-get purge bcmwl-kernel-source
```
reboot and ethernet should be working now, then do:
```
sudo apt-get install firmware-b43-installer
```
reboot and wifi should be working if not follow posts two suggestion and run the wireless script.
This is just a shot in the dark based on experience since you have not provided and information, please do not try to install additional drivers, I believe you already have them installed and that is why your ethernet stopped working.
Thanks

---

### Post by CoolishPrune on 2015-03-24
omg it worked. thank you so much!!

not saying your moethod wouldn't work, but I did do a fresh install, prior, to get the Ethernet working, however step 2 worked like a charm. Thank you

---

