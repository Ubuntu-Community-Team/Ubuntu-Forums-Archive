---
title: "Dell Latitude c840 12.04 LTS wireless connectivity problems"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by DeweyDecimator on 2013-07-05
Manages to get 12.04 LTS installed.  I know it's an old laptop, but it was a freebie and I'm using it to try to learn.  Granted, I seem to have 588 updates to wade through and I'm not positive I'm making any headway there, but that's another problem...

It seems connecting wireless is a common problem.  It clearly sees my network, just asks to authenticate every few minutes and doesn't successfully do so.

I really did try to work through some solutions here, but I'm just not smart enough yet with this stuff to confidently proceed.

I did do the following commands:
dmesg | grep twl
rfkill list all

And got:
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

Will anyone take pity on me and try to help - I'll do my best!

thx

---

### Post by mikewhatever on 2013-07-06
Can you please post the output of the following to identify the wireless hardware:
```
lspci -nnk | grep -iA2 net
```

an output of **ifconfig** would also be nice.

---

### Post by DeweyDecimator on 2013-07-07
lspci -nnk | grep -iA2 net02:00.0 Ethrnet controller [0200]: 3Com Corporatoin 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)Subsystem: Dell Device [1028:00d5]Kernel driver in use: 3c59xAs for the ifconfig command, can you tell me a way to save the output to some sort of text file so I can try to put it on a flash drive to get from that laptop to this desktoip?  It's a lot to type and I might make a mistake,

---

### Post by zDUle98 on 2013-07-07
You can redirect the output to a file:
[http://www.tuxfiles.org/linuxhelp/iodirection.html](http://www.tuxfiles.org/linuxhelp/iodirection.html)

Example:
```
lspci -nnk | grep -iA2 net > somefile
```

This will save the output of the command to the 'somefile' file in your working directory.

---

### Post by mikewhatever on 2013-07-07
> **DeweyDecimator said:**
> 
```
lspci -nnk | grep -iA2 net
02:00.0 Ethrnet controller [0200]: 3Com Corporatoin 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
    Subsystem: Dell Device [1028:00d5]
    Kernel driver in use: 3c59x

```
As for the ifconfig command, can you tell me a way to save the output to some sort of text file so I can try to put it on a flash drive to get from that laptop to this desktoip?  It's a lot to type and I might make a mistake,

Thanks for the output, but that only shows info about the ethernet card - nothing about the wireless.
If plugging a cable is an option, that would  solve the copy/pasting problem.

---

### Post by waynefoutz on 2013-07-07
> **mikewhatever said:**
> Thanks for the output, but that only shows info about the ethernet card - nothing about the wireless.
If plugging a cable is an option, that would  solve the copy/pasting problem.

I've owned 2 of these machines, but it's been 5 or 6 years ago. Almost positive it has a Broadcom in it.

---

### Post by varunendra on 2013-07-08
DeweyDecimator,

Either your output in post 3 is incomplete, or your wireless adapter is on a usb bus. To cover that, as well as to redirect the output to a file, please do -
```
lspci -nnk | grep -iA2 net > wifi.txt
lsusb >> wifi.txt
```
This will save the outputs (instead of showing them on screen) in a file "wifi.txt" in your Home directory.

But even better would be to download and run "wireless_script" as mentioned in [this post]("http://ubuntuforums.org/showpost.php?p=12350385"), and post back the "wireless-info.txt" file it generates.

---

