---
title: "what's thre easiest way to run Xubuntu"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by ah pook on 2008-05-03
ok. I have a spare 60 gig HD, and a spare CPU. What the best way, considering
there's no CDROM, and no USB to boot from. Can I d/l to an unused HD, install that to an unused  box, and get it to boot>

---

### Post by DBrocks on 2008-05-03
CDroms are like ridiculusly cheap. Only about 15 bucks for a bare minimum.

---

### Post by ah pook on 2008-05-03
for some reason the CDRON won't boot. any ideas?

---

### Post by DBrocks on 2008-05-03
Can you get into your BIOS and change the boot order?

And do you have another working machine? If so, what OS is it?

---

### Post by ah pook on 2008-05-03
yeah, I have a happily working AMD running Ubuntu, with 4 HD's. two of which are blank. I want to take one 38 HD and put XUbuntu on it and boot a CPU, and I'm not sure how to do that...

---

### Post by DBrocks on 2008-05-03
Okay, scrape up a floppy (may be difficult :lolflag:) (I am assuming you have a floppy drive in your AMD). Slap that old floppy disk into the drive. Now, download sbm.bin from here: [http://www.filewatcher.com/m/sbm.bin.1474560.0.0.html. ]("http://www.filewatcher.com/m/sbm.bin.1474560.0.0.html")

This is an image for a floppy that will allow you to boot to the cd, no matter how old your bios is. Open up a terminal and type:

sudo dd if=*Path/To/sbm.bin* of=/dev/fd0 

Pop out your floppy, stick the HDD into the old machine. Put the xubuntu CD into the old machine, and the floppy into the old machine, and Boot!

---

### Post by DBrocks on 2008-05-03
Bump. How did it go?
(Sorry, I am a very impatient person :lolflag:)

---

