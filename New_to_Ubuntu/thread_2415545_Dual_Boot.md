---
title: "Dual Boot"
date: 2019-03-27
forum: New to Ubuntu
---

### Post by seanpruitt on 2019-03-27
I currently have Ubuntu 18 installed on a server with 4 drives raid 5. I want to be able to temporarily boot in windows 10 for Adobe premiere. I don't like the idea of wine or virtual box as performance is lost.

I have an external ssd for use of win 10 boot. I'm afraid of losing data or possibility raid settings by booting in windows. If I install win 10 on separate ssd vs internal ssd ubuntu os will that effect raid settings?

If you have a better way please advise.

Thx!!

Sean

---

### Post by 1clue on 2019-03-27
Almost all newer (last 5 or 10 years) hardware has hardware features to implement virtualization. We can help you if you give us details about your cpu and motherboard, but long story short it's unlikely that using a properly created/configured VM will provide any detectable slowness.

Is your Windows license for something that came with the box, or a separately purchased license? There's a reason I'm asking: If you bought Windows separately, off-the-shelf or from a website, then you CAN install it in a VM. If it came pre-installed on a computer, then you MUST run that version on the bare metal. It won't work inside a VM.

The reason I'm trying to convince you to use a VM is because when you dual-boot, you can't access functionality on the OS you're not running. If you have a VM then you can continue to use Ubuntu and also have access to your Windows system whenever you want.

If you could provide the output of **sudo lshw** surrounded by code tags, it would be most helpful.

Thanks.

---

### Post by crip720 on 2019-03-27
Do you need to use Premiere or could you learn to use one of the many Linux alternatives for it.  I just hate when I want to use windows fast, and have to wait for updates to install.

---

### Post by 1clue on 2019-03-27
BTW, if you boot into Windows on the bare metal, it will recognize that there is a RAID card and most likely ask if you want to initialize the drives.

If you configured the system for RAID by formatting them using the RAID firmware, then Windows will recognize that you have a RAID card with RAID5 and 4 drives, but it won't recognize the formats on there and so it will want to format them.

If you used software RAID, then Windows has no idea what that is and it will want to format all 4 drives as individual devices.

---

