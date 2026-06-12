---
title: "USB HDD off for Grub"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by crip720 on 2013-06-22
I have a Seagate 1TB USB Hardrive that seems to power off when the grub screen comes on the laptop.  I therefore cannot boot to the Ubuntu OSs on it.  The boot repair script is on paste.ubuntu.com/5791247/.  The USB HDD seems to power on with the computer, and after I choose a partition on sda[internal].  It used to do this to me before, but only on restarts, not power off then turn on.  I have an Acer 5537 laptop, but the Bios is quite basic[simple].  Thank you for your help.  Colin  More info took wireless mouse off , got these errors; 1] no such device, 2] Hd1 cannot find C/H/S values, 3] load kernals first.

---

### Post by dino99 on 2013-06-23
That seems a bios settings issue
Check that your installed bios is the latest

---

### Post by oldfred on 2013-06-23
Is USB drive powered from USB port on laptop or separate power supply? Some laptops do not have enough USB  power for hard drives??

Boot-Repair asked if sda was external, it should have asked it sdb was external. So you install the grub for the install on sdb into the MBR of sdb.

Many BIOS systems seem to have issues booting very large / (root) partitions on USB external drives. Better to have a smaller 25GB  / fully inside the first 100GB of the external drive or separate /boot at beginning of drive. You then can use rest of drive for /home or data partition(s). If dual booting with Windows a shared NTFS data partition is often a good idea.

---

### Post by crip720 on 2013-06-23
The USB is on separate power.  I was wondering about when Boot-Repair asked about sda, I said no to the question.  I had a another Seagate 1Tb USB drive[with large partitions on it]  and it always worked perfectly, til recently [input/output errors].  This seems be on all the time[green light on], exccept when I select it from grub[green light is off]  I just installed Ubuntu 13.04 64b on it the other night and have not been able to boot to it.  Thank you for your response.  Colin

---

### Post by crip720 on 2013-06-23
I finally got the USB HDD to boot.  Did not do any thing different,  do not know if I just got luckly or what.  Any ideas on how to keep it booting up, I would like to know.  The light is flashing on and off now , I guest it means it is reading/writing to hard drive.  If you would like more info please let me know what you need.  Not solved yet, but working.  Thank you,  Colin.

---

### Post by oldfred on 2013-06-23
Something that is intermittent is the most difficult to resolve. 

But I would suspect some sort of hardware issue. 
Is connection tight? 
Power supply even if separate good? 
Not sure what else?

---

### Post by crip720 on 2013-06-23
Thanks Oldfred, I kinda firgure that.  I will try it for the meantime,  and let you know.  Is there any way to mark this tread as waiting or something,since it problaly won't be solved soon?  Thanks for your time.  Colin

---

### Post by oldfred on 2013-06-24
While we promote users posting as Solved so others can find similar issues with solutions, just leaving thread is ok. If issue is found not to exactly match current title, then better to start new thread with better title to attract those who may know more about that issue.

---

