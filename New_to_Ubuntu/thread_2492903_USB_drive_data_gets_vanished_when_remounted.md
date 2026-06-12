---
title: "USB drive data gets vanished when remounted"
date: 2023-11-27
forum: New to Ubuntu
---

### Post by muhammad-ali-mughal on 2023-11-27
I'm facing a problem with my Ubuntu OS. When I mount a USB I successfully input or output my data into USB drive. But when I remount it into my system or some other system the USB shows empty. I've tried it many times with other USB drives but concluded the same result. This happens the same while booting a USB.

I've also checked for some kind of malware in the system but no malware or virus detected.

Is there anyone to help me out in this case because I've lost a lots of data because of this problem.

---

### Post by oldfred on 2023-11-27
What format is partition on USB drive.
Post this with USB drive mounted.
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

If NTFS, are you attaching to Windows system that sets hibernation or fast startup flag? That will restore system to when flag was set, erasing any changes after flag set.

---

### Post by yancek on 2023-11-27
What is or originally was on the drive?  Was it a live Linux, data from Linux or windows or both as well as answering the questions in post 2.

---

