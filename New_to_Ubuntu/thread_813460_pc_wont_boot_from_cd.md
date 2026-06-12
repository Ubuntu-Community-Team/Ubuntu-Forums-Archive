---
title: "pc wont boot from cd"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by DasLegionnaire on 2008-05-30
so i just got a new mobo from gigabyte and when I set up the bios to boot from the cd drive, it wont, even when I removed all other drives it would not boot from the cd, I have to boot from the cd to set up my hardware settings, the mobo is a gigabye gag33ms2l. any help?

---

### Post by spiderbatdad on 2008-05-30
do you get the boot options screen? The screen that asks you to start or install ubuntu.

---

### Post by DasLegionnaire on 2008-05-30
no, it will only try to boot from the sata hdd and when i disconnect that it tells me to put in systems disk (not sure if it means cd or floppy) but no matter what i do it wont boot from the cd drive.

---

### Post by spiderbatdad on 2008-05-30
do you have a floppy to flash the bios with? seems like your bios isn't working right. Hopefully, you got a manual with the mobo.

---

### Post by sweeneytodd on 2008-05-30
bios is a very temperamental thing, regardless of what u think you have done, reset bios to default factory settings, then only change boot order then try, if not, there is a little jumper on motherboard, clear bios, reset boot order and try again, if not, its probably not the bios, another thing, make sure the cd cable are correctly slotted, one more thing, make sure u earth yourself on frame of computer b4 touching motherboard as some circuits can short circuit with your own kinetic energy

---

### Post by abn91c on 2008-05-30
does the motherboard detect the cdrom? make sure you check your cd jumper settings and all the IDE cable connectors and power cables areset correctly

---

### Post by DasLegionnaire on 2008-05-30
what are jumpers?

---

### Post by DasLegionnaire on 2008-05-30
oh and i flashed the bios and no noticable difference, also, i may have my f-panel set up wrong, does that matter?

---

### Post by sweeneytodd on 2008-05-30
did u reset bios to default factory settings, not sure what f-panel is but if talking about bios resetting should resolve this, jumpers are those little plastic bits attached to little pins on motherboard, sometimes there is a little button not far from bios chip. the idea is to hold it down for a couple of seconds(button) or moving plastic bit to other pin for couple of seconds, as in short-ciruiting it, make sure you are playing with right pins or buttons though

---

### Post by DasLegionnaire on 2008-05-30
ok, so, i have flashed the mobo, reset the bios, f'ed with the jumpers, removed all other hardware, ive tried it all. i really don't know what to do. the f-panel is the front panel, im pretty sure i hooked some of that stuff up wrong.

---

### Post by sweeneytodd on 2008-05-30
don't think f-panel would do this, have you tryed another cd-rom

---

### Post by DasLegionnaire on 2008-05-30
i havent, because i don't have another, but i litereally just swapped out the mobo, why would the drive be f'ed?

---

### Post by sweeneytodd on 2008-05-30
what about swapping ide? cable with hard drive, are the pins at the back of cd all straight, u will have to pull it out to have a look

---

### Post by sweeneytodd on 2008-05-30
there is also a little jumper on the back of cd, make sure its set to slave,

---

### Post by kansasnoob on 2008-05-30
Have you checked out Gigabytes Manual:

[http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=2692](http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=2692)

---

### Post by DasLegionnaire on 2008-05-30
of course ive checked gigabytes manual, i also ripped apart an external cd rom drive and it didnt work either,

just so we have things straight:

I have an hdd hooked up through sata, that is my main drive

i have an hdd hooked up through ide

and i have a cd drive hooked up through ide, jumper on slave, just power and ide plugged in

bios is set to boot from cd, it doesnt....GAAAA!

---

### Post by DasLegionnaire on 2008-05-30
alright so i hooked up a cdr drive to an external enclosure and hooked it up to usb, and it worked, now once i get thrings running i can figure this all out

---

### Post by sweeneytodd on 2008-05-30
may sound futile, but are you sure the cd you are trying to boot isn't corrupted, have you another bootable cd you can try

---

