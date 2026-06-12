---
title: "Will Ubuntu destroy my CPU"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by dolphin194 on 2012-05-12
I have just finished installing Ubuntu 10.04 on my 2008 MacBook Pro and just read somewhere that running Ubuntu on a Mac will cause ***catastrophic CPU failure*** because of a secret type of chip that Apple puts in their computers!!! I am wondering whether is true or not. 

Is my CPU going to die from Ubuntu, or is it safe to continue running Ubuntu on my MacBook?

---

### Post by d4m1r on 2012-05-12
No, it is NOT true and it is 100% safe to put Ubuntu on your Mac Book. Literally thousands of people before you have done it ;)

---

### Post by dolphin194 on 2012-05-12
ok i was just making sure because a bunch of threads out there have said something about it killing the CPU in a Intel-Based Mac because of a different voltage or frequency or something.

---

### Post by vasa1 on 2012-05-12
> **dolphin194 said:**
> ok i was just making sure because a bunch of threads out there have said something about it killing the CPU in a Intel-Based Mac because of a different voltage or frequency or something.
It is possible to **include ****links **to the " bunch of threads out there".

---

### Post by codemaniac on 2012-05-12
> **dolphin194 said:**
> ok i was just making sure because a bunch of threads out there have said something about it killing the CPU in a Intel-Based Mac because of a different voltage or frequency or something.

It is a complete rumor .Can you please post some sources that justifies your statement .

---

### Post by |{urse on 2012-05-12
Ubuntu will blow your whole house up. Be careful with it.

---

### Post by lisati on 2012-05-12
> **|{urse said:**
> Ubuntu will blow your whole house up. Be careful with it.

:lolflag: It certainly provided some distractions in the Lisati household that could potentially disrupt blissful domestic harmony!

As others have said, it's likely to be rumour, and some links to help us check what the OP has been reading might be useful when making sure we're all on the same page.

---

### Post by |{urse on 2012-05-13
On some laptops, if Ubuntu doesn't support your cpu fan then yes. But still, that's not ubuntu's fault, it's the user's for not checking to see if your fan was running. Maybe that's what you were referring to?

---

### Post by 3rdalbum on 2012-05-13
> **|{urse said:**
> On some laptops, if Ubuntu doesn't support your cpu fan then yes.

Still no.

CPUs have a sensor in them called a "thermal diode". If the temperature in the CPU hits a critical level, the CPU shuts down to prevent damage. Even if your fan stops working, the CPU will turn off safely. Actually, it's even better than that; on many CPUs you can completely unplug the fan and the CPU will simply underclock itself. This means that the CPU keeps running at a vastly reduced speed and temperature, and you can save your work and shut down safely.

I must admit I've never heard of "Ubuntu not supporting your fan". The motherboard and the EFI (on a Mac) controls the fan regardless of operating system. You can sit on the bootloader screen for a year and the fan will still run, because the EFI and the motherboard are running the fan.

In short, running Ubuntu will not damage your hardware. There are safeguards in hardware to prevent CPU and motherboard damage, and nothing short of malicious software will damage the computer.

---

### Post by idoitprone on 2012-05-13
> **3rdalbum said:**
> Still no.

CPUs have a sensor in them called a "thermal diode". If the temperature in the CPU hits a critical level, the CPU shuts down to prevent damage. Even if your fan stops working, the CPU will turn off safely. Actually, it's even better than that; on many CPUs you can completely unplug the fan and the CPU will simply underclock itself. This means that the CPU keeps running at a vastly reduced speed and temperature, and you can save your work and shut down safely.

I must admit I've never heard of "Ubuntu not supporting your fan". The motherboard and the EFI (on a Mac) controls the fan regardless of operating system. You can sit on the bootloader screen for a year and the fan will still run, because the EFI and the motherboard are running the fan.

In short, running Ubuntu will not damage your hardware. There are safeguards in hardware to prevent CPU and motherboard damage, and nothing short of malicious software will damage the computer.

With something as brain dead as the acpi specification. I will not be surprised if some manufacturer think is ok to reinvent the wheel like in acer netbook. Fan is controlled in userspace

---

### Post by MiXor on 2012-05-13
@OP I guess one way to check that is to see how many threads in the Apple users subforum say "help, ubuntu has broken my mbp" :P 
I'm running Ubuntu on a 7.1, and I loooove it!

---

### Post by |{urse on 2012-05-13
> **3rdalbum said:**
> Still no.

CPUs have a sensor in them called a "thermal diode". If the temperature in the CPU hits a critical level, the CPU shuts down to prevent damage. Even if your fan stops working, the CPU will turn off safely. Actually, it's even better than that; on many CPUs you can completely unplug the fan and the CPU will simply underclock itself. This means that the CPU keeps running at a vastly reduced speed and temperature, and you can save your work and shut down safely.

I must admit I've never heard of "Ubuntu not supporting your fan". The motherboard and the EFI (on a Mac) controls the fan regardless of operating system. You can sit on the bootloader screen for a year and the fan will still run, because the EFI and the motherboard are running the fan.

In short, running Ubuntu will not damage your hardware. There are safeguards in hardware to prevent CPU and motherboard damage, and nothing short of malicious software will damage the computer.

One some laptops, generally with amd64 and manufactured by Acer it will. On the [Acer Aspire 5500]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer"), I had it happen to 2 of the 3 I purchased together right before my eyes. Try ubuntu on that model, let them benchtest for 5 or 6 hours and see if you dont hear a "fzt[SIZE="1"]pop[/SIZE]". I know there is a "thermal diode". Could have been faulty manufacturing (I got replacements which worked better but still couldn't run ubuntu).  

[http://askubuntu.com/questions/49477/acer-aspire-5532-overheating](http://askubuntu.com/questions/49477/acer-aspire-5532-overheating)

That isn't what was intended by "ubuntu doesn't support your cpu fan". I wouldn't even blame the above on Ubuntu, it's acer's bad cooling design.

The real question here is, does repeated overheating damage the cpu on some computers who have proprietary drivers for cooling which Ubuntu doesn't support? or not?

---

### Post by |{urse on 2012-05-13
> **idoitprone said:**
> With something as brain dead as the acpi specification. I will not be surprised if some manufacturer think is ok to reinvent the wheel like in acer netbook. Fan is controlled in userspace

Exactly, yes. I was trying to say what you did.

---

### Post by sammiev on 2012-05-13
> **dolphin194 said:**
> I have just finished installing Ubuntu 10.04 on my 2008 MacBook Pro and just read somewhere that running Ubuntu on a Mac will cause ***catastrophic CPU failure*** because of a secret type of chip that Apple puts in their computers!!! I am wondering whether is true or not. 

Is my CPU going to die from Ubuntu, or is it safe to continue running Ubuntu on my MacBook?

Would you buy a computer that can be nuked by another operating system? Enjoy Linux. :)

---

