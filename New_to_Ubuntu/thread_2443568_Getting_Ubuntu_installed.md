---
title: "Getting Ubuntu installed"
date: 2020-05-17
forum: New to Ubuntu
---

### Post by pkmurray3 on 2020-05-17
I can't get Ubuntu to boot from a USB

I am trying to replace a windowsXP operating system on an Acer Aspire minilaptop.
I have downloaded Ubuntu onto a USB memory stick.
I have tried to boot from this but the laptop persists in booting Windows.
I have put USB first on the boot order using setup.
I have pushed F12 as it starts and it takes me to a menu and I have chosen USB, but it persists in booting windows.
Does the Ubuntu download need to be the only thing on the memory stick for this to work.
Thanks for any thoughts and advice.

---

### Post by CelticWarrior on 2020-05-17
Yes, it needs to be the only thing in that USB and it needs to be bootable, something you can't achieve by simply downloading Ubuntu onto a USB memory stick as you apparently did.

Assuming you're doing that in Windows you can use [Rufus]("https://rufus.ie/") or [Balena Etcher]("https://www.balena.io/etcher/"). Please be aware all contents of that USB stick will be deleted so don't forget to make a backup if they're important.

---

### Post by CatKiller on 2020-05-17
> **pkmurray3 said:**
> Does the Ubuntu download need to be the only thing on the memory stick for this to work.

You don't just put the file on the drive, you need to write the image to the drive. [Here](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview) are some instructions.

---

### Post by ActionParsnip on 2020-05-17
Copying the ISO using Windows file manager doesn't work. You need an application (as stated above) like Rufus to transfer the files from the ISO as well as making the USB bootable.

---

### Post by pkmurray3 on 2020-05-17
Thanks for the help.

---

### Post by pkmurray3 on 2020-05-17
Now I have a second problem.  When I use the new bootable USB stick, my little computer says that the kernel requires an X86-64 CPU but only a i686 CPU is detected.
please use a kernel appropriate for your CPU.
Do I need a different version of Ubuntu?
How do I find that?
Thanks

---

### Post by CelticWarrior on 2020-05-17
Yes, you have a 32-bit computer - not at all surprising - so you need 32-bit Ubuntu (or something else). The last still supported Ubuntu release for 32-bit is 18.04 (supported until 2023). 

Now the problem: If it's 32-bit and from the XP era now is an ancient almost unusable computer. Vanilla Ubuntu is a bad choice, it's too much for that hardware. Some lighter Ubuntu flavor like Lubuntu would be the suggestion but flavors have only 3 years of support therefore the last 32-bit Lubuntu has less than a year left (April 2021).

Try Debian 32-bit or AntiX. Nothing in the Ubuntu family is likely to work that old hardware satisfactorily.

---

### Post by CatKiller on 2020-05-17
> **pkmurray3 said:**
> When I use the new bootable USB stick, my little computer says that the kernel requires an X86-64 CPU but only a i686 CPU is detected.

Ubuntu stopped making 32-bit install images back in 2017. There are still some distros that haven't yet dropped support for ancient 32-bit machines, but a lot of applications have stopped doing those builds.

---

### Post by pkmurray3 on 2020-05-17
Thank you for the advice.
When I have downloaded the new kernel, do I do the same thing to make a bootable USB stick with Rufus?
Appreciate your help.

---

### Post by CelticWarrior on 2020-05-17
After you've download the 32-bit installation ISO do the same. That never changes.

---

### Post by Dennis N on 2020-05-17
You could use Ubuntu MATE 18.04 which has a 32-bit version download here:
[https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

---

### Post by drjdmartin on 2020-05-18
I'd definitely say Lubuntu 18.04 would be my choice - I've recently used it to resurrect two 15 year old Acer laptops which has been excellent given the current situation. I can remote into work off these old machines and leave the better computers for people in the house who need the processing power and memory.

Whilst the overall distribution is now not going to be upgraded again the LTS version is officially supported until April 2021 and some software support may still continue after that.

---

### Post by mörgæs on 2020-05-18
Another option is Debian:
[https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890](https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890)

---

