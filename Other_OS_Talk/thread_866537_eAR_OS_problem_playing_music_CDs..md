---
title: "eAR OS problem playing music CDs."
date: 2008-07-21
forum: Other OS Talk
---

### Post by riromero on 2008-07-21
For the past several weeks I've been using the excellent eAR Media Center for music and video. I'm able to play my collection of ripped MP3 music just fine. Now I want to play music CDs. When I select that option using "Music"->"Listen to a CD" from the main menu I get the error...

    "could not set drive speed"

on the main screen. Playing the CD with the Sound Juicer gui works fine. My fstab entry for my CD player looks like this.

> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

In my ~/.mms/config I have the following specification...
> 
# CD/DVD path
# 
# The values on the first line must correspond to the values in
# /etc/fstab for your dvd/cd drive
#
# The second line is just the device repeated and then the name of the
# device as it will appear in the gui
#
cdrom = /dev/scd0
cdrom_name = /media/cdrom0/


I'm not sure if these values are correct. Any clues as to where I should look to debug this problem? I would be much obliged

- Reuben

---

### Post by riromero on 2008-08-04
Any help?

---

