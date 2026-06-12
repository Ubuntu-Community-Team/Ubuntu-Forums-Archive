---
title: "Network Settings"
date: 2018-11-19
forum: New to Ubuntu
---

### Post by dannyk2 on 2018-11-19
I am running Ubuntu 18.10 and would like to find all my network setting from the command line if possible. 
So, can someone tell me how i might find my IP Address and all the other network settings please.

---

### Post by Dennis N on 2018-11-19
command **ip address** will disclose the ip address of connected device (and more). look at the man page of **ip** command to explore other options.

---

### Post by mitesh.agrwl on 2018-11-19
To find the network configuration : **$ ifconfig -a** 

To check the interface card settings: **$ ethtool <interface-name>**

---

### Post by Dennis N on 2018-11-19
**ifconfig** isn't available by default in 18.04 or 18.10 - you would need to install the **net-tools** package to have it. The new kid on the block is **ip**.

---

### Post by SeijiSensei on 2018-11-19
I find it annoying when standard tools like ifconfig, which have been used for decades, are removed from distributions. Saving space isn't a justification for omitting a program that takes up just a few kilobytes.

---

### Post by angisky on 2018-11-19
> **SeijiSensei said:**
> I find it annoying when standard tools like ifconfig, which have been used for decades, are removed from distributions. Saving space isn't a justification for omitting a program that takes up just a few kilobytes.

It's not that they are trying to save space it's that ifconfig is no longer supported and is becoming less compatible with newer network tools. ip is what is supported now.

---

