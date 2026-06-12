---
title: "Windows 10? Dual Boot"
date: 2016-11-04
forum: New to Ubuntu
---

### Post by arukas2 on 2016-11-04
So the liveCd worked fine.  However, after I installed it, my computer boots up into windows 10s.  I don't even get the choice select with OS to boot up.  I am use to it "Just working".  Any suggestions?

-A

---

### Post by Impavidus on 2016-11-05
Some more information on your system may be helpful. Brand and model of computer, hardware details, bios or uefi. Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Don't run the recommended repair (yet), but create a BootInfo summary and share the url with us. That will give a lot of details to help us find the cause of the problem.

---

### Post by RobGoss on 2016-11-05
Hello and welcome, Is this machine is **UEFI **most all the new machine these days are UEFI which makes installing Ubuntu or any other Linux distribution that more difficult

If your machine is in fact **UEFI** when installing Ubuntu you'll have to install Ubuntu in the same way **UEFI,** this might shed some light on how to accomplish dual booting in UEFI mode
[B]
UEFI MODE:[/B] [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[B]
UEFI / BIOS:[/B] [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by arukas2 on 2016-11-05
I figured it out, I had to go into the mother board settings and change how the HDD booted.  I have never done that before, I only had to select which drive to boot from first.

---

### Post by RobGoss on 2016-11-05
Were you able to get your machine to dual boot correctly?

---

