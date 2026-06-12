---
title: "belkin wireless notebook card-HELP"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by hazman on 2008-05-06
hi,
tried also to get card working to no avail can anyone help?

---

### Post by spiderbatdad on 2008-05-06
[http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide)

---

### Post by hazman on 2008-05-06
my card is f5d7010 would it still work

---

### Post by spiderbatdad on 2008-05-06
chances are it is the same driver. You can check when you go to find the driver. Install ndiswrapper via synaptic. I believe it is called ndiswrapper-utils-1.9 follow that guide for the rest. When your wireless is working, add the word ndiswrapper to the file /etc/modules.

---

### Post by hazman on 2008-05-06
my comps a toshiba plus driver from original cd is installed but sudo modprobe ndiswrapper just hangs there doing nothing

---

### Post by Austin_KW on 2008-05-06
> **hazman said:**
> my card is f5d7010 would it still work

Different versions have different chipsets and drivers;

Mine is ver 3000 and works best with the rt2500 legacy driver from serialmonkey.com

---

