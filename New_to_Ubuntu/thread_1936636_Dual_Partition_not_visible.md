---
title: "Dual Partition not visible"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by Digitalscribbler on 2012-03-06
Hi-
I recently installed Ubuntu 11.10 and when I installed I selected the option for it be installed along side Windows (dual partition). I already have Windows 7 installed on my machine and the Ubuntu installation was successful. However, now when I boot my computer, it only takes me to the Ubuntu login rather than displaying Windows and Ubuntu side-by-side. When I click the System Info in Ubuntu, it displays the following info:
-Memory: 3.7 GiB
-Processor: AMD C-60 AUP with Radeon(tm) HD Graphics x 2
-OS type: 32-bit
-Disk: 218.3 GB
What did i do wrong and how can I correct this so that both login options/partitions appear? Thanks.

--Hardware specs:
Aspire One 722
CPU: AMD Dual-Core Processor C60
Memory: 4GB DDR3 Memory
Storage: 500 GB HDD

---

### Post by kazztan0325 on 2012-03-06
Hi Digitalscribbler,

Try this with Terminal, and then reboot your PC.

```
sudo update-grub
```

---

### Post by Digitalscribbler on 2012-03-06
> **kazztan0325 said:**
> Hi Digitalscribbler,

Try this with Terminal, and then reboot your PC.

```
sudo update-grub
```

Thanks a lot! That did it. 

I was a little confused at first because when I first rebooted it displayed the Windows 7 loader at the bottom of a list of options. But I realized all I needed to do was cursor to the bottom of the list and then hit Enter and then it took me to Windows. (see screenshot 1 - "ubuntu_load1") 

I was hoping for it show the login options so it was only those two (see Screenshot 2: "ubuntu_load2" -- apologies for the poor photo quality).

Thanks again for your help!

---

### Post by bogan on 2012-03-06
Hi!, **digitalscribbler,**

If you install Grub Customizer, you can edit the grub menu to show as little as you please, in any order, set the default, fonts, edit text and background, and other things.

[http://www.omgubuntu.co.uk/2011/05/grub-customizer]("http://www.omgubuntu.co.uk/2011/05/grub-customizer/")

Chao!, **bogan.**

---

### Post by Digitalscribbler on 2012-03-06
> **bogan said:**
> Hi!, **digitalscribbler,**

If you install Grub Customizer, you can edit the grub menu to show as little as you please, in any order, set the default, fonts, edit text and background, and other things.

[http://www.omgubuntu.co.uk/2011/05/grub-customizer]("http://www.omgubuntu.co.uk/2011/05/grub-customizer/")

Chao!, **bogan.**
thanks for this. I downloaded and installed it but the boot menu hasn't changed. I'm guessing that whatever is check-marked is displayed at the boot/login, but I'm not sure (i've attached a screenshot). Ideally, I'd like it to just display the two operating systems: Ubuntu and Windows. So would I just select/check (1) "Ubuntu, with Linux 3.0.0-16-generic-pae" and "Windows 7 (loader) (on/dev/sda2)"? Thanks

---

### Post by kazztan0325 on 2012-03-06
Hi Digitalscribbler,

Did you **Save** (that is to say, click the Save button at the left on toolbar) your **change** (that is to say, **tick off** against the items which you would not like to be shown)?

---

### Post by critin on 2012-03-06
>  I'd like it to just display the two operating systems: Ubuntu and Windows. 

You may wish you'd kept the two recovery links available someday.  Stuff happens.  lol

---

### Post by ixtok on 2012-03-07
> **critin said:**
> you may wish you'd kept the two recovery links available someday.  Stuff happens.  Lol

+1

---

### Post by raja.genupula on 2012-03-07
Yeah I agree with these Guys , after some upgrades some times your graphic drivers may be gone or corrupted . so you should reinstall them . for that operations you need failsafeX mode and possibled by recovery mode .

if you forgot your password then you should reset it . and the easiest of resetting a user password is can be possible from recovery mode .

---

### Post by bogan on 2012-03-07
Hi!, **DigitalScribbler**,

I also agree you would be well advised to keep the recovery mode entries, but in Grub Customizer you can change the order so the two you most want are default and the other close by.

 Select the one you want to move and use the up/down arrows in the toolbar. Dont forget to press 'Save', when complete.

There is a full 'HowTo' Tutorial here: [http://ubuntuforums.org/showthread.php?t=1664134&highlight=HowTo%3A+grub+Customiser&page=24](http://ubuntuforums.org/showthread.php?t=1664134&highlight=HowTo%3A+grub+Customiser&page=24) 

See Post #1

Chao!,** bogan.**

---

### Post by Digitalscribbler on 2012-03-07
Thanks everyone!

---

