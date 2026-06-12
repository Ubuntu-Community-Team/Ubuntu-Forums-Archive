---
title: "ATI-ish contro plan for speed, fan etc?"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Darkhaund on 2012-10-24
Is there an ATI or AMD ish application that lets me control my video card?

---

### Post by newb85 on 2012-10-24
Such an application would have to interface with your video drivers, and you haven't mentioned what drivers you're using or what card you have.

---

### Post by Mark Phelps on 2012-10-25
That's typically provided by the Catalyst Control Center, or as it's known today, the AMD Vision Engine Control Center.  This is installed as a byproduct of installing the AMD restricted drivers -- which for 12.10 is being reported as a major problem.

---

### Post by Darkhaund on 2012-10-25
Thanks for the responses so far.
My main concern is if ubuntu will "contol" my RADEON 6770 card at a good temperature etc etc.

any information on this?

---

### Post by Linuxisfast on 2012-10-25
Its not Ubuntu but the Radeon driver in the kernel that controls your card. The power management has come a long way in open source drivers as per last test done at Phoronix but the proprietary drivers still do a better job so if thats your concern, install the proprietary drivers.

---

### Post by Darkhaund on 2012-10-25
I am still very new and learning linux (ubuntu)
I would appreciate if you can tell me where/how can I get and install those propietary drivers.

Thanks in advance!

---

### Post by Mark Phelps on 2012-10-25
> **Darkhaund said:**
> I am still very new and learning linux (ubuntu)
I would appreciate if you can tell me where/how can I get and install those propietary drivers.

Thanks in advance!

We first need to know the make and model video card -- and what version of Ubuntu you are using.  If you don't know the video info, open a terminal, enter "lspci" -- and look for the line containing "VGA".  Post that information back here.

---

### Post by Darkhaund on 2012-10-25
I got Ubuntu 12.04 lts

and here is the info you requested

[FONT=verdana, arial, sans-serif][SIZE=1][SIZE=1]01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon HD 4770 [RV740][/SIZE][/SIZE][/FONT]

---

### Post by Mark Phelps on 2012-10-26
OK, you should be offered drivers under Additional Drivers.  Be sure to install the first set offered, not the "post installation" ones.

---

### Post by Darkhaund on 2012-10-26
ok that i done and thank you

What is the next step or am I DONE?

---

### Post by newb85 on 2012-10-26
I would try running the AMD Vision Engine Control Center, which Mark Phelps mentioned in post #3.

---

