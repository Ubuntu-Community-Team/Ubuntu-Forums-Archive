---
title: "New load lockup or video issue?"
date: 2017-04-30
forum: New to Ubuntu
---

### Post by mbmsg on 2017-04-30
Had an old vista machine finally got around to installing ubuntu on. Everything went well, nothing really loaded on machine but as I was gathering various apps ( ubiquiti controller, anonymous browser, etc) to load, screen locked up with colorful ant races, I can't tell if machine is locked up or video is messed up. I did a physical reboot, half day passes while just doing regular browsing I get it again. 

Not it sure where to begin to see if it's a video issue or a machine/ram issue. Any ideas?

---

### Post by oldrocker99 on 2017-04-30
It does sound like a RAM problem. Try holding down the SHIFT key during boot to get into the GRUB menu, and select the RAM test. Run it for a few hours and see if there are any errors found.

---

### Post by RobGoss on 2017-04-30
What are the specs for this machine it would be helpful

---

### Post by mörgæs on 2017-05-01
Yes, we need the specs. Please copy the command ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, execute it and post lshw.txt in CODE tags.

---

