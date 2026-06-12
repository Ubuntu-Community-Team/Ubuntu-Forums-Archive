---
title: "Steam Causing System to Freeze (Alt+SysRq+R,E,I,S,U,B doesn't work)"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by TheCause on 2013-02-26
Okay, so I've been using Ubuntu for a few months now (since fall of last year), but I still consider myself a newbie. So this problem started occurring a few days ago, and I've kept trying to test to determine what is wrong. 

When running the beta version (I realize that in itself could be a problem) of Steam for Ubuntu downloaded through the Ubuntu Software Center from the link on steampowered.com, my system will often totally freeze. At first, I will be able to move the mouse, but it will not interact with any of the objects on the screen. A few seconds later, my mouse will stop moving. Once this happens, I have to hard reboot. I've tried Alt+F2 and REISUB, but neither one works. Absolutely nothing I do will get the system to respond after the mouse stops working. I tried running Steam several times, and the same result happened. When not using Steam, my computer seems to run fine. I would like to use Steam, so I started looking up some info.

On their website, I found a **[COLOR=Blue][COLOR=Black][support article]("https://support.steampowered.com/kb_article.php?ref=7493-ADXN-9620")[/COLOR] [/COLOR]**that sounded similar to what was happening to me. It keeps freezing while I'm attempting to download Team Fortress 2. Looking into the file /etc/hosts like they suggested in their only solution, I found that I already had the line they had in my /etc/hosts file. So that's not it (and it seems to be talking about updating the client itself, not downloading games).

Upon further delving, I decided to look at my syslog with Log File Viewer and I found this (Deleted my computer's name between date and "kernel" in case you're wondering where it is.)
```
Feb 26 20:32:05  kernel: [ 8304.073034] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Feb 26 20:32:05 kernel: [ 8304.073042] ata3.00: BMDMA stat 0x26
Feb 26 20:32:05 kernel: [ 8304.073050] ata3.00: failed command: WRITE DMA EXT
Feb 26 20:32:05 kernel: [ 8304.073063] ata3.00: cmd 35/00:40:f8:a4:21/00:02:03:00:00/e0 tag 0 dma 294912 out
Feb 26 20:32:05 kernel: [ 8304.073065]          res 51/84:f1:47:a6:21/84:00:03:00:00/e0 Emask 0x30 (host bus error)
Feb 26 20:32:05 kernel: [ 8304.073072] ata3.00: status: { DRDY ERR }
Feb 26 20:32:05 kernel: [ 8304.073077] ata3.00: error: { ICRC ABRT }
Feb 26 20:32:05 kernel: [ 8304.073095] ata3: soft resetting link
Feb 26 20:32:05 kernel: [ 8304.252370] ata3.00: configured for UDMA/100
Feb 26 20:32:05 kernel: [ 8304.252393] ata3: EH complete
```It prints this about every 1-15 minutes, exactly the same. Without even opening Steam on this boot. I found people with similar errors, often people suggesting that it is either a motherboard or hard drive failing. That's disturbing news to me, especially because I'm not sure how long it has been trying to tell me about it and that I only stumbled upon it because Steam seemed to be messing up my computer. I'm just kind of confused and unsure of how to go about solving this problem. Is it a hardware problem, or is it a problem with Steam, considering that is the only time I encounter any problems that I notice. Because I was curious I looked up some of the individual lines, and specifically the host bus error seems bad. That would indicate that there might be a problem with the SATA bus on the board, as far as I understand.

In case you need any system information here are some specs:
Motherboard: ASUS P4P800S-X; RAM: 1 GB; ASUS (not stock) AH3450 256MB Video Card; Hard Drive: 500 GB SATA. I'm running Ubuntu 12.04.2. Only Ubuntu is installed on the Hard drive. I have 4 Partitions: Swap, Root, Home, and a Data.
 
Any help determining the problem and/or how to fix it would be very much appreciated.

---

### Post by williejones on 2013-02-26
I have no answer for Steam, but when you lock up try **Alt+_Ctrl_+SysRq+R,E,I,S,U,B**

---

### Post by TheCause on 2013-02-26
Well to further investigate, I tried it again and I kept syslog open with Steam running. Sure enough, it froze again. I pressed and held down Alt+**_Ctrl_**+SysRq, and while holding them down pressed REISUB, making sure to leave time between each letter and holding them down for each about a second. No response. I did notice the the errors started occurring more frequently while Steam was running. Instead of printing the error every 1-15 minutes, it printed the error every few seconds.

---

### Post by DuckHook on 2013-02-26
I don't know enough to decipher your syslog. What I can tell you is that your machine is not nearly powerful enough to do the sort of gaming you want. Your MOBO is built for a Celeron/P4 CPU, which is what I suspect you are running with. Your system RAM is barely enough to run Ubuntu itself without any apps. And your Video card is barely capable of supporting Unity 3-D, never mind the GPU-intensive demands of Steam. Even if there was nothing at all wrong with your mobo/HDD, I suspect that your system would choke as soon as you tried to run Steam.

Sorry to be the bearer of bad news.

---

