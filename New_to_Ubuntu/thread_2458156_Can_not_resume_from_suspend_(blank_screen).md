---
title: "Can not resume from suspend (blank screen)"
date: 2021-02-17
forum: New to Ubuntu
---

### Post by emilio-11 on 2021-02-17
I've been using ubuntu for a while and I've never  encountered a  problem. However,after suspending the laptop, when I try  to resume  screen goes for blank(Neither mouse nor keyboard action  works).


 I've tried several solutions posted here but none of them worked like   editing grub file for AMD/Nvidia drivers, doing hardware   troubleshooting(no problem in hardware).
 After carefully examining /var/log/kern.log I've noticed that this below message:


 ***BIOS may not properly restore RDRAND after suspend, hiding RDRAND via CPUID. Use rdrand=force to reenable***

 I assume it is because of upgrading kernel to the new version. But I don't know how to resolve this. Any ideas are welcome

 
System Details:

 

[LIST]
[*]OS: Ubuntu LTS 20.04, Kernel 5.8.0-43-generic
[*]CPU: AMD A6-6310 APU with AMD Radeon R4 Graphics
[*]GPU: Mullins [Radeon R4/R5 Graphics]
[*]RAM: 8GB
[/LIST]

---

### Post by #&amp;thj^% on 2021-02-17
A short quote:
> On resume, many BIOS implementations are not doing the proper steps for ensuring RdRand support and is evidently widespread enough that AMD felt it necessary to just disable the support by default. Unfortunately there is no way to properly query whether RdRand is behaving fine on AMD hardware and thus for these older systems is more sane to just disable by default. The issue itself has been known for 5+ years where RdRand may effectively just return -1 but is now being addressed by the Linux stable tree as a kernel workaround. 
Source; [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.3-Disabled-Older-AMD-Rd](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.3-Disabled-Older-AMD-Rd)

For systems known to be in a good state or **not** >>>seeing _suspend/resume_ activity, the **rdrand=force kernel parameter **will override this default change.

---

### Post by emilio-11 on 2021-02-17
Thanks for the detailed info. But how I can resolve this suspend issue now ? Should I force enable **RDRAND **? If yes could you please explain how to achieve that?

---

### Post by emilio-11 on 2021-02-17
[INDENT] 					Thanks for the detailed info. But how I can resolve this suspend issue now ? Should I force enable **RDRAND **? If yes could you please explain how to achieve that? 				[/INDENT]

---

### Post by #&amp;thj^% on 2021-02-17
> **emilio-11 said:**
> Should I force enable **RDRAND **? 

That's up to you?
> **emilio-11 said:**
> If yes could you please explain how to achieve that?
Open a console/terminal and run:
```
sudoedit /etc/default/grub
```
Look for the line "**GRUB_CMDLINE_LINUX_DEFAULT=**" and add this "**rdrand=force**"
Example:
```
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 acpi_osi=Linux apparmor=1 **_rdrand=force_** quiet"
```
save the file, and next run:
```
sudo update-grub
```
it will take a reboot for the change to take effect.
Good Luck.

---

### Post by emilio-11 on 2021-02-17
I've successfully updated grub file by **enabling rdrand**. After reboot, I've suspended laptop but still issue remains. System just could not wake up from suspend. I've checked all possible solutions out there internet but nothing worked so far... It is seriously frustrating I've been dealing with this for about 1 week. 

Anyways thanks for your help. I should look for other possible solutions even if Im kinda hopeless tho :)

---

### Post by #&amp;thj^% on 2021-02-17
> **emilio-11 said:**
> I've successfully updated grub file by **enabling rdrand**. After reboot, I've suspended laptop but still issue remains. System just could not wake up from suspend. I've checked all possible solutions out there internet but nothing worked so far... It is seriously frustrating I've been dealing with this for about 1 week. 

Anyways thanks for your help. I should look for other possible solutions even if Im kinda hopeless tho :)

I suspected that result, but good effort on your part. :)
Try on an older kernel as I was never a fan of "Kernel 5.8.0-43-generic" .

---

### Post by emilio-11 on 2021-02-17
Good idea, I did not try that one :) Which version you would recommend ? and if reverting back to old version does it affect update/upgrade of the system later on?

---

### Post by #&amp;thj^% on 2021-02-17
probably "5.4.0-58 ", and no it should not effect updates.
You may still have it installed, unless you D-loaded 20.04.2 then it comes as default the nasty 5.8.0-43-generic version. ;)

---

### Post by emilio-11 on 2021-02-17
Thanks man!

---

