---
title: "Dell Vostro laptop, Display Settings Resolution is 640x480, can't change"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by parker-hugh on 2014-05-19
Lubuntu on Dell Vostro laptop, Display Settings Resolution is 640x480 and can't change

below is the output of terminal window....

```
hugh@Lubuntu-14:~$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0d.0 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
hugh@Lubuntu-14:~$ ^C
hugh@Lubuntu-14:~$ 
```

```
hugh@Lubuntu-14:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        73.0* 
```

I am a novice on linux so would be grateful for any tips on how to fix this or where I can go to find a solution
thanks

---

### Post by plucky on 2014-05-19
> 00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter

Is Lubuntu installed in Virtualbox?

What is host Operating System?

Have you run Guest Additions in Virtualbox?

---

### Post by parker-hugh on 2014-05-19
hi thanks for reply, I have installed Lubuntu in virtualbox to see if it will be ok to use on my dell vostro laptop, then I was going to partition the hard drive and install it proper.

the host os is windows 7

your last question "Have you run Guest Additions in Virtualbox?" I am not sure what this means as I am very new to linux. I can use the terminal window if I know the syntax to use.

regards,

Hugh

---

### Post by plucky on 2014-05-19
Not sure if Virtualbox interface is the same in windows,but if it is ,after you have Loaded Lubuntu and logged in,click on the devices tag at the top and click on "Insert Guest Additions CD Image" and it should load a CD.If you click on the CD it should then let you install "Guest Additions".

> I have installed Lubuntu in virtualbox to see if it will be ok to use on my dell vostro laptop, then I was going to partition the hard drive and install it proper

Virtualbox doesn't use the same drivers as a full install would,you might be better testing using a Live DVD/USB if you want to test compatibility.

Good Luck

---

### Post by parker-hugh on 2014-05-20
thanks plucky for reply and advice. I have burned the ISO and ran the live DVD, and it did pick up my resolution OK. So thanks for the tip, it was spot on.  will close this thread if I can figure out how to do it.

regards, Hugh

---

