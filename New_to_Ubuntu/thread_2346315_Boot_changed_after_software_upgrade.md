---
title: "Boot changed after software upgrade"
date: 2016-12-13
forum: New to Ubuntu
---

### Post by andylowe on 2016-12-13
I recently installed Ubuntu 16.04.1 LTS on a second HDD in a Lenovo PC. The Lenovo offers an F-12 boot selection prior to booting. When wanting to boot to Ubuntu I selected the WDC HDD that I installed Ubuntu onto. At that point I was booted into Ubuntu quite quickly and everthing was fine for about 3 days. Then I got a soft ware update... Now when I F-12 during boot I select the WDC HDD, but I go to a page called "GNU GRUB version 2.02~beta2-36ubuntu3.2"

The window offers this:
*Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory  test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

If I choose *Ubuntu it boots into Ubuntu after about a two minute delay and everything seems to be normal after the long boot and several different black and wine colored blank screens.

Before the software update I had not installed a dual boot because I did not want to have problems with win7 that I had the last time I dual booted with Ubuntu (over a year ago).
 
Question: Did the software update install a Ubuntu dual booter, and if so, can I go back to using the the F-12 to boot to WDC HDD (contains NOTHING but the Ubuntu installation) selection only which had no Windows 7 mention in Ubuntu.

This is my second try at Ubuntu now Microsoft is forcing everyone to go to Windows 10 which I refuse to do. Any help will be greatly appreciated.

---

### Post by ajgreeny on 2016-12-13
Please do not refer to Microsoft in the manner you did; it is frowned on in the forum and is considered derogatory by many.
See #3 in General Policy at [https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

I wonder if there was an update to grub or a new kernel in your upgrades that may have caused the change.
Run command ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
```to see what was updated and ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```to see if a new kernel was installed.
Both commands will output a list of packages updated or installed by date so you can see what happened on the date when the change happened.

---

### Post by mastablasta on 2016-12-14
> **andylowe said:**
>  
Question: Did the software update install a Ubuntu dual booter, and if so, can I go back to using the the F-12 to boot to WDC HDD (contains NOTHING but the Ubuntu installation) selection only which had no Windows 7 mention in Ubuntu.

GRUB is not dual booter but boot manager. it is what loads before the OS (windows has one as well). it likely found windows and the reason you see it is maybe something changed in a setting. you can time it out which would make it automatically proceed to boot into Ubuntu unless you hold the "shift" key. 

[http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry](http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry)

in any case as i mentioned at the start - this is a boot manager. i believe (from memorry) the windows one is reached by holding F8 just before windows boot. then you can access various modes or add your own OS to boot (MS based). since it doens't affect either of the OS (remember it works before the OS is loaded) you can actually leave it and use it. if you boot into windows you would select windows entry. what this would do is simply "tell" the PC "continue loading windows".

windows 7 installed in MBR shouldn't have any issues to dual boot with Ubuntu. wind 8 and 10 present a couple of other chalenges to overcome and may need some workarrunds. but they can work as well.

---

