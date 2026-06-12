---
title: "Execute script at shutdown?"
date: 2014-10-19
forum: New to Ubuntu
---

### Post by dejan_87 on 2014-10-19
Hi,
I have acer aspire v5-571 laptop and ubuntu 14.10 beta installed on it.My laptop reboots instead of shutdown and i have this problem for 2 years... Why is it so hard for developers to fix this bug..?? Anyway i thing i find a workaround.Before shutdown i have to execute this command as root: ```
for i in /sys/bus/usb/devices/*/power/control;
    do echo on > $i
done
```After this laptop shutdown fine.
Is there a way to execute this command at shutdown?
Sorry for my bad english and thanks.

---

### Post by ian-weisser on 2014-10-19
> **dejan_87 said:**
> Why is it so hard for developers to fix this bug..?

Two likely reasons:
1) Most Ubuntu developers are volunteers (so be nice).
2) Most Ubuntu developers cannot replicate the bug on their equipment.
You are welcome to locate the buggy code and submit a patch, too. It's a community effort.


> **dejan_87 said:**
> Is there a way to execute this command at shutdown? 
Yes, but not at every possible shutdown. 
Start with /etc/init/shutdown.conf

---

### Post by matt_symes on 2014-10-19
Hi

> Why is it so hard for developers to fix this bug..??

Why do you think the is a Ubuntu/Linux bug ?

This may be a bug in ACPI on the motherboard that the manufacturers chipset drivers fix.

If you look through the kernel source code you will see loads of quirks that are used to get around buggy firmware and hardware that does not match the specifications.

How do you know the developers have your make/ model and even the differing chipsets between the same model of your or any laptop ?

They require detailed bug reports and, sometimes, access to the hardware itself.

Don't be so hard on them. You have a work around and such is the flexibility of Linux.

Kind regards

---

### Post by whitesmith on 2014-10-19
I used to be a lead developer at a well-known software house in the Pacific Northwest. You know the one I mean. Between 2000 and 2004 I averaged $120K for adding new features and fixing bugs...lots of bugs. I do what I can for Linux but everything is performed on a voluntary basis. Keep this in mind when you complain about how long it takes to get bugs swatted. By the way, Linux is generally fixed faster (and in my opinion, better) than That Other Operating System.

---

