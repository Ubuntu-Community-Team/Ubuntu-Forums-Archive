---
title: "Ubuntu error on booting"
date: 2022-04-06
forum: New to Ubuntu
---

### Post by hahelie on 2022-04-06
Hi guys,


I am newbie to the Linux world and installed Ubuntu on my laptop after many problems.
Initially, I could not install as the installation always froze. I removed the HD from the laptop and put it on another machine where it was possible to install Ubuntu.
I replaced the HD back to my laptop and when linux starts it shows the following error (see attached picture). The last line keeps counting down the time, but nothing happens next.


Would anyone have any idea how to solve the problem?



Thanking you in advance.

---

### Post by hahelie on 2022-04-12
Bump

---

### Post by tea for one on 2022-04-13
> **hahelie said:**
> Initially, I could not install as the installation always froze. I removed the HD from the laptop and put it on another machine where it was possible to install Ubuntu.


Can you put the HD back into the laptop where you successfully installed Ubuntu.
Does Ubuntu boot there?

---

### Post by yancek on 2022-04-13
Is Ubuntu the only OS on the laptop you are trying to boot from?
Was Ubuntu the only OS on the other machine on which you actually instaled Ubuntu?
Are either/both machines UEFI?
Did you boot and install Ubuntu in UEFI mode?

---

### Post by hahelie on 2022-04-19
> **tea for one said:**
> Can you put the HD back into the laptop where you successfully installed Ubuntu.
Does Ubuntu boot there?

Yes, the Ubuntu boot in the laptop where I successfully instaled it.

---

### Post by hahelie on 2022-04-19
> **yancek said:**
> Is Ubuntu the only OS on the laptop you are trying to boot from?
Was Ubuntu the only OS on the other machine on which you actually instaled Ubuntu?
Are either/both machines UEFI?
Did you boot and install Ubuntu in UEFI mode?

1) No, Ubuntu is not the only OS on the laptop. I also have Windows 10.
2) Yes, Ubuntu was the only OS on the other machine.
3) Yes, both are UEFI
4) I booted and instaled in UEFI mode.

---

### Post by tea for one on 2022-04-20
> **hahelie said:**
> Yes, the Ubuntu boot in the laptop where I successfully instaled it.

Therefore, as Ubuntu boots in the PC where it was installed, it seems to be a hardware or possibly UEFI settings in your target laptop.
Is there anything esoteric about the hardware i.e. Trusted Platform Mode, Optane memory etc?

Boot into Ubuntu in your working laptop.
Download mkusb [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
Download and verify an Ubuntu 20.04 iso
Create a new USB installer

On your target laptop, reset the UEFI settings to default
Disable secure boot
Make sure Windows is not hibernating or encrypted
Boot the USB in UEFI mode

Can you boot into a live session?
If not, please describe what happens?

---

