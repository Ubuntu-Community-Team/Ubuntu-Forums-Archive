---
title: "Problems with Ubuntu 16.04 install"
date: 2016-09-15
forum: New to Ubuntu
---

### Post by joec522 on 2016-09-15
I just installed Ubuntu on my new ASUS F555U. It has an i5-6200 2.8 ghz processor with 8gb RAM and 1tb HD with Intel integrated graphics. Some of the problems I am having with the install are:

Slow response time 

WiFi doesn't work. Connects for a very short period of time - if at all

Computer won't shut down when I tell it to. Must force shutdown 

This is my second install. First install I did was with encryption enabled. Second install did not have encryption enabled. Both installs had these problems. The first install had boot up issues that didn't show up on the second install. 

Thank you.

---

### Post by oldfred on 2016-09-15
Perhaps you need a boot parameter?

If you only have Ubuntu installed you should not get grub menu. But with UEFI you press escape during UEFI/BIOS boot. If UEFI fast boot is on, you may not have time to press a key. 
If BIOS install you press and hold shift key from BIOS until menu appears.

You add other boot parameters like you add nomodeset for those systems with video issues.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    

 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by Bucky Ball on 2016-09-16
As above from oldfred. If your wifi is still not working after you fix the initial problems, post a new thread for it. It doesn't really belong here as your problems seem to be slow response and won't shutdown. These should be fixed before delving into the wireless (which goes in another forum area, ***Networking and Wireless***). 

You're in good hands so good luck. :)

---

### Post by ltrtiger2 on 2016-09-16
Perfect! Wish I'd seen this reply earlier!

---

### Post by joec522 on 2016-09-17
Thank you oldfred. Your information helped me solve most of the problems. I still have some wifi issues that I will address when I have more time. I will follow Bukcy's advice and move over to Networking and Wireless to address these issues.

I have recently decided to switch over most of my personal computing activities over to Linix and get away from Windows. I have a lot to learn and you guys have been a big help.

---

