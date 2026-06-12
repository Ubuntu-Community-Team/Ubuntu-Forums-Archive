---
title: "Default Wireless Network"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by ionFreeman on 2008-06-26
I'm using NetworkManager, and it connects to wireless networks fine. However, I'd like it to connect to my wireless network. It often seems to prefer my neighbors -- both his and mine are unsecured, and they have different names (his is 'linksys.')

I can changed the wireless network easily enough, but I'd like to switch to my SSID as soon as Ubuntu detects it. What can be done?

Thanks!

---

### Post by niyonk on 2008-06-26
Right click the network tool then choose profiles to delete your neighbor's :)

Or click on the tool, then choose connect to other wireless network 
Cheers! ):P

---

### Post by ionFreeman on 2008-06-26
> **niyonk said:**
> Right click the network tool then choose profiles to delete your neighbor's :)

Or click on the tool, then choose connect to other wireless network 
Cheers! ):P

Thanks! The command caption was 'Edit Wireless Networks...', btw, not 'Profiles.'

---

### Post by stchman on 2008-06-26
> **ionFreeman said:**
> I'm using NetworkManager, and it connects to wireless networks fine. However, I'd like it to connect to my wireless network. It often seems to prefer my neighbors -- both his and mine are unsecured, and they have different names (his is 'linksys.')

I can changed the wireless network easily enough, but I'd like to switch to my SSID as soon as Ubuntu detects it. What can be done?

Thanks!

What version of Ubuntu are you using?

Also for wireless I recommend wicd over network manager.  Follow the instructions to install wicd in Ubuntu.  You can instruct wicd to auto connect to a certain WAP and give it a static IP.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Why are you leaving your wireless connection unsecure?  You do know if someone uses your internet connection for illegal activity you are going to get blamed.  Secure your wireless with WPA or WPA2 if your wireless card supports it.  Use a really long passphrase with uppercase, lowercase, symbols and numbers.  At least 30 characters.

---

### Post by niyonk on 2008-06-26
> **ionFreeman said:**
> The command caption was 'Edit Wireless Networks...', btw, not 'Profiles.'

lol :biggrin:
I was in WinLand back then :(
anyway, glad to see it work out for you :)

---

### Post by ionFreeman on 2008-07-07
> **stchman said:**
> What version of Ubuntu are you using?

Also for wireless I recommend wicd over network manager.  Follow the instructions to install wicd in Ubuntu.  You can instruct wicd to auto connect to a certain WAP and give it a static IP.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Why are you leaving your wireless connection unsecure?  You do know if someone uses your internet connection for illegal activity you are going to get blamed.  Secure your wireless with WPA or WPA2 if your wireless card supports it.  Use a really long passphrase with uppercase, lowercase, symbols and numbers.  At least 30 characters.

I leave my wireless network unsecure so that my neighbors and houseguests can use it without trouble. If I notice spooky looking vans hanging out in front of my apartment, I'll advise them to move forward 50 feet and get much more bandwidth from the bar across the street.

Thanks for the tip! I don't have much patience left for Network Manager, so I'll try wicd.

---

### Post by ionFreeman on 2008-07-08
Installing one uninstalls the other, so wicd is a little dangerous to try out. It didn't connect at work, even to the wired connection, but it worked at home. I've restored gnome network manager.

---

