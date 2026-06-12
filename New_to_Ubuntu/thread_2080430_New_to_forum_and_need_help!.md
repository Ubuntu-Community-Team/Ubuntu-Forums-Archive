---
title: "New to forum and need help!"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by kb7kuh on 2012-11-04
Hello all,

It's been many years since I used Red Hat.  Due to a lot of Win 7 crashes, I'm back!

I just loaded Ubuntu on my laptop.  I can get the wireless card to work when booted off the CD, loading the correct driver.  When I let it boot off the HD, it does not seem to want to load the driver.  it just stalls out.  It is a Alienware (dell) laptop, and a Broadcom wifi internal card.

Looking at it when it loads off the CD, it says the driver location is "bcmwl-kernel-source"

Any suggestions on how to load the Wifi driver booting from the HD?  I do have Internet when I plug in the Cat-5 from the router.

Thanks,

Don

---

### Post by idoitprone on 2012-11-04
> **kb7kuh said:**
> Hello all,

It's been many years since I used Red Hat.  Due to a lot of Win 7 crashes, I'm back!

I just loaded Ubuntu on my laptop.  I can get the wireless card to work when booted off the CD, loading the correct driver.  When I let it boot off the HD, it does not seem to want to load the driver.  it just stalls out.  It is a Alienware (dell) laptop, and a Broadcom wifi internal card.

Looking at it when it loads off the CD, it says the driver location is "bcmwl-kernel-source"

Any suggestions on how to load the Wifi driver booting from the HD?  I do have Internet when I plug in the Cat-5 from the router.

Thanks,

Don

bcmwl-kernel-source is a package

to install the package to your computer
connect to ethernet

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```reboot and see if your internet work

If it doesn't then you may need to load the proper kernel module

post the results of ```
lspci -nnk
```so we can advise you to load the proper module. 
It should be simple since it worked on the live usb

Broadcom wifi cards is common problem here

---

### Post by kb7kuh on 2012-11-04
OK.  

I have a silly question, how do I get a command line prompt?

---

### Post by Jeffreytooker on 2012-11-04
> **kb7kuh said:**
> OK.  

I have a silly question, how do I get a command line prompt?

Control Alt t

Jeffrey

---

### Post by kb7kuh on 2012-11-04
Thanks!!!

Of to bed, I will get back at it tomorrow and let ya know how it goes!

Don

---

### Post by kb7kuh on 2012-11-04
Well I ran the command line you posted and am now on the wireless network!:)

Thanks for the help, and I'm sure I will need more!

Don

---

