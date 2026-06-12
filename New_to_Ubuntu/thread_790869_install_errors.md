---
title: "install errors"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by nefrin on 2008-05-11
Running into an error I have never seen before. First, the computer specs:

# eMachine T6412
# AMD Athlon 64 Processor 3400+ 2.19GHz
# 1GB of RAM
# ATI Radeon Xpress 200 Series Graphics Card
# Sony LCD Monitor
# Running XP SP2

When trying to install from the live CD (and yes, it's the AMD 64 live CD) I get the following error after the splash hangs up, and I have to hit ctrl+alt+F1:

MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait...
Buffer I/O error on device fd0, logical block 0

The Buffer I/O error just repeats every few seconds until I reboot

---

### Post by SuperSon!c on 2008-05-11
found this old post regarding such a scenario

> **Erian said:**
> I've had this problem as well on my A64x2 4600. It is possible to fix it during the install by pressing f6 and adding the "noapic" option before the final -- in the text line with boot options.

So your line should something look like:

```
xxxxxxxx xxxxx xxx xx xxx xxxx noapic--
```

see if that helps.

---

### Post by nefrin on 2008-05-14
when booting from the live CD, when it got to the screen asking what to do (install, run without changes, test memory, etc) I hit F6 twice.

That presented a popup menu that gave me the option to select "noapic". From there I escaped out of the menu once i had selected it, and choose the install Ubuntu option.

It loaded for awhile, then I still receieved the Buffer I/O error on device fd0, logical block 0

this sounds like a hard drive error to me.

Update:

After displaying the above error twice, the system ran through it's setup and brought me to the install screen for Ubuntu. It's currently installing. Have to run out to get to an appointment on time, but I'll leave an update on the install when I return.

OK, got it installed. I went into BIOS and disabled the APIC option in the BIOS. Now the issue I am having is I get to the login screen, enter my user name and password, and then it looks like it's going to load, except it kicks me right back to the login screen every time. Is it still the APIC issue that I am having problems with?

---

### Post by nefrin on 2008-05-14
ok, got all booted up. I had to change my initial session to the failsafe GNOME, as I was trying to log in and it kept kicking me back to the login screen repeatedly.

Once i logged in failsafe, I was able to download the drivers needed for my graphics card (built in ATI for emachines), and that solved the issue. I am now able to log in under normal conditions. Seems to be working smoothly.

---

