---
title: "Dual boot fail"
date: 2015-02-17
forum: New to Ubuntu
---

### Post by banduka123 on 2015-02-17
Hello every one

I'm using Dell Inspiron 5537 which has uefi boot system
once i installed ubuntu 14.04 to my lap beside with on build windows 8.1 with it
it is hard to log on to ubuntu
every time i have to disable the uefi boot system from boot setting.after that i unable to log on to window therefor i have to enable uefi boot system.
please some one can help me
I'm very new to ubuntu
But my desktop pc I use ubuntu 12.02 with windows 7 there is no any issue.

Thanks.

---

### Post by oldfred on 2015-02-17
Did you then install Ubuntu in BIOS/CSM boot mode?

Best to see details. Boot-Repair can convert a BIOS install to UEFI if on gpt partitioned drive and you already have an efi partition, which you have if Windows is UEFI.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not reinstall Ubuntu without reviewing the link below in my signature. You should not have to reinstall anyway.

---

### Post by sandyd on 2015-02-17
> **banduka123 said:**
> Hello every one

I'm using Dell Inspiron 5537 which has uefi boot system
once i installed ubuntu 14.04 to my lap beside with on build windows 8.1 with it
it is hard to log on to ubuntu
every time i have to disable the uefi boot system from boot setting.after that i unable to log on to window therefor i have to enable uefi boot system.
please some one can help me
I'm very new to ubuntu
But my desktop pc I use ubuntu 12.02 with windows 7 there is no any issue.

Thanks.

Hi, can you log into Ubuntu, and run the following in a terminal?
```

wget http://softlayer-dal.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvf bootinfoscript-061.tar.gz
sudo ./bootinfoscript bootinfooutput.txt
```

There should be a file named bootinfooutput.txt created after running, please attach to post.

---

### Post by banduka123 on 2015-02-18
> **sandyd said:**
> Hi, can you log into Ubuntu, and run the following in a terminal?
```

wget http://softlayer-dal.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvf bootinfoscript-061.tar.gz
sudo ./bootinfoscript bootinfooutput.txt
```

There should be a file named bootinfooutput.txt created after running, please attach to post.


I have tried
but code doesn't work
if code work correctly what will happen?
and also when i want to log ubuntu i have to change the uefi boot setting
after that i can log to ubuntu but when i restart my lap again i have to change the dettings
it not saved.when i log to windows immediately after that my lap getting very slow
but it automatically fix when after restart and log to the windows.

please help(buy the way thanks for the supporting)

---

### Post by banduka123 on 2015-02-18
> **oldfred said:**
> Did you then install Ubuntu in BIOS/CSM boot mode?

Best to see details. Boot-Repair can convert a BIOS install to UEFI if on gpt partitioned drive and you already have an efi partition, which you have if Windows is UEFI.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not reinstall Ubuntu without reviewing the link below in my signature. You should not have to reinstall anyway.

I'm not reinstall ubuntu i install only once and it will appear in os selecting step(widows or ubuntu)
i only manage to log into windows without any bios changing
but if i want to log into ubuntu every time i need to change bios settings
 
is there any chance to log into ubuntu without changing bios setting i mean uefi setting
if uefi setting help to protect and recovery my lap?

thanks for the support.

---

### Post by oldfred on 2015-02-18
The way you are booting sounds like a BIOS install, since starting in UEFI mode you have to totally reboot to start in BIOS mode.
But we need the Summary report from Boot-Repair to know for sure.

---

