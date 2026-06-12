---
title: "Help with wireless networking and resolution."
date: 2008-04-29
forum: New to Ubuntu
---

### Post by i_am_tek on 2008-04-29
Hey everyone.  I just recently installed Linux (Ubuntu) again after maybe 2yrs or so.  When I used Linux before, I was connecting via Cat5.  Now, I'm using a wireless home network and I'm having some problems detecting the router.

I am using Ubuntu 8.04 on my HP Laptop.  The laptop is standard with HP's WiFi 802.11 etc. etc.  What are the steps that I need to do in order to get my laptop connected to the internet via wireless connection?

Also, I can't remember the files that you edit to add in new resolution and I forget where those files are located.  Any help would be appreciated.

Thanks

---

### Post by bilal.17 on 2008-04-29
For resolution check this thread [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

as for the wireless is the wireless card detected and can be enabled from hardware drivers, if not please provide the name of the card

---

### Post by i_am_tek on 2008-04-29
It's an Atheros Comm. card.  A friend of mine says that it's well supported so I should be able to find information on it.  No luck as of yet.

---

### Post by bilal.17 on 2008-04-29
which model of the card is it

---

### Post by i_am_tek on 2008-04-29
Not sure.

When I do a iwconfig or ifconfig, it does not show my ath0 setting.  Any ideas what is causing this?  The internet works fine with Ethernet, now.  Any suggestions?

---

### Post by i_am_tek on 2008-04-29
Oh, I did an lspci -v and the return was AR242x 802.11abg Wireless PCI Express Adapter.

---

### Post by bilal.17 on 2008-04-29
well it looks like Atheros cards arent officially supported in Ubuntu [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
But if you can find the model of the card then it might work with ndiswrapper

---

### Post by bilal.17 on 2008-04-29
check these 2 threads [http://ubuntuforums.org/showthread.php?t=766529&page=2]("http://ubuntuforums.org/showthread.php?t=766529&page=2")
[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

---

