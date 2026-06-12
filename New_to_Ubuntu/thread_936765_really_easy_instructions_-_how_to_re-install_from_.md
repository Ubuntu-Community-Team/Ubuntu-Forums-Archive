---
title: "really easy instructions - how to re-install from cd"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by 3blaxcatz on 2008-10-03
[COLOR="Navy"]Hello,
still stuck with ubuntu

i was advised last time i posted to re-install ubuntu from the live cd

but i can not get the computer to boot from the cd

I have ubuntu on the computer ( I think I got rid of the windows os)

when i put the live cd into the drive and press start it just loads as normal into ubuntu

how do i force the computer to load from the live cd

please very simple instructions [/COLOR]

---

### Post by nothingspecial on 2008-10-03
You have to get into your computers bios.
When you restart your computer try holding down F12 or another F key. One of them should do it.
Or google the make and model of your computer with "access bios" or something like that.

---

### Post by 3blaxcatz on 2008-10-03
erm
i do not know what the computer bios is or what i would do if i got there

pressing F keys does nothing it starts up as normal tried all of of F keys

---

### Post by nothingspecial on 2008-10-03
Do you know your make and model. Look on the back.

---

### Post by 3blaxcatz on 2008-10-03
o.k
sorry replied to quickly
i now have a blue screen ROM PCI/ISA BIOS....etc

wot do i do now

---

### Post by billgoldberg on 2008-10-03
> **3blaxcatz said:**
> erm
i do not know what the computer bios is or what i would do if i got there

pressing F keys does nothing it starts up as normal tried all of of F keys

When you start your computer up, the very first screen you see will be something of your computer manufacturer.

Normally somewhere on the bottom or top of the screen there will be a line telling you how to access the bios.

So when you know what key to press, reboot and when you see that screen quickly press that key a few times and you'll be in the bios.

(if you see the grub, you are already too late and missed it)

Then somewhere in the bios you can set your boot preferences.

Make sure it will boot from cd first, harddrive must be second.

-

I don't know if this will help you, but here is a video about it:

[http://www.youtube.com/watch?v=Tc1t3c5Yke8](http://www.youtube.com/watch?v=Tc1t3c5Yke8)

(almost every computer has a different bios)

---

### Post by Sycron on 2008-10-03
You have to set to boot **first** from CD not from HDD-0.

---

### Post by nothingspecial on 2008-10-03
Try navigating with the arrow keys. Have a look if there are instructions on how you move through the menus somewhere on the screen. You are looking for boot list or boot devices or something to do with boot.
When you find it select boot from cd (or something similar). Insert the disc restart and you should be running the live cd.

---

### Post by 3blaxcatz on 2008-10-03
options on blue screen

STANDARD CMOS SETUP
BIOS FEATURES SETUP
CHIPSET FATURES SETUP
CHIPST FATURES SETUP
POWER MANGEMENT SETUP
PNP/PCI CONFIGURATION
LOAD BIOS DEFAULTS
LOAD SET DEFAULTS

ON OTHER SIDE OF SCREEN
INTEGRATED PERIPHERALS
SUPERVISOR PASSWORD
USER PASSWORD
IDE HDD AUTO DETECTION
SAVE & EXITE SET UP
EXIT WITHOUT SAVING

i do not see boot preferences

---

### Post by Sycron on 2008-10-03
go to bios features and tell us what it says ?

---

### Post by billgoldberg on 2008-10-03
> **3blaxcatz said:**
> options on blue screen

STANDARD CMOS SETUP
BIOS FEATURES SETUP
CHIPSET FATURES SETUP
CHIPST FATURES SETUP
POWER MANGEMENT SETUP
PNP/PCI CONFIGURATION
LOAD BIOS DEFAULTS
LOAD SET DEFAULTS

ON OTHER SIDE OF SCREEN
INTEGRATED PERIPHERALS
SUPERVISOR PASSWORD
USER PASSWORD
IDE HDD AUTO DETECTION
SAVE & EXITE SET UP
EXIT WITHOUT SAVING

i do not see boot preferences

They could be in one of the sub menu's.

Bare in mind that it could be that it doesn't actually say "boot preferences". However it should be fairly obvious once you see it.

---

### Post by 3blaxcatz on 2008-10-03
i saw boot under
BIOS FEATURES SET UP

long list 
and i can see boot sequence

with letter in yelloW
A,C,SCSI

---

### Post by nothingspecial on 2008-10-03
Anything about boot from cd? When you find it select it and save your changes.

---

### Post by billgoldberg on 2008-10-03
> **3blaxcatz said:**
> i saw boot under
BIOS FEATURES SET UP

long list 
and i can see boot sequence

with letter in yelloW
A,C,SCSI

That's most likely where you need to be.

I'm not sure what they mean with A, C , SCSI.

I don't know if anyone else will (I'm sure they'll will).

I would say, go online to you manufacturers website and I'm pretty sure they'll have instructions for that bios on how to set boot preferences.

I myself would just tamper with the bios a bit, but bare in mind that when you do something wrong you could make your pc unusable. You could then just change the bios back, but still, it could give you a scare.

---

### Post by Sycron on 2008-10-03
Could be C from CD-ROM ? I doubt.

---

### Post by 3blaxcatz on 2008-10-03
o.k
i am loading up normally so that i can check the letters of the drives

i've been to the website it was in german

and thanks for the link to the YouTube video it is really helpful

---

### Post by billgoldberg on 2008-10-03
> **3blaxcatz said:**
> o.k
i am loading up normally so that i can check the letters of the drives

i've been to the website it was in german

and thanks for the link to the YouTube video it is really helpful

Post the link to the website.

My German is a bit rusty, but I'll give it a try.

Maybe some German speakers could also read the website and help you.

---

### Post by 3blaxcatz on 2008-10-03
[http://www.amitech.dk/](http://www.amitech.dk/)

---

### Post by billgoldberg on 2008-10-03
> **3blaxcatz said:**
> [http://www.amitech.dk/](http://www.amitech.dk/)

That's not German, so I can't help.

I think it's a Scandinavian language, not sure which one but from the domain I would presume it is Danish.

Edit: you can change the language on the bottom of the left column to english.

---

### Post by nothingspecial on 2008-10-03
There`s a little button, bottom left to change it into english

---

### Post by tarps87 on 2008-10-03
Try translation the website with babelfish. [http://babelfish.yahoo.com/](http://babelfish.yahoo.com/)
The drive letters in Ubuntu will not be the same as your bios uses.
In boot sequence can you change the letters "A,C,SCSI" usually enter and then the arrow keys or +/- on the number pad with them highlighted

---

### Post by nothingspecial on 2008-10-03
Ah, but only the front page. What is the exact make and model of your machine?

---

### Post by tarps87 on 2008-10-03
Just found that too it doesn't seem to work on all pages though
Can you post your bios and pc/motherboard make

Argh nothingspecial you are too quick :)

---

### Post by Sef on 2008-10-03
> In see boot sequence can you change the letters "A,C,SCSI" usaly enter and then the arrow keys or +/- on the numberpad with them highlighted

Is there a boot from CD-Rom?  Go through the sequence to find it.

---

### Post by miegiel on 2008-10-03
> **3blaxcatz said:**
> i saw boot under
BIOS FEATURES SET UP

long list 
and i can see boot sequence

with letter in yelloW
A,C,SCSI

¨A,C,SCSI¨ means your boot oder is "boot from floppy, else boot from your 1st normal hard disk, else boot from you SCSI hard disk"

You probably don have a SCSI disk, it's a common disk type for older servers.

Try changing "A,C,SCSI" to "CDROM,C" or something similar with CDROM coming befor C.

good luck : )

---

### Post by 3blaxcatz on 2008-10-03
thanks so much everyone - someone just skyped me who is also very good at computers and he has talked me through the settings

I found the correct setting by using the arrow keys until
i saw CDROM, C

then saved and exit

then it re-booted from the live cd - it is now installing

oh and he told me that the website was from Denmark and not German

---

