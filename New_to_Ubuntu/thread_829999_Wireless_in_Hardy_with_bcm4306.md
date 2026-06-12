---
title: "Wireless in Hardy with bcm4306"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by captgadget on 2008-06-15
I just did a clean install of Hardy and have not download the fwcutter yet. What is the best way to get this wireless installed?

---

### Post by Otto-C on 2008-06-15
Suggest you try the following site:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Have had great success here.

hth
otto-c

---

### Post by captgadget on 2008-06-15
As usual - didn't work

---

### Post by anewguy on 2008-06-15
Could you be more specific in how it didn't work?  Being able to see any error messages you may have encountered, the output from ndiswrapper, etc., is crucial in being able to help you.  :)

Thanks

---

### Post by captgadget on 2008-06-15
OK, I installed fwcutter. When I left mouse click the Network Manager, I can see my wireless. I click that and I get the dialog box Wireless Network Key Required. I fill in the blanks, it tries to connect and then it flips back over to wired.

---

### Post by sam_delta on 2008-06-15
try using wicd instead of network manager
open a terminal and type
```
sudo apt-get install wicd
```
wicd will appear under applications>internet>wicd

sam

---

### Post by anewguy on 2008-06-16
> **captgadget said:**
> OK, I installed fwcutter. When I left mouse click the Network Manager, I can see my wireless. I click that and I get the dialog box Wireless Network Key Required. I fill in the blanks, it tries to connect and then it flips back over to wired.

A small heads-up might be needed here:  in previous versions, if you had a wep key it defaulted to 64 bits, but I noticed lately (I think since Hardy) that the default is 128 bits.  So, if you need a network key, be sure of the number of bits for that key and match it in the window.  If you are unsure, check your router.  I had these same symptoms with my old DSL when I upgraded to Hardy, and it took me a while to realize the default had changed.  Be sure to match to passphrase, hex key or ascii key.  Let us know what happens.

---

### Post by captgadget on 2008-06-16
I'm using WPA Personal.

---

### Post by anewguy on 2008-06-16
Do you have wpa-supplicant running?

If so, and you are sure everything is configured correctly, this is what I would try, given that you can see your network:

- connect to your wireless router (either via Windows or hard wire)
- temporarily make the wireless side wide-open
- try connecting from Linux (e.g., no network key, etc.)
- if connection is successful, add 1 thing at a time - perhaps wpa first and then try connecting.  
- be sure you don't have MAC filtering on such that your address may be being rejected.

Post back what you find out.
  :)

---

### Post by captgadget on 2008-06-19
Absolutely nothing!!! I just don't understand. When I left mouse click network manager, it shows up including my neighbors, but it will not connect. Sorry I'm late in responding but I'm in sales and was gone this week. This isn't a major issue since I can connect wired, it's just the principal. Everything worked until I installed Hardy.

---

### Post by captgadget on 2008-06-19
I can even connect to the router from Linux, but Network Manager won't allow me to connect wireless.

---

