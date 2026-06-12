---
title: "More Wireless help"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by nhshah7 on 2008-05-01
I seem to be stuck. I know there are tons of wireless help threads out there, but I can't find my problem out there.  I was poking around in programs and I installed something called "configure network card" (i'm pretty sure). once i installed it, I tried to run it and it failed.  At this point, my internet dropped out.  I tried clicking on the network manager and there was no wireless option upon right click or left click. i ran ipconfig to no avail and iwconfig told me that it sensed my wireless card, but i wasn't connected to any networks (ESSID=""). roaming mode also did not work, and neither did ethernet. please help!

i'm running hardy heron on a hp dv6500 (broadcom wireless card) and i installed linux for the first time 3 days ago. thanks in advance!!!

---

### Post by diablo75 on 2008-05-01
The first thing you should do is check to see if you need to install a driver for your wireless adapter.  Go to System>Administration>Hardware Drivers, and if there is anything in there that is not checked off, check it off.  It may bring up a prompt asking if you want to download and compile (or something like that) which you will want to do.  Hopefully that will enable your card.

If this doesn't work, you might try using [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") to attempt manually setting up the driver with ndiswrapper.

---

### Post by nhshah7 on 2008-05-01
> **diablo75 said:**
> The first thing you should do is check to see if you need to install a driver for your wireless adapter.  Go to System>Administration>Hardware Drivers, and if there is anything in there that is not checked off, check it off.  It may bring up a prompt asking if you want to download and compile (or something like that) which you will want to do.  Hopefully that will enable your card.

If this doesn't work, you might try using [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") to attempt manually setting up the driver with ndiswrapper.

Dear Diablo,
thanks for the quick response. I tried going to hardware drivers, but nothing showed up in the list. I will try setting up the driver manually later. It was working up until I installed the program. Also, I forgot to mention, I uninstalled that program when I realized my wireless wasn't working.  Also, I retried using ethernet, and it works (it wasn't plugged into the router-->faulty clip). and on the network manager, my wireless settings are all still saved (the locations I saved, routers, passphrases, etc).

thanks for the quick response, and I'll get back to this once I try the drivers

~nhshah7

---

### Post by tashmooclam on 2008-05-01
The answer is get a new wireless card. Others may disagree, but I went through this baloney and switched to an intel card (the laptop was a dell). It was easy to make the swap, and cost me $25 on ebay. The linux drivers for intel cards are already in Ubuntu OS. So, it worked and I did nothing except of course, turn it on.

---

### Post by nhshah7 on 2008-05-01
Oh, i forgot one more thing. My bluetooth card works, and i have transferred files with it since the problem. not sure if it's related or not

---

### Post by nhshah7 on 2008-05-01
> **tashmooclam said:**
> The answer is get a new wireless card. Others may disagree, but I went through this baloney and switched to an intel card (the laptop was a dell). It was easy to make the swap, and cost me $25 on ebay. The linux drivers for intel cards are already in Ubuntu OS. So, it worked and I did nothing except of course, turn it on.

well, the card has already worked. it was just that something messed it up, and I don't know how to fix it because i'm a complete linux/ubuntu noob

---

### Post by tashmooclam on 2008-05-01
Sorry, I didn't read your first post carefully. You had wireless working at first then lost it? Sorry, I never even got wireless to work well with my broadcom card. It worked a little bit, enough to drive me nuts.

---

### Post by nhshah7 on 2008-05-01
> **tashmooclam said:**
> Sorry, I didn't read your first post carefully. You had wireless working at first then lost it? Sorry, I never even got wireless to work well with my broadcom card. It worked a little bit, enough to drive me nuts.

Yep. I took a prt screen of the system log when I think it first started having trouble. I can't make any sense of this, though...

---

### Post by diablo75 on 2008-05-01
Here's something stupid I did once:

Forget to check and see if the laptop had a hot-key for enabling/disabling the wireless adapter.  A friend of mine has a Dell laptop which had a bios setting that required the OS to tell the card when to turn on.  I changed this so that the card would always be on, as well as disabled the Fn-F4 binding so if he hit it by accident, it wouldn't disable the card again...  You might check and see if your laptop has such a feature.

---

### Post by nhshah7 on 2008-05-01
> **diablo75 said:**
> Here's something stupid I did once:

Forget to check and see if the laptop had a hot-key for enabling/disabling the wireless adapter.  A friend of mine has a Dell laptop which had a bios setting that required the OS to tell the card when to turn on.  I changed this so that the card would always be on, as well as disabled the Fn-F4 binding so if he hit it by accident, it wouldn't disable the card again...  You might check and see if your laptop has such a feature.

Hm, I doubt this is the problem. I'm currently dual booting ubuntu and vista, but when I boot into Vista, my wireless works fine. i ran iwconfig and ipconfig and teh results are as follows:




nikhilshah@nikhilshah-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nikhilshah@nikhilshah-laptop:~$ ipconfig
bash: ipconfig: command not found

---

