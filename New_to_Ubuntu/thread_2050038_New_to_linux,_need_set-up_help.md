---
title: "New to linux, need set-up help"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by Dasberry on 2012-08-29
Hello,

As the title of the thread says, I am new to linux and ubuntu. I made the switch from Windows 7 after spending the last 3 days trying to fix a problem. I had a lot of help from Overclock.net and I tried everything but it was no use. So out of frustration I decided to switch over to linux after confirming it was not a hardware issue. The switch was going to happen anyway, because Steam will be porting their games/engine to linux in the near future. 

But right now, I need some help setting up my system. If you can answer the questions here that is great, but links to other threads or websites are more than welcome! 

1. How can I optimize my SSD/HDD combo (run in AHCI mode) in ubuntu? 

2. How can I view the space left on these drives? (Like going into my computer on Windows 7)

3. I have a Xonar DX sound card. The drivers in windows 7 allowed me to adjust effects, and various other elements that could make everything sound great. I was able to make adjustments for various types of music, gaming, movies, etc. 

4. Microphone set-up? 

5. How can I redirect my downloads to the HDD instead of them going to the SSD? 


That's all for now. Thanks.

---

### Post by oldfred on 2012-08-29
Welcome to the forums.

Many of us dual boot. It took me 5 years to totally wean myself from XP. Its always that one application that does not run or run well in Linux that makes you keep Windows.  So backup Windows, make repairCD and recovery DVD set.

Not sure about all the hardware issues. Do not know about your sound card.

Best to use Windows to shrink the Windows partition, but Windows works best with 30% free, so do not shrink too much. If dual booting best to create another NTFS shared data partition. Then the system partition does not have to be as large as data is in the shared.

I only have Ubuntu on my SSD, but have all my data on my rotating drives. So SSD is just a boot drive with only the system partitions.

Download the 64bit version and run as a liveCD, check what works. It may even suggest a driver for your sound card or it may just work. I now prefer USB flash drives as they are quicker & reusable

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick). 

Use Windows to shrink the NTFS partition but do not create partitions with Windows, use gparted from the liveCD. It will also show you how much space is used.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

How large are your drives?

From liveCD terminal post this and or screen shot from gparted:
```

df -H
```You can upload screen shots with the little paperclip icon in the edit panel above your message.

---

