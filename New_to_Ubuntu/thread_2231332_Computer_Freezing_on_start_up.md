---
title: "Computer Freezing on start up"
date: 2014-06-24
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-06-24
My computer starts up but freezes the minute it gets to the Desktop. This doesn't occur everytime, and when it does if I restart it about 3 or 4 times it works eventually. I am running Ubuntu 14.04 and it is a quad-core with 32GB of RAM and ~ 3 Giga Hertz processor. It has a Gigabyte Ultra Durable Classic 4 78LMT-USB3.

---

### Post by DuckHook on 2014-06-25
1. Try using the *nomodeset* option at boot. Instructions [here]("https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Temporarily_for_an_Existing_Installation").
2. Even if Unity freezes, can you get to a command line with <Ctrl>+<Alt>+<F1>?
3. If above doesn't work, does it run reliably from a LiveDVD/USB?
4. Either from working session or from LiveDVD/USB post output of:```
lspci -nnk | grep -iA2 vga
```To confirm this output, also tell us what graphics chipset you believe your system is using.

---

### Post by Bucky Ball on 2014-06-26
Are you using the 64bit version and not the 32bit version?

---

### Post by Paper Pusher on 2014-06-28
Hi Bucky Ball,

          I am running a 64bit version.

---

### Post by Paper Pusher on 2014-06-28
Hi DuckHood,

               The graphics card is a Nvidia 620. I tried to get to the command line after it froze by <Ctrl>+<Alt>+<F1> but didn't have a luck.

---

### Post by Vladlenin5000 on 2014-06-28
**GT**620? If so you need proprietary drivers for optimal performance and for that you need to first add nomodeset as mentioned in the point 1 of post #2. With that hopefully it won't freeze adn it'll allow you to install the required drivers. Then it should be fine.

---

### Post by Paper Pusher on 2014-06-29
Hi DuckHood, 

       This is what I got from the command you gave me: 

axel@axel-GA-78LMT-USB3:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 620] [10de:0f01] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:8a91]
	Kernel driver in use: nouveau
axel@axel-GA-78LMT-USB3:~$

---

### Post by Vladlenin5000 on 2014-06-29
```
Kernel driver in use: [COLOR=#ff0000]nouveau[/COLOR]
```

This means you're using the open-source driver. As I said you need the proprietary nvidia drivers.

---

### Post by Paper Pusher on 2014-06-29
Hi everyone,

            I installed the nvidia drivers and blacklisted the nouveau driver. After that the computer seems to work great with no issues of freezing at all. I appreciate everyone and their help!

---

