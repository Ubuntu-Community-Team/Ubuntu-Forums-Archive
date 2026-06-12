---
title: "Kubuntu 18.04 LTS won't shutdown (black screen)"
date: 2019-04-19
forum: New to Ubuntu
---

### Post by abulero on 2019-04-19
Hello everyone.


Recently  installed Kubuntu 18.04 LTS but it won't shut down and will also take  longer than usual to boot. I see people saying their Kubuntu systems  take 3-5s from grub to login whereas mine takes 15s+ while having an SSD  installed. But that's not the main point here. I can't turn off my  system. The screen stays black forever and I can't shut down without  resorting to the power button.
Can anyone help me  on how to solve/debug my system?


Note:  I already tried the highly popular "change the  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line in /etc/default/grub to  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"". I doesn't change  anything and I also tried changing the parameters from "quiet splash" to  simply "nonsplash". Some said it would enable a verbose shutdown but  nothing changes. Black screen all the way.


---System specs:
Dell Inspiron 7000 Notebook
Intel i7 - 8550U
GeForce 150MX
500GB Kingston SSD
8GB Ram


---What happens:
I try to reboot/shutdown and the screen goes black forever.

---

### Post by Rubi1200 on 2019-04-22
Hi and welcome to the forums :-)

First try creating a new user, logging in and doing a few things, then shutting down. If it works normally, then something is corrupted in your current profile and we need to look into that.

Thanks.

---

