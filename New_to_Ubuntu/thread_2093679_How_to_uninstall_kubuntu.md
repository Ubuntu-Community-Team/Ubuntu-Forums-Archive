---
title: "How to uninstall kubuntu"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by mike0liver on 2012-12-11
I am currently running Kubuntu (I can't find out what version but it's beyond 11.10). I wish to uninstall Kubuntu so that I can temporarily install Windows to run some software that won't run on Linux (even using Wine).
 
My Toshiba Notebook NB100 does not have an internal CD drive but I have an external one which can be used to run the Windows disk. I have tried installing from the disk after modifying the boot device order in BIOS but it will not autorun and keeps default booting to Kubuntu.
 
Is there some way I can uninstall Kubuntu and then install Windows? I'd be happy to run Kubuntu and Windows from the same machine but I suspect I shall have memory/storage capacity problems.
 
Any help would be appreciated. Thanks.
 
Mike
 
PS: I'm not technical enough to understand anything but step-by-step instructions with jargon explained :-)

---

### Post by audiomick on 2012-12-11
I think you should look into installing Windows in a virtual machine. That would perhaps be easier than de-installing, installing, de-installing and re-installing, and it would mean that your Kubuntu install remains intact.

---

### Post by coffeecat on 2012-12-11
@mikeOliver, I've moved your post (+ the reply) from the old dead thread you posted to into its own thread. You're more likely to get help that way.

Good luck!

---

### Post by mastablasta on 2012-12-11
what disk size do you have?

you could split it (create empty disk space), install windows on newly created part of disk and then run grub repair tool (because windows overwrites the grub) to get dual boot in the end.

anyway if windows doesn't want to boto make sure the device is set to boot first, try to clean the DVD/CD. if the disk is faulty it will skip it and boot what is on hard disk. 

what windows are you trying to install btw? if XP then maybe virtualbox install or similar would indeed be good enogh.

---

### Post by mike0liver on 2012-12-11
Thanks for that. I see I have a couple of replies and will look into it to see if I can navigate my way through to a satisfactory conclusion. I appreciate everyone's assistance.
 
Cheers,
Mike

---

### Post by mike0liver on 2012-12-12
Hi Michael:
 
I wouldn't have the first idea of how to do this (I don't really understand what a "virtual machine" is :-()
 
The link you provided seems to be to another forum which I'll try if I get no joy here. Thanks for the response.
 
Mike

---

### Post by mike0liver on 2012-12-12
Hi Mastablasta:
 
Thanks. My hard drive is 80Gb. It is Win XP that I'm trying to install and I think there is something wrong with the disk. I tried using the disk which I used to install the OS on my desktop and it worked but I aborted it because I didn't want to invalidate my desktop installation :-)
 
Cheers,
Mike

---

### Post by audiomick on 2012-12-12
> **mike0liver said:**
> The link you provided seems to be to another forum ...

That link is in my signature. It wasn't intended to be directly related to your question... ;)

Virtual machine:
[http://en.wikipedia.org/wiki/Virtual_machine]("http://en.wikipedia.org/wiki/Virtual_machine")

In very simple terms, a VM is an operation system (guest system )installed inside a program running on the actual operating system of the machine (host system) that tricks the guest system into thinking it is controlling the machine when in fact it is just communicating with the host system which passes on the guest systems' messages to the hardware. 

I think this one is the one that sees most use in the Ubuntu world
[http://en.wikipedia.org/wiki/Virtualbox]("http://en.wikipedia.org/wiki/Virtualbox")

If you search for "virtualbox" in the software centre, you should find the package "Virtualbox ose". That is it.

I wont offer any advice on setting that up, as I have only really ever read about it. Suffice to say that it seems to have gotten rather easy in the last couple of years. Certainly worth looking at before you go de-installing a running system that you intend to re-install again.

---

### Post by audiomick on 2012-12-12
> **mike0liver said:**
> 
My Toshiba Notebook NB100 does not have an internal CD drive but I have an external one which can be used to run the Windows disk. I have tried installing from the disk after modifying the boot device order in BIOS but it will not autorun and keeps default booting to Kubuntu.

Incidentally, I think you would have less stress with this business if you take the VM approach, too. You would be reading a CD from a running system instead of trying to boot the machine from a drive it isn't recognising, or isn't looking for as a boot device.

---

