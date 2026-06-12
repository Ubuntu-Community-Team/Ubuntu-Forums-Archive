---
title: "Total Newbie: &quot;Error: Unknown filesystem: grub rescue&quot;"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by ultrapiggy on 2013-04-26
First things first, this is on an Asus x401a laptop, and therefore does NOT have a disc drive. I'm currently downloading Ubuntu 13.04 on a separate computer to create into a bootable USB to perhaps resolve this one way or another.

All right, so I had Ubuntu installed on a separate partition than Windows 7, and I got everything up and running perfectly fine. It was set to go to the boot screen where I could choose Windows or Ubuntu, and if it wasn't chosen within a few seconds, it would default to Windows.

About 3 weeks to a month ago, I deleted my Ubuntu partition from the computer, and expanded my Windows partition to the original size. The laptop worked fine, and I could restart. shut down and boot up without any issue - it would always start up like it did before Ubuntu was ever installed. However, within the last week, I've been getting the "Unknown filesystem: grub rescue" error after 2 weeks+ of flawless activity. I don't know how the issue could have randomly popped up like that.

I know enough about computers to fix Windows issues and I can usually find the solution to other issues, but this time it seems like I'm stumped. I look on the forums and there are walls of system-mumbo-jumbo being posted back and forth, and I just need a few steps, in layman's terms, how to get this all back to normal. I'm a busy college student and I really need to get back into Windows as soon as possible, as this is my last few weeks and I need access to, well, everything.

Hopefully there's a simple solution that I can come to using a bootable USB with 13.04 on it. In fact, that seems to be the only way, since the usual F9 for recovery options (for Asus PCs) isn't working...

Thanks for reading, and hopefully I can get this issue resolved by the end of the day.

---

### Post by ultrapiggy on 2013-04-27
I know this issue is fixable, and I've seen plenty of "solved" threads, but I don't understand what any of them are talking about, as all the wording just gets me lost.

Is there really not one person who can explain how to fix this in simple terms? I was told I'd get a fast response here and so far, it seems like my issue has only been ignored. :(

---

### Post by fantab on 2013-04-27
When installing Ubuntu you installed GRUB- Bootloader to the HDD? or Did you use EasyBCD to boot Ubuntu?

Grub will write itself to MBR and in the process Winodows Boot loader gets corrupted/overwritten. You may have to _['Fix the MBR' with Windows Recovery/Repair Disk]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")_ or with the Windows installation Disk. Or try to recover MBR with Asus recovery partition.

---

### Post by ultrapiggy on 2013-04-27
GRUB Bootloader was installed on the HDD.

Would there be a way to so it through Ubuntu? I have gotten 13.04 installed and it works fine. I just still can't get back into Windows.

Using the recovery partition will only work if I can get into Windows and run the Asus recovery AI software. And since there is no disc drive, an installation disc did not come with the laptop.

---

### Post by fantab on 2013-04-27
So you have installed 13.04 and its working but you are unable to boot Windows7. I don't think that you have to boot into Windows to be able to perform 'recovery', are you sure that you can't? If its possible to run recovery then you must remove ubuntu and its partition.

You can try:

Open 'Files' (Nautilus) file manager in Ubuntu. In the left side pane you should see your Windows partition under 'Devices'. Click on it to mount it. Then from TERMINAL run the following:

```
sudo update-grub
```

and see if grub menu finds Windows.

If the above solution does not work then from Ubuntu post the output of [BOOT INFO SCRIPT]("http://bootinfoscript.sourceforge.net/"). Also have a look at [BOOT REPAIR]("https://help.ubuntu.com/community/Boot-Repair"). 

Can you tell us if you have Windows in UEFI boot?

---

### Post by grahammechanical on 2013-04-27
> [COLOR=#000000]About 3 weeks to a month ago, I deleted my Ubuntu partition from the computer, and expanded my Windows partition to the original size. The laptop worked fine, and I could restart. shut down and boot up without any issue - it would always start up like it did before Ubuntu was ever installed. However, within the last week, I've been getting the "Unknown filesystem: grub rescue" error after 2 weeks+ of flawless activity. I don't know how the issue could have randomly popped up like that.[/COLOR]

It didn't randomly pop up. You removed Ubuntu but did you reinstall the Windows boot manager? You are still using Grub to boot without a Ubuntu on it to run update-grub. Was there a Windows update?

---

### Post by Impavidus on 2013-04-27
You get a grub rescue prompt, so grub is still installed. The ubuntu partition has been removed and the disk space allocated to the windows partition. Grub needs data from the Ubuntu partition. Hypothesis: grub was able to read its data on the former Ubuntu partition for two weeks, until the partition was overwritten by windows. I've no idea how else it could have worked for two weeks. But it seems you need a bootable medium to install a windows boot loader.

---

### Post by ultrapiggy on 2013-04-27
I seemed to figure it out. I ran Boot Repair and it fixed everything. :)

---

