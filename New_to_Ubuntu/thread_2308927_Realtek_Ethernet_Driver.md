---
title: "Realtek Ethernet Driver"
date: 2016-01-06
forum: New to Ubuntu
---

### Post by c10h15n2 on 2016-01-06
Hi. My internet connection drops out every few seconds and then reconnects. My adapter: ***Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller*.** Someone suggested to install the latest version of the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2"). I tried to do that using ***./autorun.sh ***and this showed up:

```

Check old driver and unload it.
Build the module and install
arch/x86/Makefile:138: CONFIG_X86_X32 enabled but no binutils support
Makefile:669: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler
make[2]: *** No rule to make target 'linux/r8168-8.041.00/src'.  Stop.
make[1]: *** [clean] Error 2
make: *** [clean] Error 2



```

I've never installed a driver on Linux before. How should I do it ? thanks.
(*I'm using Ubuntu 15.10*).

---

### Post by Vladlenin5000 on 2016-01-06
Have you checked the obvious first? Like cable, router, etc.
Your Ethernet card is (should be) well supported natively.

---

### Post by c10h15n2 on 2016-01-06
of course I did... I used to have a router and everything worked just fine, but after I removed it and plugged in the cable directly, the internet disconnects and reconnects every few seconds (so I have a working connection for about 15 seconds). On windows works fine (I have dual boot with windows 10), that's how I know the problem isn't the cable. I tried to use **pppoeconf **as an alternative for '*Set up a wireless, broadband, or dial-up connection to the internet*' in Windows but it didn't work. After I tried installing that driver, the '[wired](http://www.omgubuntu.co.uk/wp-content/uploads/2014/02/system-status-wired.png)' connection disappeared completely. By the way, wi-fi works fine. :-s

---

