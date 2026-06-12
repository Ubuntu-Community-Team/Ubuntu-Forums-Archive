---
title: "a program/code that allows to copy all data from flash stick to hdd when inserted"
date: 2008-05-20
forum: Programming Talk
---

### Post by meborc on 2008-05-20
the title says it all... i constantly transfer files to and from my computer... i would like to find a way to automatically copy all data from a usb stick to a specified hdd folder when stick is inserted

is that too complicated to achieve? any ideas?

---

### Post by inaety on 2008-05-20
a program could easily be made but a command would probably be just as easy

```
sudo cp "/mnt point of usb" "/folder"
```

---

### Post by dtmilano on 2008-05-20
If you are synchronizing them in any way, 'unison' is worth a try.

---

### Post by panayk on 2008-05-20
Since you probably don't want to run the command manually each time you mount the device, this will be useful:

[http://www.gradstein.info/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/](http://www.gradstein.info/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/)

---

### Post by meborc on 2008-05-22
> **panayk said:**
> Since you probably don't want to run the command manually each time you mount the device, this will be useful:

[http://www.gradstein.info/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/](http://www.gradstein.info/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/)

thank you, just what i was looking for! :)

---

