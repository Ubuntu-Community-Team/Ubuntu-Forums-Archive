---
title: "locked sd card by password"
date: 2016-09-26
forum: New to Ubuntu
---

### Post by mavyge2017 on 2016-09-26
may i have some support please
i make an locked sd card by password

and now i can not see any more the sd card

there is a command that i restore data from sd card ???

this is the command with my password from my sd card

sudo ./mmc lock_sd /dev/mmcblk0 <password snipped>

i am looking forward for your support

thank you

---

### Post by QIII on 2016-09-26
Hello!

What do you mean by you can't see the card?

Is it not shown as a device?
Are you unable to mount it?
Are you unable to view the files?

---

### Post by mavyge2017 on 2016-09-27
yes after i put this command the card is gone 
i can not see as a device
i am unable to see files
i can not recognize the card even on windows os
on the ubuntu whn i insert the card nothing is showing :(

there is a command that i can restore password??

---

### Post by sudodus on 2016-09-27
Please tell us where you found the command line ```
mmc lock_sd ...
``` and how you installed the tool.

That way we have a better chance to help.

---

### Post by mavyge2017 on 2016-09-27
i will upload de mmc tool password


[http://www.filedropper.com/mmc](http://www.filedropper.com/mmc)

[http://www.filedropper.com/mmc](http://www.filedropper.com/mmc)

---

### Post by sudodus on 2016-10-03
I can't see anything about mmc at that link. (Maybe it is necessary to be 'a member of the club'.)

I think this is not a standard linux or Ubuntu tool, so I don't know. If you are lucky, someone who knows will read this and help you. Maybe you have batter luck, if you ask at the Filedropper web site.

---

### Post by mastablasta on 2016-10-03
why not just use LUKS?: [SIZE=2]http://askubuntu.com/questions/652557/encrypting-sd-card
[/SIZE]

---

