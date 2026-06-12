---
title: "won't suspend on lid close"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by pcreqeust on 2012-12-30
Installed and updated Xubuntu 12.04 LTS yesterday on a Dell Inspiron B120 (has latest BIOS from a few years ago).  

I want the laptop to suspend when closing the lid on either AC or Battery.  I have set "Suspend" for "When laptop lid is closed" in Power Manager for both AC and battery.  When I close the lid, I see the backlight is still on, and the power LED is still solid on. I've waiting many minutes. When I [I]open[I] the lid, only then does it suspend.  The backlight goes off, and the power LED blinks.

If I push the fn key combo to suspend, that works fine.

---

### Post by pcreqeust on 2013-01-13
This is still a problem.  Any ideas?  Thanks.

---

### Post by squakie on 2013-01-13
I'm having a similar problem with an old Dell 1501.  I actually have mine set to hibernate, but it doesn't do it when the lid is closed - but if you open the lid in a couple of minutes it continues and goes into hibernation.

---

### Post by matt_symes on 2013-01-14
Hi

This is an odd one ! 

Have you checked to see if the kernel is getting an ACPI event when the lid is closed ?

Maybe the laptop is returning the ACPI event the kernel is expecting when the lid is opened ?

Buggy BIOS ?

I would start by opening a terminal and typing

```
acpi_listen
```

Closes the laptop lid and then open it. Wake it from suspend and post the results from the terminal back here.

That may give some clues.

Kind regards

---

### Post by squakie on 2013-01-14
With mine, it apparently knows it's supposed to hibernate, as it starts the process but never goes into hibernation.  Just opening the lid causes it to complete hibernation and power off.  I'll try your suggestion later.

---

### Post by matt_symes on 2013-01-14
Hi

@squakie.

It sounds like you have a different problem than the OPs. My last post was for the OP.

For you though, open a terminal and type

```
sudo pm-hibernate
```

Does it hibernate ?

Both of you: Please give the version of Ubuntu you are using and the kernel version.

```
cat /etc/lsb-release && uname -r
```

Kind regards
[]("http://ubuntuforums.org/member.php?u=1741485")

---

### Post by Curt101010 on 2013-01-15
Mine is doing the same, but I'm running Ubuntu 12.10 on a Compaq nc8230.  Here is what the output on the terminal is:

thermal_zone TZ1 00000081 00000000
thermal_zone TZ1 00000081 00000000
button/lid C1F3 00000080 00000001
button/lid C1F3 00000080 00000002
thermal_zone TZ1 00000081 00000000

Thanks!

---

### Post by squakie on 2013-01-15
Well, I guess my problem is a moot point - the laptop bit the dust today (can you say "don't drop it, have it land on a corner and break the display?).  ;)

---

### Post by MoFro624 on 2013-01-15
For me I set my Dell Latitude D600 to not suspend when the lid is closed. It wouldn't wake back up without re-starting the laptop. Go to Systems Settings>Power> There will be an option for Power scheme when the lid is closed. See what it is set at for suspending when the lid is closed. Try that and see what happens.

---

### Post by matt_symes on 2013-01-17
Hi

@curt101010

> Mine is doing the same, but I'm running Ubuntu 12.10 on a Compaq nc8230. 

Can you be a bit more specific. What is your laptop not doing ?

Kind regards

---

### Post by squakie on 2013-01-17
> **MoFro624 said:**
> For me I set my Dell Latitude D600 to not suspend when the lid is closed. It wouldn't wake back up without re-starting the laptop. Go to Systems Settings>Power> There will be an option for Power scheme when the lid is closed. See what it is set at for suspending when the lid is closed. Try that and see what happens.

For everyone - remember that hibernate, when it works, will power you PC down thereby saving the battery.  If you only use suspend, the battery is still being used.  So, at least for a laptop or perhaps even a netbook, I personally would use hibernate - it's the only way to save the battery.

---

