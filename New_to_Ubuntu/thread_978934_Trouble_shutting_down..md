---
title: "Trouble shutting down."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by I am &gt;= Wes on 2008-11-11
I've been trying to shut down my machine and Ubuntu doesn't seem to be cooperating.  I tell it to shut down and the computer goes to a black screen with a flashing cursor in the upper left hand corner and just stays that way.  I can still try to get to the terminal with ALT + F1 but it just takes me to login in the terminal and I can't type anything.  I have gone so far as to turn the power strip off and then back on and the computer just starts right back up.
Comments and suggestions?

--Wes

---

### Post by CLomax on 2008-11-11
Not a fix but more of a protip:

Don't try to shut down the normal way. Press CTRL+ALT+F1 to get to the terminal, log in with your normal credentials then...

```
sudo shutdown now
```

Just until you can solve this problem before wrecking your filesystem. :)

---

### Post by Coreigh on 2008-11-11
If the power is OFF at the power-strip and you turn it on, did you say that the computer starts itself without you hitting the button on the computer?

In my experience that is a hardware malfunction of some kind. I have seen it be a simple compatibility problem with hardware all the way to indicating a failing power supply or mother-board. At the very least it is annoying, as you have discovered.

---

### Post by I am &gt;= Wes on 2008-11-11
Terminal commands appear to yield the same result :(

I am afraid it may be hardware related, and while I keep it in mind, I would like to rule out all other possibilities first.

---

### Post by CLomax on 2008-11-11
I'd put my money on it being a hardware problem...

and I don't have much :p

---

### Post by handydan918 on 2008-11-11
Perhaps a little more detail on the hardware? General specs, age, etc? Has this function EVER worked correctly on this machine, with Ubu installed?

---

### Post by CLomax on 2008-11-11
Let's see if this command gives us anything...

In the terminal type:

```
lspci
```

and paste the result here.

---

### Post by I am &gt;= Wes on 2008-11-11
Ubuntu used to work completely fine.  I can't think of anything that I may have done recently to cause it to do this.
However
```
 lspci 
```
returned
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
02:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

```

The computer as far as I know isn't horribly old but it's not mine so it's hard to tell.  My friend is letting me borrow it because my mom has some insecurities about me installing Ubuntu on her/our computer.

---

### Post by CLomax on 2008-11-11
Looks alright to me, nothing that has been confirmed incompatible as far as I'm aware.

---

### Post by ciscosurfer on 2008-11-11
Bug reports have been submitted by many (check Launchpad), but everyone's case seems different.  No amount of prodding has successfully fixed this problem for me.  Oh well.  I'm running Intrepid and this has been an issue since the alpha releases.  No workaround is sufficient in my case and my poor computer must go through a hard shutdown when I want to power off.  It's been an intermitent pain for me since Breezy--seems like every other release cycle I get hit by the 'I refuse to fully poweroff' bug.  It's a bummer really.

---

### Post by handydan918 on 2008-11-11
I'd be interested to know what happens if you kill the splashy so you can see the shutdown output as it scrolls by. Maybe the kernel is shutting down, but isn't successfully killing the hardware? acpi issue?

---

### Post by I am &gt;= Wes on 2008-11-11
I'll probably just deal with it for now and wait for the next update.

---

### Post by Blvd on 2008-11-12
I'm having the same problem on two different computers, it takes 5 minute to shut down on both. All previous  Ubuntu (6.04 and Up) shut down fine on my computers...

This one is a Dell Intel P4 2.40GHz 1GB RAM

---

### Post by I am &gt;= Wes on 2008-11-12
Okay, now we're in business. It's working fine now that I'm only using one router.

---

### Post by Blvd on 2008-11-12
So I'm testing this in two different computers with the same problem, both take 5 minutes to shut down.
I didn't have this problem before with previous Ubuntu (6.04 and up), only now with Intrepid.
I notice that this only happens if I turn off my computer with the DSL on, but if I turn off the DSL first, than my computer will shut down in: 
9 sec (home PC, running DSL from Verizon Modem: Actiontec) Dell Intel P4 2.40GHz 1GB RAM
20 sec (office PC, running DSL from ATT Modem: Netopia) Intel P4 2.60GHz 256 MiB RAM

Any ideas?

---

