---
title: "Simple USB memory stick backup"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-08-09
I want to backup my home folder to a usb memory stick. I dont want the backup  to be archived, and I dont want to include any hidden folders. It would be useful if the backup worked more like a synchronisation tool as I sometimes edit from the memory stick on other PC's. The other problem I have is that the laptop that I wish to use this on has no battery, so the date and time are not stored.

I currently use this as a script :-

#!/bin/bash
rsync -av /home/gary /media/disk

But it copies all the hidden folders.

Any help.

---

### Post by rockerphil on 2008-08-09
you could do it the "hard" way and just do a drag & drop bit with your file manager

---

### Post by celticbhoy on 2008-08-09
I really want it automated so that I just need to double click after each session, otherwise I will end up just switching off - I'm a bit of a lazy sod.

---

### Post by ingeva on 2008-08-09
> **celticbhoy said:**
> I really want it automated so that I just need to double click after each session, otherwise I will end up just switching off - I'm a bit of a lazy sod.

I would write a shell script to be run automatically after login. For instance, use the cp command. It has a lot of parameters but "cp --help >cpman" will give you a list of them in the file "cpman".

When you have made the script work as intended, add it to the auto-startup by going to "System", "Preferences", "Sessions".

The only prerequisite for the script would be that the memstick is in place .... :)

---

