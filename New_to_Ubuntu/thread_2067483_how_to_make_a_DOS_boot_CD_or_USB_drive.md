---
title: "how to make a DOS boot CD or USB drive?"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by mopalia on 2012-10-06
I need to update my Bios and the first step will be to boot  into DOS.  I'm sure this is covered out here, by=ut searches haven't found it.  Either a CD or from a USB drive is fine. Thanks! (And simple, non-terrifying procedures are appreciated.)

---

### Post by DuckHook on 2012-10-07
[http://askubuntu.com/questions/176141/how-to-create-dos-boot-usb-flash-drive-with-xubuntu](http://askubuntu.com/questions/176141/how-to-create-dos-boot-usb-flash-drive-with-xubuntu)

---

### Post by mopalia on 2012-10-07
> **DuckHook said:**
> [http://askubuntu.com/questions/176141/how-to-create-dos-boot-usb-flash-drive-with-xubuntu](http://askubuntu.com/questions/176141/how-to-create-dos-boot-usb-flash-drive-with-xubuntu)

Thanks, I guess I wasn't clear. I know how to boot to whatever I want (I have both Mint and Ubuntu installed), but I'm not understanding instructions on how to make a bootable DOS disk or a bootable USB drive. That's what I need to update the bios.

---

### Post by slooksterpsv on 2012-10-07
I say use FreeDOS or UBCD and put it on a flash drive along with the bios update files (in their own directory e.g. BIOS) then boot into Freedos or UBCD and flash that way. UBCD = Ultimate Boot CD - google it.

---

### Post by mopalia on 2012-10-07
> **slooksterpsv said:**
> I say use FreeDOS or UBCD and put it on a flash drive along with the bios update files (in their own directory e.g. BIOS) then boot into Freedos or UBCD and flash that way. UBCD = Ultimate Boot CD - google it.

Thanks, I think I actually understand this!  And I'm almost there, have all this downloaded already.  Now let's see if it works . . .

---

### Post by mopalia on 2012-10-07
Nope, no joy - can't write these to the USB for some reason, and can't seem to burn them, either.  I'm giving up.  Thanks anyway.

---

### Post by Cheesemill on 2012-10-07
You can use [Unetbootin]("apt://unetbootin") to create a FreeDOS bootable USB, just select FreeDOS from the drop down list and it will automatically download it and create a bootable USB.

---

