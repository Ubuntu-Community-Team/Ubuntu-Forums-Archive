---
title: "KVM: Disabled By Bios"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by rodrigues2 on 2013-10-14
Hi. I have a problem when trying to install Windows 8. I am currently running Ubuntu 12.10 and when I try to boot from the CD/DVD drive, I get a black screen with a blinking cursor and then it goes to a purple Ubuntu background. After that, this occurs:
> kvm: disabled by bios
I'm not sure if this is a Ubuntu or Windows problem so I came here anyway for an answer as to what's causing this.
Thanks in advance!

---

### Post by David D. on 2013-10-14
My understanding is that this is the result of a BIOS setting.  I get this on my computer too, but it does not affect anything unless you are trying to use a virtual machine.  If you want to get rid of this error message, go into the BIOS settings when you first boot up your computer and change the setting to activate KVM.

---

### Post by rodrigues2 on 2013-10-15
> **David D. said:**
> My understanding is that this is the result of a BIOS setting.  I get this on my computer too, but it does not affect anything unless you are trying to use a virtual machine.  If you want to get rid of this error message, go into the BIOS settings when you first boot up your computer and change the setting to activate KVM.
I don't seem to have that option in my BIOS settings.

---

### Post by ibjsb4 on 2013-10-15
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
kvm-ok
```

What it say?

---

### Post by rodrigues2 on 2013-10-15
> **ibjsb4 said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
kvm-ok
```

What it say?
The program 'kvm-ok' is currently not installed. You can install it by typing:
sudo apt-get install cpu-checker

I'll install it now.

---

