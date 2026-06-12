---
title: "serious boot issue.. some windows stuff involved"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by carrarin on 2012-08-22
I have a dual boot laptop running MS7 and ubuntu. I was having some issue installing Service Pack 1 on MS7. Did a little research found 0x800f0a12 was the error code MS reported. Went online and saw something which said to set the C:\ drive as active partition. I did that and rebooted. 

Now, after the rebooted I am booted into the grub rescue prompt. 

How do i fix this? If anyone could that would be very much appreciated. 

Thanks

---

### Post by NikTh on 2012-08-22
Hi , 
I think the easiest way is to boot from a Live Cd - Usb of Ubuntu and click "Try Ubuntu" , then open a terminal and apply below commands..** I assume you have a regular boot with windows and not a WUBI.** **[COLOR=Red]If you have a WUBI[/COLOR] (install from inside windows) then [COLOR=Red]_Ignore below._[/COLOR]**

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```at the opened window click on [Recommended Repair] option . 
Reboot to see the results. 
Thanks

---

### Post by YannBuntu on 2012-08-24
(@NikTh: Boot-Repair can help also with Wubi: 
- it allows the user backup its Wubi files (by mounting the root.disk and opening it in a file browser)
- it proposes a fsck on the WUbi filesystem
- it fixes the MBR  )

---

### Post by NikTh on 2012-08-24
Thank you for the Info ! 

I didn't know that.

---

### Post by Mark Phelps on 2012-08-26
> **carrarin said:**
> I have a dual boot laptop running MS7 and ubuntu. I was having some issue installing Service Pack 1 on MS7. Did a little research found 0x800f0a12 was the error code MS reported. Went online and saw something which said to set the C:\ drive as active partition. I did that and rebooted. 

Now, after the rebooted I am booted into the grub rescue prompt. 

How do i fix this? If anyone could that would be very much appreciated. 

Thanks

Did you get this fixed yet?

The problem is most likely because, if the PC came with Win7 preloaded, there was ANOTHER partition in front of the one marked as "C:\" and THAT partition actually contains the boot loader -- and is the one that should be marked as Active.

---

