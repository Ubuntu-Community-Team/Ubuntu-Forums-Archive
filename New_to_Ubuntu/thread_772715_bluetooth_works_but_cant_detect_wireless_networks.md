---
title: "bluetooth works but cant detect wireless networks"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by sayeo87 on 2008-04-28
Hi, first off I'd like to say that I'm very new to Ubuntu but I've tried a few things on my own.

I just freshly installed Hardy 8.04 and the restricted drivers for my broadcom card were already installed automatically. I turned on the wireless switch and the LED DID change from orange to blue (I have a HP dv6000z laptop), but I couldn't detect the wireless network I have at home. The bluetooth manager icon appeared, though, so I tested that and to my surprise it could detect my phone.

I have a broadcom bcm4312 (rev 01) card.

So then I tried "connect to other wireless network" and entered the network name and password. The network manager then shows signal bars in the top taskbar: "Wireless network connection to <networkname> (0%)" and I can't connect to anything when I pull out my ethernet cable.

So where should I go from here? Any help is much appreciated! Thanks!

---

### Post by dokdoom on 2008-04-28
Aside from making sure you have access to the wireless, and making sure your wireless switch is turned on (To find out run 'iwlist scan'). Unless your wirelass network connect is hidden you should be able to left click on your network manager and see a dropdown of available wireless entworks. As I said, if the wireless is hidden then make sure you using the correct settings and passphrase.

---

### Post by sayeo87 on 2008-04-28
OK, iwlist gives me the following, even though my switch was turned on and the LED showed that it was on:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

And no, the wireless network I'm trying to connect to is not hidden. Could it be that I need to get new drivers for my card instead of using the ones that came installed?

---

### Post by dokdoom on 2008-04-28
Perhaps, have you tried to see if anyone was having similar problems with that particular wireless card? It's a shame to hear it simply won't work right out of the box though. My Hardy expereince has thus far been very easy.

---

### Post by sayeo87 on 2008-04-28
Yeah... that's the thing. Because I've hearda few people say that their bcm drivers work out of the box in Hardy, I'm asking around to see if I'm missing anything. I don't want to go through all the ndiswrapper stuff if I don't have to... were those iwlist outputs sure-fire signs that my driver is not working?

---

### Post by dokdoom on 2008-04-28
iwlist scan

Will tell you which wireless networks you card sees. If you ran it and gave that output "I" would bet it is not working properly. Maybe I am wrong but that is how I would troubleshoot. There's always the chance something went wrong during the install but even though I would just reinstall, it is a pretty drastic measure that I would not recomend.

---

### Post by sayeo87 on 2008-04-28
Alright. Looks like it's off to looking for guides then. Do you have any guides to recommend for my specs / situation?

---

### Post by sayeo87 on 2008-04-28
Fixed! I used this very comprehensive guide: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Thanks for your help!

---

