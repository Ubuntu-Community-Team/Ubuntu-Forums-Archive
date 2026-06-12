---
title: "Dell Inspiron 14z, 12.10, Not suspending"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by surajkr on 2013-04-16
I am having trouble with suspend using Ubuntu 12.10 on Dell Inspiron 14z. Please see attached tar.gz file for the  logs.

---

### Post by Toz on 2013-04-17
Hello and welcome to the forums.

I have moved your post to its own thread.

---

### Post by Toz on 2013-04-17
From your log files:
> pr 16 21:46:49 surajkr-Inspiron-5423 kernel: [20980.934880] PM: Device 0000:09:00.0 failed to suspend async: error -5

Can you post back the results of:
```
lspci
```
...
and the contents of /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```

---

### Post by surajkr on 2013-04-17
> **Toz said:**
> From your log files:


Can you post back the results of:
```
lspci
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)


...
and the contents of /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```
[http://paste.ubuntu.com/5715685/](http://paste.ubuntu.com/5715685/)

---

### Post by Toz on 2013-04-17
Hmmm.
According to your log files, suspend/resume is working:
> Wed Apr 17 07:24:10 EDT 2013: Running hooks for suspend.
.....
Wed Apr 17 07:24:10 EDT 2013: performing suspend
Wed Apr 17 07:24:12 EDT 2013: Awake.
Wed Apr 17 07:24:12 EDT 2013: Running hooks for resume
.....
Wed Apr 17 07:24:12 EDT 2013: Finished.

I think you are having an issue with the backlight of your screen not coming back after resume.

After a suspend/resume, can you: 
1. try adjusting your brightness keys to see if the screen comes back on
2. Try going to the first tty (Ctrl+Alt+F1) then back to the gui (Ctrl+Alt+F7) to see if that works.

If not, try suspending manually by using this command:
```
sudo pm-suspend --quirk-vbestate-restore
```

There are other quirks that you can try. See: ```
man pm-suspend
```
I would suggest also trying:
```
sudo pm-suspend --quirk-vbe-post
```

---

### Post by surajkr on 2013-04-18
Hi Toz,
Thanks for looking into the logs.   I did see the machine suspend once or twice, during last 7 days or so since I bought this.  Subsequent attempts at suspend keep failing and currently all the suspend does is: flicker to text mode sccreen,  print some text messages onto screen and  revert to User Login screen in less than a second.    I think one  of the error messages you quoted is repeated after every suspend attempt on the text screen : 

pr 16 21:46:49 surajkr-Inspiron-5423 kernel: [20980.934880] PM: Device 0000:09:00.0 failed to suspend async: error -5

----

Since you mentioned lspci,  I believe  the PCI device is the On Board NIC card and it is somehow preventing suspend from completing.  I disabled the onboard NIC card from the BIOS and now suspend is working better and I do not see immediate screen lock/user login screen.

It is not clear to me why the NIC card won't let suspend to finish. After disabling the NIC, at least for time being, suspend is working for me and I won't have  to keep the laptop connected to Power, for 24 hrs.

---

