---
title: "HOT! laptop; help"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by AcademyKP03 on 2008-06-15
I have Ubuntu - Hardy Heron.

I've noticed that my laptop get really hot while normal use; ie surfing internet.

I went into terminal and typed: acpi -V

I noticed the temp was at 82.0 degrees C 

I then, from experience, unplugged the AC power to the laptop (by the way, its an Alienware laptop); then the temp. went down INSTANTLY!

You can see the temperature drop in the following:

All within 20 seconds (81C to 67C)

Any ideaS????

john@john-laptop:~$ acpi -V
     Battery 1: charging, 33%, rate information unavailable.
     Thermal 1: ok, 82.0 degrees C
  AC Adapter 1: on-line
john@john-laptop:~$ acpi -V
     Battery 1: charging, 33%, rate information unavailable.
     Thermal 1: ok, 82.0 degrees C
  AC Adapter 1: on-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 81.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 81.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 80.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 78.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 76.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 74.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 73.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 72.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 72.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 72.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 33%, rate information unavailable.
     Thermal 1: ok, 72.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 31%, rate information unavailable.
     Thermal 1: ok, 67.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$ acpi -V
     Battery 1: discharging, 31%, rate information unavailable.
     Thermal 1: ok, 67.0 degrees C
  AC Adapter 1: off-line
john@john-laptop:~$

---

### Post by saj0577 on 2008-06-15
Whats the question mate?


Saj

---

### Post by cespinal on 2008-06-15
nop... no ideas...but do want to know how to do to make that command show my laptops temp....

---

### Post by AcademyKP03 on 2008-06-15
> **saj0577 said:**
> Whats the question mate?


Saj

Why does my laptop overheat with the AC power plugged in?  Why does it cool down right away when I disconnect the AC power?


Lastly, how can I edit or config so that the laptop doesn't overheat?

I imagine that some software configuration kicks in when I unplug the AC power, resulting in cooler temps ... that I might be able to emulate, but *with* the AC power?

Any ideas?

Thanks again ...

---

### Post by saj0577 on 2008-06-15
```
acpi -V
```

---

### Post by AcademyKP03 on 2008-06-15
> **cespinal said:**
> nop... no ideas...but do want to know how to do to make that command show my laptops temp....

I typed: acpi -V

@ terminal

---

### Post by saj0577 on 2008-06-15
> **AcademyKP03 said:**
> Why does my laptop overheat with the AC power plugged in?  Why does it cool down right away when I disconnect the AC power?


Lastly, how can I edit or config so that the laptop doesn't overheat?

I imagine that some software configuration kicks in when I unplug the AC power, resulting in cooler temps ... that I might be able to emulate, but *with* the AC power?

Any ideas?

Thanks again ...


IT will overheat because its charging a batter much like when you re charge rechargeable batteries in a socket.

There is a way to tell your computer to shutdown at a certain temperture but I am not sure as to how, I shall research it. 

If its overheating even without AC power then its probably the processor working too hard with all your open applications.


Saj Hope it helped

---

### Post by AcademyKP03 on 2008-06-15
> **saj0577 said:**
> IT will overheat because its charging a batter much like when you re charge rechargeable batteries in a socket.

There is a way to tell your computer to shutdown at a certain temperture but I am not sure as to how, I shall research it. 

If its overheating even without AC power then its probably the processor working too hard with all your open applications.


Saj Hope it helped

No, it won't overheat w/out the AC power.  I've noticed in the past - if I'm doing something really intensive ... like loading up another O/S in VirtualBox -- it'll overheat pretty easily ... shut off ....

I've seen the temperature say that it's hit 103C! automatically turns off ... and then when I try to restart it -- can't .... says something about the Xserver ... image not found ..... after trial and error ... realized I could simply restart in safe grapics mode - with the AC power UNPLUGGED .. and allow Ubuntu to fix itself ... and then, sure enough ... I can login in normally ....

---

### Post by the_doc on 2008-06-16
I would suggest that some kind of heat increase is to be expected during charging, but it shouldn't overheat and shut off when firing up a VirtualBox image.

How old is this laptop?

---

