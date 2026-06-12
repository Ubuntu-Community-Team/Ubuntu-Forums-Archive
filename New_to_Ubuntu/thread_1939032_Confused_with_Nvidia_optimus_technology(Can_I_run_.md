---
title: "Confused with Nvidia optimus technology(Can I run linux efficiently?)"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by mulroydm on 2012-03-10
I have been wanting to install Linux on my laptop(my only PC for that matter).  After playing around with a few live CD's and doing some research I have run into a dilema with my graphics card.  I have the Nvidia GeForce 540m with optimus technology.  I have read about Bumblebee and Ironhide projects but have found that they cause battery drainage or won't render the desktop correctly(By this I mean ubuntu defaults to unity 2d or I end up in a black terminal screen, and with mint it defaults to the older version of gnome and kde wouldn't work efficiently).  I am new to linux and want to know what my options are.  Should I look into running a light-weight desktop such as xfce, or am I misinformed on Bumblebee an such.  I own a Dell xps 15 l502x so there is no option in the bios to turn off the optimus technology.  Thanks for your time!

---

### Post by dekom on 2012-03-10
Since optimus is designed to toggle GPU load from dedicated card to integrated ones, I would assume that initial implementations of that technology for Linux isn't as ideal as ones provided by nvidia.  So, less efficient battery usage should be expected.

Also, changing desktop managers (XFCE, etc.) won't resolve the problem since they all run ontop of the xserver, which requires a load graphical driver.  That said, you may still be able to install Linux, without the optimus technology.  How much of a difference that would make? I am not sure.

---

### Post by mulroydm on 2012-03-11
How would I go about running Linux without the optimus technology?  Could I have it run on solely my Nvidia card, or would it default to the intel HD card?  If the latter is true, how much would it affect performance?

---

### Post by mcduck on 2012-03-11
> **mulroydm said:**
> How would I go about running Linux without the optimus technology?  Could I have it run on solely my Nvidia card, or would it default to the intel HD card?  If the latter is true, how much would it affect performance?

It depends on your computer, but if the system was designed by any intelligent person you should be able to decide one or the other GPU to be used from your computer's BIOS. Or at least force to use the nVidia one only.

In that case using the Intel GPU would give better battery life, and bad 3D graphics performance, while using only the nVidia GPU would give much better graphics performance but worse battery life.

The exact difference in performance/battery life is something you'll have to try yourself, as it depends on what exact hardware you have and what kind of applications you run.

---

### Post by Lekensteyn on 2012-03-17
Citation needed for "battery drainage" on Bumblebee or Ironhide. The latest Bumblebee version (3.0 as of this writing) uses a kernel module for reliably toggling the power on nvidia Optimus cards.

Unless your BIOS has an option for it, you cannot always run on the nvidia card ("discrete mode"). It'll then always run on the Intel card with the nvidia card always being powered on (unless the BIOS is set to use "Integrated mode")

---

