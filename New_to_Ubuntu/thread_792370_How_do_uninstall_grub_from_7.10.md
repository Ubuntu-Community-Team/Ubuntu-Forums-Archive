---
title: "How do uninstall grub from 7.10"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by reevine on 2008-05-12
I'm wondering how to uninstall Grub from 7.10 so that i can put Ubuntu on a different computer.

---

### Post by JoshuaRL on 2008-05-12
> **reevine said:**
> I'm wondering how to uninstall Grub from 7.10 so that i can put Ubuntu on a different computer.

Could you explain a little bit more?  You will need a bootloader of some type, and GRUB is the bootloader default in Ubuntu.  What exactly are you trying to do that requires taking GRUB off?

---

### Post by reevine on 2008-05-12
Well i was duel-booting and i deleted the ubuntu partistions because i wanted to remove Ubuntu and put it on a different computer. But when i start my computer grub gives me an error and it stops there.

---

### Post by Promaster91 on 2008-05-12
[Here]("http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/") is how you uninstall grub. Note: If you have 2 OS, it is not a good idea to remove Grub unless you want a different boot loader.

---

### Post by JoshuaRL on 2008-05-12
> **reevine said:**
> Well i was duel-booting and i deleted the ubuntu partistions because i wanted to remove Ubuntu and put it on a different computer. But when i start my computer grub gives me an error and it stops there.

What other OS are you running on that computer?

---

### Post by reevine on 2008-05-12
> **JoshuaRL said:**
> What other OS are you running on that computer?
Windows XP Pro

---

### Post by Promaster91 on 2008-05-12
If that is it then you can remove Grub. Since you only have one OS grub is not needed.

---

### Post by JoshuaRL on 2008-05-12
> **reevine said:**
> Windows XP Pro

Okay, if you have the installer disk then we can fix this really simply.

> **Promaster91 said:**
> If that is it then you can remove Grub. Since you only have one OS grub is not needed.

Not exactly true.  All OS's need a bootloader to load them.  GRUB is one, and Windows has their own.

From the XP install disk, go into the recover console.  You should be in a command prompt.  Do the following and it should be fixed:
```

fix boot
fix mbr

```
That will fix the boot and MBR (master boot record), the first partition on the HD and where the bootloader sits.  Windows should boot just fine then.

As far as funtioning after that, I can't be held responsible.

:lolflag:

---

### Post by reevine on 2008-05-12
But grub comes up with "Error 15"

---

### Post by reevine on 2008-05-12
> **Promaster91 said:**
> If that is it then you can remove Grub. Since you only have one OS grub is not needed.
But Grub comes up with "Error 17" or "Error 21"

---

### Post by JoshuaRL on 2008-05-12
> **reevine said:**
> But Grub comes up with "Error 17" or "Error 21"

That'll happen when you delete Ubuntu.  Follow my directions in the post above and it'll be fixed.

---

### Post by reevine on 2008-05-12
Working on that now. I'll get back to you when i get results.

---

### Post by reevine on 2008-05-12
It is asking me [Which Windows Installation would you like to logon to}
What do i do now?

---

### Post by JoshuaRL on 2008-05-13
> **reevine said:**
> It is asking me [Which Windows Installation would you like to logon to}
What do i do now?

You'll want to go into Recovery Console.  It is a command prompt,  Then enter those two commands.  Should fix it for you.

---

### Post by reevine on 2009-05-15
well this problem was solved thank you for your help

---

