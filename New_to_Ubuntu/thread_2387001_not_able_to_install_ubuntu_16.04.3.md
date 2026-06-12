---
title: "not able to install ubuntu 16.04.3"
date: 2018-03-13
forum: New to Ubuntu
---

### Post by anuragkumar048 on 2018-03-13
I have a Dell XPS laptop with intel i7 processor, 7th gen. I am not able to install ubuntu in this laptop. There is windows already installed in this laptop.

The screen gets stuck at first page when I try installing ubuntu. The screen has UBUNTU written on it with dots below. I tried searching online for support but could not have any successful solution. Can anyone help.

---

### Post by kc1di on 2018-03-13
this Dell youtube video may be of help to you:
[https://www.youtube.com/watch?v=RW9UWDOJjL4]("https://www.youtube.com/watch?v=RW9UWDOJjL4")

---

### Post by mörgæs on 2018-03-14
With hardware this new you should be using new software. At least 17.10.1, maybe 18.04 (beta).

---

### Post by mastablasta on 2018-03-14
7th gen is arround since 2016, and the HWE in 16.04 keeps kernel up to date (sort of).

still latest version of kernel might help (in case the CPU is form 2017).


they are at gen8 now.

---

### Post by thebman2 on 2018-03-16
I have an xps 9360 i7 8th gen and 16.04.4 installs and runs very well on it. Having tried all of the Ubuntu's, 16.04.4 has given me the least amount of issues with my configuration. I cant help with dual boot setup if that is your plans other than I know you need to go into disk managment in Windows and create yourself some space on the drive prior to installation. As a stand alone OS, I have the following BIOS settings

advance boot options > enable UEFI network stack
Boot Sequence > UEFI
system configuration > sata > set to AHCI
secure boot > secure boot enable > disabled

---

### Post by deanr2 on 2018-03-20
I've had various nightmares trying to boot or install from USB. 

I switched to a burned DVD image and have had no problems on multiple installs. I recommend this over USB on Windows 10 - which in my experience has made it that much harder to install an alternative OS.

---

### Post by monkeybrain20122 on 2018-03-20
> **deanr2 said:**
> I've had various nightmares trying to boot or install from USB. 

I switched to a burned DVD image and have had no problems on multiple installs. I recommend this over USB on Windows 10 - which in my experience has made it that much harder to install an alternative OS.

You mean in general or dualboot? I have always used usb to boot since the big bang except in one case where the machine was so old that it didn't boot from usb. I never have any problem. Who still burns DVDs in 2018 except that one guy with many threads on the same problem relating to burning DVD?? :P Most laptops don't even have a dvd drive.

Edited: If you are talking about dualboot then I don't know, maybe Windows 10 is only happy if you install Linux with floppies, who knows. I think dualboot with Win is a  bad idea, and it is doubly bad with Win 10, it is a fragile configuration hard to set up and maintain.

---

### Post by monkeybrain20122 on 2018-03-20
> **anuragkumar048 said:**
> I have a Dell XPS laptop with intel i7 processor, 7th gen. I am not able to install ubuntu in this laptop. There is windows already installed in this laptop.

The screen gets stuck at first page when I try installing ubuntu. The screen has UBUNTU written on it with dots below. I tried searching online for support but could not have any successful solution. Can anyone help.

Maybe you need to set some kernel parameters like nomodeset or such.

---

### Post by monkeybrain20122 on 2018-03-20
> **mörgæs said:**
> With hardware this new you should be using new software. At least 17.10.1, maybe 18.04 (beta).

I doubt it  We have several computers at work running Ubuntu 16.04.4, all intel i7 7th generation and we installed Ubuntu ourselves. All work. System 76 is selling laptops with intel 8th generation that come with Ubuntu 16.04.4 (granted that they know how to tweak it that may elude the ordinary user) 

18.04 is beta and many bugs remain to be ironed out, 17.10 is unstable and full of little problems in my test. I think 16.04.4 is the way to go.

---

### Post by deanr2 on 2018-03-21
Yeah, I mean dual boot. You'll find a few other people who 'can't install Ubuntu' reporting problems with screen stuck on boot, not detecting boot loader, not detecting USB, booting to windows and ignoring Ubuntu etc. 

Credit where credit is due, Microsoft have done an excellent job protecting windows 10. Try it. Just for fun ](*,)

---

