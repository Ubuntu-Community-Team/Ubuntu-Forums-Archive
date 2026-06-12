---
title: "Linux subsystems"
date: 2014-01-12
forum: Programming Talk
---

### Post by zooey on 2014-01-12
Hi,

i am developing python script, i need to know what kind of subsystem are IDE tapes, i see that SCSI tapes are scsi_tape, it is similar with IDE tapes=> ide_tape? And also does somebody know where is some list of all Linux subsystems available. Thanks

---

### Post by kostkon on 2014-01-12
Device management in Linux is handled by [udev]("http://en.wikipedia.org/wiki/Udev"). Therefore, you could use [pyudev]("http://packages.ubuntu.com/saucy/python-pyudev") or [pygudev]("http://packages.ubuntu.com/saucy/python-gudev") in your python script.

Hope that helps.

---

### Post by zooey on 2014-01-12
Hi,

yes i am using them, but i need to know what is subsystem for IDE tapes and also where is some list of available subsystems. I didn't find this info anywhere...

---

