---
title: "Perplexed About UEFI and Dual Boot Encryption"
date: 2019-04-10
forum: New to Ubuntu
---

### Post by Franz_Ziereis on 2019-04-10
I bought a new HP with one 512Gb SSD (Win 10 files there) and 1Tb SSD. After researching about dual booting and dual booting with UEFI, I'm confused:confused:.  I just watched a guy on YT install VeraCrypt on his Win 10 going through the usual procedures without a hitch or mucking with the UEFI.  When I dual booted Windows (in the good old days) with TC, as I seem to recall I would create my partitions, install Ubuntu FDE (2 partitions) since I used a paging file and home was on /root. Just /boot and /root partitions.  I would then install XP using TrueCrypt and when it asked if there were any other operating systems, selected, "no".  When I started the comp, I would press one of the keys (probably escape) and got my Ubuntu login. If I let it run, w/o, pressing anything, it would default to the TC login screen.

Is this still a viable way of doing  this today or what is the next best plan?  In my searching it seems there was more than one My primary desire is  to keep Ubuntu encrypted even if that means a plain text Windows.

P.s. I have an external USB with Ubuntu fully installed on it, it's 64 bits.  Do I dare try and plug it in and mount it and see if it works?

---

### Post by yancek on 2019-04-10
If your windows 10 was preinstalled, it is likely a UEFI install.  Dual booting Ubuntu with windows on a UEFI machine is explained at the Ubuntu site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I'd be reluctant to use instructions from a You Tube video since anyone can put anything on one of thee videos, particularly since Ubuntu usually has detailed instructions available. 

> P.s. I have an external USB with Ubuntu fully installed on it, it's 64 bits.  Do I dare try and plug it in and mount it and see if it works?

Did you do this install of Ubuntu on this computer?  Did you do a UEFI install?  When you installed to this disk, did you use the LVM option to install w/encryption?  Simply trying to boot it from a BIOS boot option should not be a problem.  It either boots or it doesn't.

---

### Post by oldfred on 2019-04-10
If you have UEFI Secure Boot on, you may not be allowed to boot from an USB port. That is not secure. 
Then there should be a setting somewhere where you can allow USB boot. I think it always should be allowed as how do you repair a system if you cannot boot it from repair media?

---

### Post by Franz_Ziereis on 2019-04-10
Thanks to all the replies, I'll look into each of them.

---

### Post by Franz_Ziereis on 2019-04-10
That was the thing I liked about the old days.  I don't remember how many times I salvaged peoples' HDD files by mounting with Ubuntu and even removing a very persistent malware from my XP dual boot by running a Linux antivirus on the XP partition from the Ubuntu partition on the unmounted XP drive.

---

### Post by Franz_Ziereis on 2019-04-10
> **yancek said:**
> If your windows 10 was preinstalled, it is likely a UEFI install.  Dual booting Ubuntu with windows on a UEFI machine is explained at the Ubuntu site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I'd be reluctant to use instructions from a You Tube video since anyone can put anything on one of thee videos, particularly since Ubuntu usually has detailed instructions available. 



Did you do this install of Ubuntu on this computer?  Did you do a UEFI install?  When you installed to this disk, did you use the LVM option to install w/encryption?  Simply trying to boot it from a BIOS boot option should not be a problem.  It either boots or it doesn't.

I created the external from my current laptop, so no UEFI. I suppose I could wipe it and reinstall from my new computer.

---

