---
title: "b43 legacy not working?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by OhioYJ on 2008-07-17
This is driving me nuts. A while back I updated to 8.04, and fought with the wireless for quite a while, and eventually got it to work. This is my card:

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Now I had to re-install Ubuntu, and now I can't figure out what I did before to make it work. I thought I used the old bcm43xx-fwcutter utilities and drivers, but I can't get that to work either this time around.

After much searching on the internet all I'm coming across is to just use the restricted drivers utility in the menus, but that doesn't work for me.

---

### Post by phidia on 2008-07-17
With network problems sometimes you need to start at the begining. 
What does iwconfig and sudo lshw -C network output?

---

### Post by OhioYJ on 2008-07-17
Ok I just did a fresh install, and all the updates, then using the hardware drivers let it download the firmware.

iwconfig output:

> wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"amd"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:79:A4:40   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=83/100  Signal level=-43 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lshw command:

>  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:4e:5f:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.6 multicast=yes wireless=IEEE 802.11g


---

### Post by carandraug on 2008-07-17
Take a look at [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). There's a list of users saying if the method worked and if not which method did the job for them.

---

### Post by OhioYJ on 2008-07-18
Thanks for your help so far guys. I followed the instructions in that link. Now when I do the lshw -C network command it says driver: ndiswrapper...., However when I do a ndiswrapper -l is shows device present, but then it also shows alternate driver:ssb. 

Issueing iwconfig commands does nothing to config the card. My regular LAN connection also stopped working at this point. I know I've tried ndiswrapper in the past with this card, and never could it working. I've always had to use the bcm43xx driver.

I couldn't find my 7.04, or 7.10 discs, the only one I could find was a 6.10, but that one won't let me update (I'm guessing because it's not supported anymore?) I'm just not sure what I did before to make 8.04 work, that I'm not doing now?

---

### Post by carandraug on 2008-07-18
Have you tried get rid of the ndiswrapper and just try?
```
sudo apt-get b43-fwcutter
```
I had a friend with some problems (but he had BCM4318) and all he needed in the end was that.

---

### Post by OhioYJ on 2008-07-18
Ok thanks for the suggestion. I reinstalled Ubuntu again, starting with the fresh install I did the apt-get install b43-fwcutter, and it downloaded the firmware. However it still didn't work? I really think it comes back down to the b43 doesn't work for my card, or perhaps its installing the regular b43 driver, and not the b43 legacy driver? I can't find a way to download and use the older bcm43xx driver? 

This is really frustrating especially since I got it to work once before after messing around with it and now I can't figure out what I did before? Or maybe the driver got updated?

---

### Post by carandraug on 2008-07-18
You should be able to download the old bcm43xx drivers [here]("http://svn.berlios.de/wsvn/bcm43xx"). I found that link [here]("http://bcm43xx.berlios.de/?go=development").
Also, they mention their IRC channel > #bcm-dev, on irc.freenode.net They should be right persons to look for help with that but I'm not sure if they're active there since in the main page they have> This site won't be updated anymore. Please check the [b43 driver page]("http://linuxwireless.org/en/users/Drivers/b43") at [linuxwireless.org]("http://linuxwireless.org/") for up-to-date information.

I went to linuxwireless.org and in the main page they have, about Linux 2.6.26,
> Also, lots of removals this time:

    * the bcm43xx driver
    * the old ieee80211softmac code 
Anyway, [here's]("http://linuxwireless.org/en/users/Drivers/b43") the page about b43 in Linux (your card is in the list of supported). Also, they show a different IRC channel for support> **[COLOR="Silver"]support[/COLOR]**

**IRC channel**
[INDENT]irc.freenode.net #bcm-users (English please)[/INDENT] 
**Mailing list**
[INDENT][http://lists.berlios.de/mailman/listinfo/bcm43xx-dev](http://lists.berlios.de/mailman/listinfo/bcm43xx-dev)[/INDENT]
I hope you know how to get to a IRC channel. If not, Pidgin, albeit not the best for that, does the trick specially because it's probably already installed and you have used it before which you'll save you time. Just create and account with the IRC protocol and then join a chat with that account and in the channel name [COLOR="Red"]don't forget the "#"[/COLOR] (without the "#" it will just say that there's no chat).

---

### Post by OhioYJ on 2008-07-19
Thanks for you help so far. I've been using that site, and tried numerous different ways.

I also tried blacklisting the B43 and SSB driver to make it use the BCM43XX, perhaps I need to do something else though, because after I blacklist those my wireless card doesn't work at all?

I tried the IRC channel but no luck yet.

It just doesn't make sense that I got it to work back when 8.04 was released, but now it doesn't work? It's frustrating, especially since this is just one of a long list of things that no longer work in 8.04 on my machine.

---

### Post by carandraug on 2008-07-19
If you followed all the instructions in that page and can't get it to work then I'm sorry but I have no idea what else you can do. Just don't log out from the IRC channel and wait, like they say, it can take hours. If they can't figure it out, I don't know who will. I noticed that in the topic they say to download the firmware from their site only.
> _DOWNLOAD_ _FIRMWARE_ from [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) ONLY! <- READ CAREFULLY!
Ask and be patient, nobody is paid to answer. Mind the timezone, you could even have to wait for hours.
No bcm4328 support so far, we are working on that. Don't ask. There is NO support!
Everybody (especially bcm4311 users) please use 2.6.24.4 or later
Take note what you need to make everything working this time so you don't have problems next time. I'm planning on making a clean install next month and there's a lot of problems I'm pretty sure I'll bump into. And I too, have no list of that kind.

And of course, when you got it solved, mark the topic as solved and post the solution.

---

### Post by OhioYJ on 2008-07-20
Thanks for your help so far. At the moment I've given up on Ubuntu 8.04, and even worse, had to temporarily install Windows (First time Windows has been on this machine in 2 years).... There was just to many things that did not work in 8.04, the other things where minor enough I could ignore, but the wireless has to work. I know I made it work before but I sure can't figure out why it doesn't work now (I really think something got updated, and now just doesn't work with my card)? Maybe when the next version comes out I'll try it again and see if they've fixed any of these problems. 

I think I may try SUSE, I've been hearing many good things about it.

I really appreciate all your help though.

---

