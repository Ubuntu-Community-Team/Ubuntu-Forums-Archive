---
title: "Booting on Windows Xp first.."
date: 2008-03-04
forum: Philippine Team
---

### Post by killer_d76 on 2008-03-04
newbie po sa linux patulong naman po.. i was able to dual boot my laptop with ubuntu 7.10 /XP and i'm so happy with it!.. the reason why i wanted to boot on windows first para kasi pag-ginamit ng anak ko, it will boot directly on windows first, unti-unti ko kasi ini-introduce sa kanya 'tong Linux e, and i'm still on the learning part din hehehe.. thanks in advance

---

### Post by loell on 2008-03-04
**short **> edit nyo lang po ang grub menu.lst, and change the default entry number

**step by step**:

paste nyo po ang output ng command na ito

```
cat /boot/grub/menu.lst 
```

para malaman natin kung anong entry # nang xp.

---

### Post by Nhatz on 2008-03-04
yup tama si sir loell... edit mo yung /boot/grub/menu.lst mo pero make sure na ma-backup mo muna sya...

ex.
```
cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```

then hanapin mo tong part na to...

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0  [COLOR="Red"]<---------- 0 para default Ubuntu OS (4 ata for Windows basta paglaruan u nalang.. hehe)[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3 [COLOR="Red"]<---------- time ng delay (in sec.) bago mag boot sa default OS.[/COLOR]

Astig! :guitar:

---

### Post by killer_d76 on 2008-03-05
thanks guys! ;)... after playing with ubuntu for quiet sometime and following all your advices i was able to make it boot to window xp first..

okay i got another issue with ubuntu again.. after putting a tick or a check on all the  boxes inside the "software resource" and tried to update ubuntu?, seems like nothing happened but when i tried to shut it down  this message came up " NetworkManager: nm_dbus_signal_device_status_change: assertion 'cd_data->dbus_connection'failed" :confused:  and it didn't shut down the laptop and i need to press the power button to turn if off... have i done something wrong? :confused:

---

### Post by jayarsantos on 2008-03-18
I mad a post for this one, titled "Ubuntu: Load From Windows XP Bootloader". kung interesado lang kayo...

here is the link [My Computer by Takure]("http://computertakure.blogspot.com/2008/01/ubuntu-start-with-windows-xp-bootloader.html")

from this post makakakuha kayo ng idea kung pano gagamitin ang bootloader ng xp replaced ung grub.

---

