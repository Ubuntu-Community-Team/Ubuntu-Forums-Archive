---
title: "dual distro failure"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by nnjond on 2011-10-14
Hi,

I have dl the upgrade Kubuntu 11.10 and installed it without a snag, but the gui is strewn with bugs and and soon freezes streight after the pasword panel. (-And it wont let me load the failsafe mode)

Now my Ubuntu issue of 9.10 even crashes or freezes in live mode.

Can anyone give me advice please?

---

### Post by matt_symes on 2011-10-14
Hi

Run a memory test ? Check for overheating ? Check hard drive SMART status ?

Kind regards

---

### Post by Johnb0y on 2011-10-14
> **matt_symes said:**
> Hi

Run a memory test ? Check for overheating ? Check hard drive SMART status ?

Kind regards

+1

without more information, little we can do! thanks.

---

### Post by nnjond on 2011-10-14
Thanks for your help.

I'm pretty sure it's not over heating.

# How do I run memory tests
#              SMART test
# What else would you like to know

-from a live cd which is performing much better than my installed os.

---

### Post by matt_symes on 2011-10-14
Hi

> **nnjond said:**
> -from a live cd which is performing much better than my installed os.

The LiveCD is performing alright ? It may not be hardware then. It is always worth checking these thing out though.

> # How do I run memory tests[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

> #              SMART testUse disc utility to run a SMART test. 

Or from the terminal type

```
sudo apt-get install smartmontools
```Enter you password. It will not be echoed to the screen. Then

```
smartctl --test=long /dev/sda
```to run the test (assuming the drive is sda). It will take a while. When it has finished type

```
sudo smartctl -a /dev/sda
```to get SMART information. Post it back here if you want to.

> # What else would you like to knowCheck wiring, cabling and build up of dust. After that it is worth looking for a software issue.

Kind regards

---

### Post by whitethorn on 2011-10-14
Removed reply

---

