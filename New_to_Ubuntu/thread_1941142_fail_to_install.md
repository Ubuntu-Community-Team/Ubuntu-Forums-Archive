---
title: "fail to install"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by Edge92 on 2012-03-15
I have been trying to install 11.10 for the past few hours with no luck.  I have the ISO burned to a disk, and I can get to the first screen, which looks nothing like the install screen from the instructions here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Once I hit install it jumps strait to a screen that looks like DOS, it runs what looks like some tests, and then stops....I can type in this screen so it is not locking up but it will just sit there for ever...well at least an hour.  

Any thoughts on what is going on?

---

### Post by Perfect Storm on 2012-03-15
What's the specs of your computer?

what happens if you type **startx**

---

### Post by Edge92 on 2012-03-15
AMD phenom quad core processor
4 gb ddr3 ram
win 7 64 bit


I tried using one of the alt downloads and it had a bit of a different effect.

it still goes to the dos like screen but now after is cycles through some stuff it says this over and over again.

Udevd[146]: timeout: killing '/sibin/mod probe then a long set of numbers.

I will try that start x on the first disk I have.

---

### Post by Perfect Storm on 2012-03-15
Can you give more info on your hardware with more details (including video card etc. etc.)

---

### Post by Edge92 on 2012-03-15
graphics card is a EVGA 550 ti
harddrive is a 1 td Toshiba
mother board is...i have no idea.
i think that is about everything...

and startx did nothing

---

### Post by Perfect Storm on 2012-03-15
Also try this;
In bootup screen press [tab] and add -- acpi=off to the bootup line command.

---

### Post by Edge92 on 2012-03-15
ACPI is already off according to the splash screen F6 options can look at.

do you want me to describe the screen I get where I can chose to install?  it dose not look right, if i didn't know better it looks like it is an older style, not the style it shows in the instructions.

it is laid out like this 
__________________________________________________________________________________________________-

[CENTER]Ubuntu
Try Ubuntu with out installing
Install Ubuntu
Check disk for defects
test memory
boot from first hard disk


f1 help   F2 language   F3 Keymap   f4 modes  f5 accessibility  f6 other options[/CENTER]

__________________________________________________________________________________________________

---

### Post by Perfect Storm on 2012-03-15
Can you please post the bootup commandline.


Edit: I'm wondering if it may be the video card. I have seen other here at the forum having trouble with the 550 model.

---

### Post by Edge92 on 2012-03-15
sure...no problem....I thought this was the absolute beginner forum....how exactly do I do that?

---

### Post by Perfect Storm on 2012-03-15
> **Edge92 said:**
> sure...no problem....I thought this was the absolute beginner forum....how exactly do I do that?

So you  try didn't bootup in F6 options with the ACPI off?


EDIT: check about the bootup options here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Edge92 on 2012-03-15
you sir are a gentlemen and a scholar. I did not have the ACPI off checked

I thought it was off or on, not a thing that could be checked.

Things seam to be going well.

---

