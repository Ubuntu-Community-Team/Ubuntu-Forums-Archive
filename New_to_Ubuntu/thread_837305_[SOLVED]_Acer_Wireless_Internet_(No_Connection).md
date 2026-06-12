---
title: "[SOLVED] Acer Wireless Internet (No Connection)"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Johnathannn on 2008-06-22
I have an Acer Aspire 5000 computer... I recently installed Ubuntu Ultimate Edition 1.8 (which is pretty much the same as the newest Ubuntu Distro)... I know that I have a Broadcom Ethernet Card (built in)... Anyways, I can't connect to the internet, because I don't think it recognizes the hardware... I solved this problem before, but now with the new release I guess it's changed... Can someone give me a step by step guide on what to do in order to make my Linux read that I have an ethernet card... Also, I have WEP protection on my wireless internet access point, will that be a problem (I don't really have any info on this)... Please tell me exactly what to do, thanks so much in advance...:popcorn:
Johnathannn

---

### Post by sp0nge on 2008-06-22
What is the chipset in the wireless card? Have you confirmed you are following the correct guide? When I had this issue, I had to go through the process twice once I had the proper guide. For some reason the first take didn't work so well.

---

### Post by diablo75 on 2008-06-22
Before doing anything, I would use your hardline connection (Ethernet) to connect to the Internet and download ALL the updates you can.  This will likely include kernel updates, which may add new hardware detection and compatibility, as well as make your system aware of proprietary drivers for your card if you need them.  Once all the updates are down, use your Restricted Drivers Manager (located in System>Administration) to see if there are drivers that are not enabled that simply need to be "turned on".

---

### Post by Johnathannn on 2008-06-22
The only thing is, when I plug in the Ethernet cable... It keeps saying my network requires a password, and I think I'm putting it in correctly, but it's not working... So, is there anything I can download that will recognize my wireless internet correctly???
Johnathannn

---

### Post by sp0nge on 2008-06-22
Not really. 

Hardwire the machine to the router and check the security settings. disable your router security just for the sake of getting things working.

---

### Post by Johnathannn on 2008-06-22
There's no way I can just download ndiswrapper from another computer, and install it on my Acer laptop? That's what I did before, but it doesn't work now...
Johnathannn

---

### Post by Johnathannn on 2008-06-23
Alright, for this distro, this is what you have to do...
1. Make sure you're connected through an Ethernet Cable to your router (Wired Internet Connection)
2. Open a terminal, and type it the following:
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
3. Everything will be downloaded and extracted automatically, ENJOY!
Johnathannn

---

