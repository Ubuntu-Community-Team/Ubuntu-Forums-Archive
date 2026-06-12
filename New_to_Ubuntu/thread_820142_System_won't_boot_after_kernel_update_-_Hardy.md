---
title: "System won't boot after kernel update - Hardy"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by wheelwrightmike on 2008-06-06
Hi, 
I've been running 8.04 on a Thinkpad T22.  The system was originally installed from the Beta of the Alternate install CD.  For some reason, it installed LILO rather than grub.  Today's upgrades included a new kernel.  After installing the upgrades a reboot was required.  The system will not boot.  

```
[ 283.733630] ACPI: PCI Interrupt 000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
```

I have tried to boot with the original Beta Alternate CD and it stopped at the same message.  And I just tried to boot with a system rescue CD and it stops at the same message.

Is this a hardware problem that just happened coinsident with the ubuntu update?  Any idea what it is?

Thanks,
-Mike from Cleveland, OH, USA, currently in Calgary, Alberta, CA

---

### Post by jemate18 on 2008-06-06
You said that LILO was installed instead of GRUB?
I think it is strange since Ubuntu installs GRUB by default.

---

### Post by wheelwrightmike on 2008-06-06
> **jemate18 said:**
> You said that LILO was installed instead of GRUB?
I think it is strange since Ubuntu installs GRUB by default.

I know.  And I have no idea why it installed LILO.  I tried installing grup from synaptic and if failed. 

Thanks,
-Mike

---

### Post by Sef on 2008-06-06
> Now, I planned on wiping 7.1 in order to install 8.04, but I read earlier this morning about a kernel update that kills wireless. If this is the case, I am stuck with gutsy.

Some people decide to install LILO instead.   Someone else had a similar problem.

On [[URL="http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5120191"]]("http://ubuntuforums.org/showthread.php?p=5120191#post5120191")another post[/URL] it was recommended to reinstall LILO.

---

### Post by wheelwrightmike on 2008-06-06
> **Sef said:**
> Some people decide to install LILO instead.   Someone else had a similar problem.

On [[URL="http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5120191"]]("http://ubuntuforums.org/showthread.php?p=5120191#post5120191")another post[/URL] it was recommended to reinstall LILO.

They suggest reintalling lilo from a live CD.  If I knew how to do that, I would try.  I just made a new live CD.  I posted back on that thread asking how.

Can I re install LILO from an alternate CD?  A thinkpad T22 can't boot from the live CD because the savage video card doesn't get set up right by the X server.

Thanks,
-Mike

---

