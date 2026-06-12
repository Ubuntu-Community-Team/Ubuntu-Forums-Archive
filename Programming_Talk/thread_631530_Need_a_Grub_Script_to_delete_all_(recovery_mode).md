---
title: "Need a Grub Script to delete all (recovery mode)"
date: 2007-12-04
forum: Programming Talk
---

### Post by thenetduck on 2007-12-04
Hi was wondering if anyone out there has a script to remove (recover mode) from the listing of a computer. I know how to edit it by hand, I need a script to run on about 50 school computers. 

Thanks!

The Net Duck

---

### Post by LaRoza on 2007-12-04
Could you just rewrite Grub as you want it (if they will be the same on all computers) and just write a script to replace the old ones?

---

### Post by meierfra on 2007-12-04
You probably already know that,  but I just want  point out that  you also need to change

#alternative=true

to 

#alternative=false

(Otherwise the recovery mode will reappear after the next kernel upgrade.)

I don't know how to  write scripts. But all the script has to do is:

Change  "# alternative=true" in /boot/grub.menu.lst" to "# alternative=false"

and then  run "sudo update-grub"


Somebody here should be able to tell you how to write such a script.

---

### Post by thenetduck on 2007-12-04
Thanks that's what I needed to know... you da man or woman or whatever..

The net duck

---

