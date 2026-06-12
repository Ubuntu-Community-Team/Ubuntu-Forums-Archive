---
title: "lspci with alternate routing ID"
date: 2012-08-17
forum: Programming Talk
---

### Post by ggankhuy on 2012-08-17
I have a SRIOV NIC with more than hundred virtual NIcs. They all appear as PCI function under lspci command. However the devices and upstream bridge conforms to ARI (alternate routing ID specification). According to ARI FWD spec, the device bits are interpreted as function bits (8:5:3 -> 8:8) therefore 8 bits allocated for function making possible 256 functions per bus. However when I do lspci dump, lspci utility still seem to interpret the 8-bit functions as 5bit devices and 3bit functions. Is it supposed to be this way? Is there any upgraded utility where it will shot it as 8-bit funtions? Thanks,

---

### Post by gordintoronto on 2012-08-17
Have you tried this command: sudo lshw -html > Desktop/config.htm

It's a different approach to displaying your configuration data. The result displays nicely in Firefox or any other web browser.

---

### Post by ggankhuy on 2012-08-22
hmm i dont see lshw-html command available. Do i need to install it?

---

### Post by Hetepeperfan on 2012-08-22
> **ggankhuy said:**
> hmm i dont see lshw-html command available. Do i need to install it?

you probably need to add a space between lshw and -html

like this 

```
sudo lshw -html > ~/Desktop/hardware.html
```lshw with sudo shows more info. -html is an option to lshw. This also shows why people should use the CODE tags with the '#' above.

cheers

---

