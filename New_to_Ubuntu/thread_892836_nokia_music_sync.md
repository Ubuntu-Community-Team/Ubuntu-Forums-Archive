---
title: "nokia music sync"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by samforthelove on 2008-08-17
I have a Nokia 5300 Xpressmusic phone and i cant get it to show up.
i've tried kmobiletools and gmobilemedia and nothing seems to work.
any help? thanks.

---

### Post by neurostu on 2008-08-17
[http://ubuntuforums.org/showthread.php?t=234900](http://ubuntuforums.org/showthread.php?t=234900)

Have you read this thread?

---

### Post by t0p on 2008-08-17
> **samforthelove said:**
> I have a Nokia 5300 Xpressmusic phone and i cant get it to show up.
i've tried kmobiletools and gmobilemedia and nothing seems to work.
any help? thanks.

There's a program, **gnokii**, that *might* work with nokias. It's a command-line prog - If you wants its (rather minimalist) GUI, you'll also need **xgnokii.**

---

### Post by samforthelove on 2008-08-17
i've tried wammu.
and my phone doesnt run symbian.
idk what else to try.

---

### Post by tahina on 2008-08-17
According to the gammu phone database, the [5300 should work with gammu]("http://cihar.com/gammu/phonedb/nokia/710/"), for wich there's a GUI frontend named wammu... ```
sudo apt-get install wammu
```

(Maybe this is not exactly what you're looking for, though, since gammu/wammu seem to be more into using the phonebook, SMS, calendar and stuff, maybe not syncing music...)

---

### Post by samforthelove on 2008-08-17
okay i installed gnokii but when i go to open it
it opens and closes out really quick. 
i dont think its gonna let me put music on my phone.

---

### Post by t0p on 2008-08-17
Have you tried to see if **amarok** can transfer music to your phone?  I've never tried that particular function, but the amarok docs certainly claim it can manage music on a device.

---

### Post by samforthelove on 2008-08-17
im thinking amarok might work.
but my phone doesnt show up when
i plug it in. if it did amarok needs
to know the mount point so it can tell
where to send the stuff. so how do i figure
that out?

---

### Post by koshari on 2008-08-25
my wifes 5310 accepts mp3s via bluetooth and usb fine.

with usb you will need to change it to access as a storage device in the settings.

then it pops up with the memory card mounted fine,

the bluetooth is slower however it lets you copy the files to the phones memory however given the minimal internal memory we push these files across to a folder on the uSD card.

---

