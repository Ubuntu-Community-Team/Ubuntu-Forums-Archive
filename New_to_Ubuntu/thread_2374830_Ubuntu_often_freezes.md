---
title: "Ubuntu often freezes"
date: 2017-10-19
forum: New to Ubuntu
---

### Post by oguz-189013 on 2017-10-19
I been toying around dualbooting Ubuntu and Win10 on my low-spec notebook for a week, I tried Ubuntu 16.04, 17.04 and several Ubuntu flavors but they all freeze. And shutting down notebook physically, makes Ubuntu installation useless; it corrupts the partition on which Ubuntu is installed. As far as I guess, reason for it to freeze is %100 cpu usage but I don't know how to fix. Please help
Here are my notebook's specs:
CPU: AMD Dual Core A9-9410
Memory: 4GB
HDD: 1TB

---

### Post by ian-weisser on 2017-10-19
"Freeze" could mean a lot of things. Does it ever unfreeze if left alone for a half-hour or so? If not, then it's likely to actually be a 'crash'.
Is there anything you can do that will reliably cause a freeze?
Is there anything you do that reliably avoids a freeze?

Look up how to run a SMART test on your HDD.
Note the time of a freeze. After reboot, review the system log (/var/log/syslog) around that time for clues.

---

### Post by oguz-189013 on 2017-10-19
It won't unfreeze. Since mostly I can't boot into Ubuntu again (because even initramfs does not appear), I can't see logs. It "crashes" when I'm browsing on Firefox randomly, other day it crashed in Ubuntu Software, yesterday it has crashed when I'm changing sound volume and today it crashed after I have typed sudo apt update

Here are lines around crash from syslog:
Oct 20 00:02:12 oguz-X555BP systemd-timesyncd[622]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Oct 20 00:02:22 oguz-X555BP systemd-timesyncd[622]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Oct 20 00:02:32 oguz-X555BP systemd-timesyncd[622]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Oct 20 00:05:47 oguz-X555BP rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="743" x-info="http://www.rsyslog.com"] start
Oct 20 00:05:47 oguz-X555BP rsyslogd: rsyslogd's groupid changed to 108
Oct 20 00:05:47 oguz-X555BP rsyslogd: rsyslogd's userid changed to 104
Oct 20 00:05:47 oguz-X555BP systemd[1]: Started Create Static Device Nodes in /dev.

---

### Post by ian-weisser on 2017-10-19
1) Instead of poweroff, try the MagicSysRq key to avoid corruption: [https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
Write down the key combo, and leave it by your machine. Plenty of opportunity to learn it the first time you need it.
It might prevent corruption, it might not. Worth a try.

2) Linux developers have spent years finding ways for software crashes to leave a log entry. Since there isn't a relevant log entry, we widen the scope to include hardware. The three most common causes of hardware-related freeze-type crashes are dying HDDs, bad RAM, and incompatible video cards.
- How did that SMART test go?
- Look up how to use MEMTEST to check your RAM.
- What is the *exact* model of your graphics hardware?

---

### Post by oguz-189013 on 2017-10-19
sorry for late reply. reisub seems not working on my situation.
SMART test said that my hardware is "Good"
memtest took a lot of time but there were no errors
AMD Radeon R5 M420

---

### Post by ian-weisser on 2017-10-19
Most likely an incompatible video card.
See [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by oguz-189013 on 2017-10-20
Thanks a lot. But I did not understand what I should do. Is it impossible to run Ubuntu fluently on my graphics card ?

---

### Post by dino99 on 2017-10-20
you said "low-spec", that can explain why you get such problem. But is w10 running smootly ? how ubuntu has been installed ? on which kind of partition ? is there a swap partition ?
which are these specs ?
usually on such low-spec hardware, ext4 partition is set to install Lubuntu as its the lightest DE

---

### Post by oguz-189013 on 2017-10-20
yes, there is no problem with w10. I have installed Ubuntu from USB (if this is what you are asking). There are two partitions on my HDD; on the first part(ntfs) w10 is installed. Ubuntu is installed on the second(ext4). I have tried Lubuntu, Kubuntu and Xubuntu but they were worse, I have faced freezing even while installing Ubuntu flavors

---

### Post by oguz-189013 on 2017-10-22
I installed AMDGPU-PRO. Now Ubuntu began to crash randomly. Did I do something wrong ?

---

### Post by RobGoss on 2017-10-22
Hello **oguz-189013**, How does the live installer work does it also freeze? as mentioned it can be a lot of things related to the freezes in some cases older hardware is a key player

---

### Post by oguz-189013 on 2017-10-22
it works as expected but kubuntu, xubuntu etc. freezes

---

