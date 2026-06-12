---
title: "Xubutnu 11.10 random freeze"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-10-11
Hi

I dont know why its happening , But system getting freeze randomly . There is no response from any interface(Mouse/KB).I got irritated to restart my pc and i want a solution for this.

Thanks in advance.

---

### Post by raja.genupula on 2011-10-12
some one pick this please .

---

### Post by cariboo on 2011-10-12
Could you provide us with some relevant information. Is there anything in the logs? Have you run memcheck? What troubleshooting have you tried?

---

### Post by raja.genupula on 2011-10-12
Hi thanks for picking .

I am trying to attach the file but its saying file size too large. could you please tell what specific part i can attach for this .

---

### Post by effenberg0x0 on 2011-10-13
I don't know what files you're trying to attach. .tar.gz limit in this forum is 1MB.
I think it would be of more use to us if you could send us syslog, dmesg and xorg.0.log.
That would go like this if using a terminal:

```
cd
mkdir raja_logs
cd raja_logs
sudo cat /var/log/Xorg.0.log > xorg.txt
sudo cat /var/log/dmesg > dmesg.txt
sudo cat /var/log/syslog > syslog.txt
tar -cvzf rajalogs.tar.gz xorg.txt dmesg.txt syslog.txt
```The tar.gz file will probably be less than 100K. You can upload it here easily. When replying, click on manage attachments / click on browse, select the .tar.gz file on your home-folder/raja_logs and click upload.

Regards,
Effenberg

---

### Post by raja.genupula on 2011-10-13
Hi i have done for dmesg log and it shown me the limitation error.

but now i am compressing the log with tar and attaching now.
 Thanks you.

---

### Post by effenberg0x0 on 2011-10-13
Maybe others here will spot more things. The one thing I see immediately is this:

```
ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  3 05:59:59 raju-xubuntu kernel: [ 1782.112074] sr 2:0:1:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Dec  3 05:59:59 raju-xubuntu kernel: [ 1782.112099] ata3.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 16392 in
Dec  3 05:59:59 raju-xubuntu kernel: [ 1782.112102]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Dec  3 05:59:59 raju-xubuntu kernel: [ 1782.112107] ata3.01: status: { DRDY }
Dec  3 06:00:04 raju-xubuntu kernel: [ 1787.152022] ata3: link is slow to respond, please be patient (ready=0)
Dec  3 06:00:09 raju-xubuntu kernel: [ 1792.136024] ata3: device not ready (errno=-16), forcing hardreset
Dec  3 06:00:09 raju-xubuntu kernel: [ 1792.136035] ata3: soft resetting link
Dec  3 06:00:09 raju-xubuntu kernel: [ 1792.324154] ata3.01: configured for UDMA/100
Dec  3 06:00:09 raju-xubuntu kernel: [ 1792.329700] ata3: EH complete
```

I did get a (temporary) system freeze when I used to have this error. In my case it was worse because the disks were part of a RAID (and the RAID obviously got corrupted). I investigated a lot back then. There are many reasons why this happens. Some common ones are: 
[LIST]
[*]**Broken SATA Device:** Disconnect this drive and see if error persists.
[*]**Bad SATA cable:** Change SATA cables and see if error persists.
[*]**Low-power on SATA Device:** Disconnect a few devices, turn of some lights, secondary fans, etc. Change device to its own PSU or dedicated power line in the PSU (if modular). Switch to more powerful PSU.
[*]**Unsupported Hotplug:** You have removed the SATA cable from device **but** your chipset doesn't allow AHCI/Hotplug (or it is not enabled in BIOS). I doubt this is the problem since you're seeing it right at boot time.
[/LIST]
This is what I would investigate, regarding the error I spotted. See if it fits your setup. If you have any other PSU there, run in parallel, do some testing. As I mentioned, others here may spot different things. But I'll put my money on alternatives 3 and 2, as most likely causes, in this order.

Regards,
Effenberg

**EDIT:** If you search online on how to manually reset the ATA devices, you'll find that you can reproduce the freeze when you do. Or just unplug one unimportant  SATA device while the PC is on (old HDD/ODD, etc), wait for it to unfreeze and run dmesg. You'll see the error I quoted above.[B]

EDIT 2:[/B]
```
EXT4-fs (sda6): warning: mounting fs with errors, running e2fsck is recommended
```
This is not good too. And probably caused by the soft/hard reset to SATA. Fix the filesystem soon, its a priority.

---

### Post by raja.genupula on 2011-10-13
Hi thanks for writing complete possibilities and everything.

but

I am not much aware of Hardware and afraid about this.Is this a serious issue?

---

### Post by effenberg0x0 on 2011-10-13
No, it shouldn't be, not at all. Generally when you buy a desktop it doesn't have top-quality components. The Power Supply Unit (PSU) is a no-brand standard 300Watts / 350Watts one, cheap SATA cables, etc. Then, as you start to demand more from the PC, it's natural to replace the PSU for a more powerful one, from a known brand (like Corsair, etc), get better cables (not expensive), better VGA card, etc. It's absolutely normal. 

Some desktops don't even need upgrades for years. But, in your case, what I see in the logs suggests one of the problems I mentioned. 

Ask a friend that is more used to hardware to perform the tests I mentioned, you'll see that its no big deal. In the worst scenario, you have a broken SATA drive or a weak PSU (in my opinion). This is completely normal. 

Just backup your stuff as soon as you can because, as you've seen in your logs, you already have file system errors in your HDD.

Regards,
Effenberg

---

### Post by raja.genupula on 2011-10-13
Thanks again .
Few months ago i got power problem and I have taken my PC to Hardware repair center & he replaced by new one.

I just wanna know only one thing.is there any possibility for Harddisk crash due to this.

---

