---
title: "Ubuntu 12.04 LTS black screen problem"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by kartoos2 on 2013-10-23
I recently bought a lenovo y510p with pre-installed windows 8. I did not like win8 and decided to switch to ubuntu for good. However, I have a problem. After installing ubuntu 12.04LTS from a liveUSB and rebooting, I am welcomed by a black blank screen with a blinking cursor in the top left corner of the screen. Below are the details of what I did before the black screen:
1. Disabled secure boot and enabled boot into legacy mode from the BIOS.
2. Using LivUSB I chose "Erase disk and install ubuntu". The installation continued and asked for a reboot. On restart I got the black blank screen.
3. Went into LiveUSB to run [FONT=courier new]boot-repair[/FONT]. It failed.
4. Tried to update GRUB but failed in that as well. 
After searching online I figured the problem is due to the nVidia graphics card so I get into the kernel mode after the BIOS flash using the shift key. But I do not get the options, after restart I end up at the black screen. So I changed the options to not use the nVida card using "[FONT=courier new]nomodeset[/FONT]" from the liveUSb and then tried updating the GRUB. But GRUB will not update.

here is the boot-repair URL info [http://paste.ubuntu.com/6291325/](http://paste.ubuntu.com/6291325/)


I have been stuck with this issue for a couple of days now and it is getting frustating. Kindly help me resolve this problem.

---

### Post by Impavidus on 2013-10-24
According to your summary, your computer has a 24GB SSD (sda) and a 1TB HDD (sdb). sdc is your live usb. Ubuntu is installed on sdb, but there is no boot loader installed. The SSD is not used, it has no partition table. The recommended repair would install grub to sdb, which should fix the problem, provided the computer tries booting from the second drive. Did you try? Did you check the boot order?

Furthermore, as you have an SSD, you would get better performance if you put the Ubuntu root partition on the SSD and put your /home partition on the HDD. Easiest way to get it like this is by reinstalling, using manual partitioning. As you haven't put anything yet on the computer this can be done quickly.

---

### Post by Askel on 2013-10-24
hi

had the same problem with the blackscreen. in my case there's only one of the 4 graphicsdrivers for nvidia that works for me. otherwise I get the same problem. In the bios-settings mark (or unmark) optimus. this will disable nividia and it will start using the inteldrivers. it should be enough to be able to use another nvidiadriver.

---

### Post by kartoos2 on 2013-10-24
Thanks for the reply. 

Yes, I did try that and the boot order was to boot from the HDD first, sdb. 

After your recommendation to install the root in the SSD I did that too but same old problem :/

---

### Post by kartoos2 on 2013-10-27
Well the problem is finally solved. I ended up reinstalling windows 7 and then Ubuntu 12,04. It still didn't boot Ubuntu, only windows, but the boot-repair fixed that issue. I later installed the nVidia drivers without any bugs.
Thanks

---

