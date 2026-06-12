---
title: "How to use internal hard drive while using ubuntu from pen drive"
date: 2017-07-14
forum: New to Ubuntu
---

### Post by utkarsh101 on 2017-07-14
[COLOR=#111111][FONT=Ubuntu]my windows stuck on BSOD and seem it got corrupted as well, all I wanted is to save my data before reflashing the windows, that's why I was running Ubuntu from a thumb drive, but still, i could not access my all 4 drives. Is there any way I can access them from Ubuntu.Also, I'm new to Ubuntu so any help would be highly appreciated.[enter link description here]("https://drive.google.com/open?id=0B7HzhjseT2HgMU9FdjJKTlVMelk")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]BSOD Error I gets.[enter link description here]("https://drive.google.com/open?id=0B7HzhjseT2HgQU5PVXdkZDkwUm8") the error I get in Ubuntu[/FONT][/COLOR]

---

### Post by yancek on 2017-07-14
The message in the image you posted indicates you left your windows hibernated and no Linux OS will mount a hibernated windows partition except as read only.  That should not be a problem in your case as you don't need to write to the windows partition but just copy from it.  Methods to do that are explained at the link below.

 [https://wiki.manjaro.org/index.php?title=How_to_mount_Windows_(NTFS)_filesystem_due_to_hibernation](https://wiki.manjaro.org/index.php?title=How_to_mount_Windows_(NTFS)_filesystem_due_to_hibernation)

---

### Post by col48 on 2017-07-17
If you want to copy data on the disk which was not being processed at the time Windows was hibernated, that's fine - but (obviously?) copy it to an external drive like your pen drive.  If you suspect corruption, even a partition which is ostensibly invisible to Windows is vulnerable.

If it is data being processed by Windows (ie edited) at hibernation time, you can only read the data as it was last time it was saved by you.

---

