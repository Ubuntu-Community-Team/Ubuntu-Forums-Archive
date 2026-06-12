---
title: "The Non-working Kernel Discussion Thread"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by ALex! on 2008-04-26
I've decided to start this thread because apparently many users are having the same problem: After the upgrade to Hardy Heron, the new kernel won't boot... It hangs with an error message saying

```
[12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1
[12.95975] ACPI: EC: read timeout, command = 128
```

Please post here any news about a possible solution... And make this post a sticky for helping other users with the same issue/bug...

Thank you!

---

### Post by frup on 2008-04-26
load a liveCD and try adding noacpi to the grub entry in /etc/menu.lst.

If you have done an upgrade you should still have your old kernels too. Press escape on grub to select them and you should be able to boot to them. If there is no fix currently for your system, booting on the old kernel should harm you too much for a week or two until the next kernel update which might well fix your problem.

---

### Post by ALex! on 2008-04-26
> **frup said:**
> load a liveCD and try adding noacpi to the grub entry in /etc/menu.lst.

If you have done an upgrade you should still have your old kernels too. Press escape on grub to select them and you should be able to boot to them. If there is no fix currently for your system, booting on the old kernel should harm you too much for a week or two until the next kernel update which might well fix your problem.

by "adding noacpi" do you mean I should add "pci=noacpi acpi=noirq" to the kernel line???

why via a livecd? can't this be fixed by 

```
sudo gedit /boot/grub/menu.lst
```

adding then pci=noacpi acpi=noirq

and then 

```
sudo update-grub
``` 

??????????

---

### Post by AndyCee on 2008-04-29
Hey, slightly unrelated but I had the exact same error when booting a Sony Vaio from a LiveCD.

The 'solution' so far in my case was to hit F6 ('options') and add acpi=off to the end of the line, as suggested by InfinityCircuit

[http://ubuntuforums.org/showthread.php?t=773342](http://ubuntuforums.org/showthread.php?t=773342)

I'm somewhat not impressed by command-line shenannigans in a LiveCD boot. That said, my wife's Vista laptop is about to be 'dualed'.

---

### Post by Gavie14 on 2008-05-28
I have the same problem with a Sony VAIO laptop also, I'm hoping the problem will be sorted in an update soon too.

If anyone has a "fool proof solution" then please post it here, thanks.

---

### Post by Varox on 2008-05-28
hi, i also have the same problem with a sony vaio, and the problem still remains in the 2.6.24-16 kernel which i just got...

---

### Post by Gavie14 on 2008-05-29
I think the noacpi boot option has to be entered but I haven't a clue how to do it. Could someone please help..?

---

### Post by Varox on 2008-06-03
I solved this issue by removing the option "quiet" on the kernel boot options. Removing acpi didnt work for me, sound dissapears if i start with "noacpi"

how to change kernel boot options: [https://help.ubuntu.com/community/Bo...496dc2cf9f7cbd](https://help.ubuntu.com/community/Bo...496dc2cf9f7cbd)

---

