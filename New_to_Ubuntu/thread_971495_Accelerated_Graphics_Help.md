---
title: "Accelerated Graphics Help"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by raydanator on 2008-11-05
I have an ati rage 128 mobility card and am trying to get accelerated graphics. What can I do?

---

### Post by Peter09 on 2008-11-05
Hi can you post the output of the terminal command

```
lshw -C display
```

What version of Ubuntu are you running?

---

### Post by raydanator on 2008-11-08
here is that output. thanks for the help!

danny@Danny-Laptop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage Mobility M4 AGP
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master vga_palette cap_list
       configuration: latency=32 mingnt=8
danny@Danny-Laptop:~$

---

### Post by phidia on 2008-11-08
Does your card show up in System > Administration > Hardware drivers? If you see it there you can enable it. (Edit: I see you're using xfce so that menu location may not be available)

If it doesn't show up there look at the wiki [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") on installing the ATI driver.

---

