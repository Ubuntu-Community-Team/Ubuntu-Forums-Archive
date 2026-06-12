---
title: "How to get into my BIOS?"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by kramer65 on 2012-02-28
Hello,

I am trying to get into my BIOS to set the bootup order. Unfortunately I don't get to see anything about what button to press to get into the bios. I tried continually pressing the ESC, F1, F12, and the delete button while booting up. But none of that works.

Does anybody know what I can do to get into my bios?

All tips are welcome!

---

### Post by collisionystm on 2012-02-28
try F2

---

### Post by Ms. Daisy on 2012-02-28
If F2 doesn't work, you can google the type of computer along with BIOS and you'll probably find it.

---

### Post by audiomick on 2012-02-28
You should perhaps mention what the machine is. Maybe there is some one here with the same one who could help you.

---

### Post by zero-g on 2012-02-28
Some BIOS's use F8 or F9 to select the boot up device. Give it a try

---

### Post by Jerry N on 2012-02-28
DELETE key works on my Gigabyte MBs

Jerry

---

### Post by jwbrase on 2012-02-28
> **kramer65 said:**
> Does anybody know what I can do to get into my bios?

It depends entirely on the manufacturer and model of your computer. Thoughtful manufacturers will generally have something along the lines of "Press <key> to enter system setup" on the boot splash screen. If they don't have that, you'll just have to Google it, or failing that, mash keys until something works. Sometimes it also has to be pressed at a certain time during the POST (power on self test), and it always has to be pressed before the BIOS hands control of the machine over to the bootloader.

---

### Post by I2k4 on 2012-02-28
Go to the documentation for the computer you own - this is a thing that varies by manufacturer, and you don't specify a make or model.

---

### Post by kramer65 on 2012-02-29
Alright. I got into my BIOS and set the boot order as follows:
1st Boot Device: CDROM
2nd Boot Device: Removable Dev.
3rd Boot Device: HDD
4th Boot Device: Network
(see first attachement for image)

When I boot up and press F8 I get a pop-up screen in which I can select the boot device (see second attachement). In this menu however, I don' t see any option to select the USB-stick.

Am I doing something wrong or is my computer simply unable to handle booting through USB?

---

### Post by nothingspecial on 2012-02-29
That would be the removable device option.

---

### Post by kramer65 on 2012-02-29
I know. But it apparently doesn't recognize the usb-drive as a viable option when I am actually booting up. See the second image for the options which I have for booting up..

---

### Post by Ms. Daisy on 2012-02-29
What happens when you make the removable device first in the boot order?

---

### Post by Gremlinzzz on 2012-02-29
when you click on removable device does it offer a choice?:popcorn:

---

### Post by mastablasta on 2012-02-29
is you USB marked/flagged as boot device?
 
I am guessing you used unebootin or similar to add linux on it?!
 
additionally some USB keys behave strange and could refuse to boot (i.e. they do not show up on this boot list as they should).

---

### Post by kramer65 on 2012-03-02
Alright. I reached the BIOS (it turned out to be delete after all.. :roll:)

I switched the usb device to the first device to boot from but this still didn't let me boot from the usb-drive. After a while I walked to the computer store down the road and they concluded that my usb-stick wasn't "active". So he went into his windows pc to the command line and turned it into "active mode" (or something like that).

So finally I was able to boot, and I just installed Ubuntu 12.04 beta1 (which I am so far really happy with!)

Thanks a lot for all your advice!! :D

---

