---
title: "Installing on Pentium 3"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by AJEllisuk on 2008-09-28
Hi

I'm trying to install Ubuntu on an older PC with a Pentium 3 450MHz CPU and 384MB RAM, and the Intel i440BX chip set. I keep getting these messages when I try to install, or run Ubuntu from the CD:

[0.000000] ACPI: bios age (1999) fails cutoff (2000), acpi=force is required to enable ACPI

Then I get a black screen with the following text:
BusyBox v1.1.3 (Debian 1:1.13-5ubuntu12) Built in shell (ash) 

If I type help I get a list of commands.

I have searched these forums for answers to these problems but none of the solutions offered seem to help.

I can run Ubuntu from a friends dell laptop with no problems and on my brothers pc with an AMD Sempron CPU without any problems.

Can someone please give me some advice on what I could do?

Thanks in advance

Andrew Ellis

---

### Post by bumanie on 2008-09-28
You should try xubuntu, it has a much lighter desktop environment and should run OK on those specs. Your ram is at the minimum to run ubuntu and the cpu is probably a bit underpowered, but xubuntu should work, if not, try damn small linux or puppy linux - they definitely will run very well on that system.

---

### Post by jimrz on 2008-09-28
> **AJEllisuk said:**
> Hi

I'm trying to install Ubuntu on an older PC with a Pentium 3 450MHz CPU and 384MB RAM, and the Intel i440BX chip set. I keep getting these messages when I try to install, or run Ubuntu from the CD:

[0.000000] ACPI: bios age (1999) fails cutoff (2000), acpi=force is required to enable ACPI

Then I get a black screen with the following text:
BusyBox v1.1.3 (Debian 1:1.13-5ubuntu12) Built in shell (ash)
When you boot the "live cd", at the first screen hit f6 and add ```
acpi=force live boot=break
```
then from resulting cli type in ```
modprobe piix
exit
```

These should get you going.I still have my old laptop that needs the "acpi=force" flag and used to have an old desktop that suffered from the "busybox" issue. My old LT (pIII 500 + 384Mb ram) does run ubuntu ok, but I find that using the fluxbox wm + various lighter weight apps gives a great increase in it's performance (much more so than xubuntu).

---

### Post by wolfen69 on 2008-09-28
> [0.000000] ACPI: bios age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
a bios update will fix that.
> BusyBox v1.1.3 (Debian 1:1.13-5ubuntu12) Built in shell (ash) 
try xubuntu alternate cd to install. xubuntu will run better with those specs anyway.

---

### Post by jimrz on 2008-09-28
> **wolfen69 said:**
> a bios update will fix that.

It may. However on my Thinkpad 600x the latest bios rev (2001), which is installed, contains a string somewhere that still triggers the bios age warning and forces the use of the "=force" flag. I have read that this is true of some other machines from that period, as well.

---

### Post by candtalan on 2008-09-28
> **AJEllisuk said:**
> Hi

I'm trying to install Ubuntu on an older PC with a Pentium 3 450MHz CPU and 384MB RAM, and the Intel i440BX chip set. I keep getting these messages when I try to install, or run Ubuntu from the CD:

[0.000000] ACPI: bios age (1999) fails cutoff (2000), acpi=force is required to enable ACPI

Then I get a black screen with the following text:
BusyBox v1.1.3 (Debian 1:1.13-5ubuntu12) Built in shell (ash) 

If I type help I get a list of commands.

I have searched these forums for answers to these problems but none of the solutions offered seem to help.

I can run Ubuntu from a friends dell laptop with no problems and on my brothers pc with an AMD Sempron CPU without any problems.
Andrew Ellis

I use ubuntu on similar machines, it is slow, but it is ok for, it is a matter of taste. I have installed ubuntu recently on similar machines with only 192MB ram - not using the live cd though, I used the alternate cd install.

384 mb ram should actually run as live cd ok, if slow, so the real problem is probably something else, maybe the cd drive reader or maybe the video.

Does the cd check itself ok from the live cd boot menu 'check this cd for defects'? this is useful to verify not just the cd which sounds maybe ok, but importantly checks that the particular cd can be read perfectly in that particular cd drive.

Other things being equal, also use the available options to use safe graphics mode from that early menu.

hth

---

### Post by AJEllisuk on 2008-09-30
> **wolfen69 said:**
> a bios update will fix that.

try xubuntu alternate cd to install. xubuntu will run better with those specs anyway.

Hi,

Thanks to all of you for replying.

I have tried pressing F6 and typeing "acpi=force", which didn't work, I also tried using xubuntu but i still have the same problems. 

Can anyone recommend a site where I could get a bios update. I tried typing the motherboard details "Intel i440BX" into google but didn't get anywhere.

Would it be best if I invested in a new motherboard?

Thanks

Andrew

---

### Post by wolfen69 on 2008-09-30
have you tried the [Alternate CD]("http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/xubuntu-8.04.1-alternate-i386.iso")? i would give that a go before doing anything drastic.

---

### Post by oldos2er on 2008-09-30
> **AJEllisuk said:**
> 
Can anyone recommend a site where I could get a bios update. 

 From the BIOS manufacturer's website.

---

### Post by snowpine on 2008-09-30
Hi I am sorry I don't have a specific suggestion, but I just wanted to say I successfully installed Ubuntu (using the Alternate CD) on my old Pentium 3... so don't give up, it is possible!

Good luck. :)

ps What I did was search for my specific brand and model number, I got a few good tips that way.

---

### Post by philinux on 2008-09-30
I have ubuntu running on a old pentium 3 500 320meg with same motherboard.

There is a 2000 bios which I used to get round that problem.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=208&DwnldID=3519&strOSs=22&OSFullName=Windows*%20Me&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=208&DwnldID=3519&strOSs=22&OSFullName=Windows*%20Me&lang=eng")

I was dual booting so I use windows me to make the boot floppy

---

