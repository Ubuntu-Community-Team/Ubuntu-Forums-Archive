---
title: "New, Ahteros AR8132 in Compaq Mini"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by BROM22 on 2012-06-30
Hi, I'm new in using Ubuntu. I used a netbook (Compaq Mini) that came with Windows 7 Starter. I have erased the hard disk and install Ubuntu.
1. I just can get a wired Internet, no wireless. I have a ATHEROS AR8132 PCI-E Fast Ethernet Controller. It's said that I have the physical switch off but I siwtch on and nothing changes. I check the controllers and it'ssaid that I have the wireless controller Broadcom STA and says that it's a propietary software but it's working and in use. Any idea?
2. I feel the netbook a bit slowly, do you know anything faster than Ubuntu 12.04 for netwook?
3. Do you know which programs are the "equivalent" of EVEREST or MozBackUp?

Thank you very much.

---

### Post by BROM22 on 2012-06-30
The wireless controller it's exactly WLAN Broadcom 802.11b/g

---

### Post by BROM22 on 2012-07-05
Hi, anybody can answer any of my questions? Thanks.

---

### Post by SirWhy on 2012-07-05
I know not of a MozBackUp equivalent for ubuntu but this thread may help,  [here]("http://ubuntuforums.org/showthread.php?t=818374").

---

### Post by spcwingo on 2012-07-05
Please post the output of these commands ran from a terminal:

```
lspci
```

and

```
lsusb
```

finally

```
rfkill list
```

---

