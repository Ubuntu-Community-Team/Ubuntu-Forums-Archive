---
title: "No init found try passing init = bootlarg"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by humdrumm on 2012-07-05
Hi everyone, I have been reading through the forum all day for this problem and somehow I have still not been able to fix it despite all the solutions I've tried.

I have tried making live cds of easypeasy 1.6 and Gpart, but it would not load. It would only give me this message:

(initramfs) usb storage - device scan complete
direct access - generic usb flash 8.07 PQ: 0 ANSI: 2
Attached scsi generic sg1 type 0
[a lot of other things in between]
assuming drive cache: write through
sdb: sdb1
assuming drive cache: write through
attached SCSI removable disk
device scan complete

that's all and it won't boot. it boots on other computers too.

Please, I am getting so frustrated and I don't know what to do, I have been using this OS perfectly for the last 3 years so everything is saved on it. 

Thanks in advance, every little thing appreciated!

---

### Post by ikt on 2012-07-06
So when you put in a livecd of ubuntu 12.04 it has that error in the title?

---

### Post by humdrumm on 2012-07-06
What's there is the no init error message and that message. If i cant recover my laptop, can i at least recover the data in it? Thanks so much.

---

### Post by Cheesehead on 2012-07-06
Your laptop should be easily recoverable after we have enough information to help you.

DON'T make things worse by trying to reinstall, or blindly changing things.

Did this happen after an update or some change? Usually, this error message means that GRUB is trying to boot from the wrong partition.

Do you happen to know the correct partion? If not, we can tell you haow to figure it out.

---

### Post by humdrumm on 2012-07-06
Okay so good news is I recovered it now, I made it boot and everything using the hidden menu (when you hold down the shift button) in recovery mode I believe. It said it had a problem in /dev/sda1 and after everything ended I can boot normally again, data there and everything

The problem now is though, my laptop can't detect ANY wireless connection whatsoever. What could have happened?

---

### Post by humdrumm on 2012-07-06
Sorry, I was dumb, wifi light just wasn't turned on. Thanks for all your help anyway! :D

---

