---
title: "Unable to boot win 7 aftr clickin boot alongside windows...\"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by krishna yadav on 2012-03-29
First i installed_*** wubi.exe ***_and checked the option for install alongside win ,
by fortune my installation was done in 1st attempt .I installed*** ubuntu*** somewhere on my hard disk but  i am sure that i didn't deleted my windows 7 files and I can still browse my windows 7 files from Ubuntu explorer...
after the ***BIOS*** screen moves The control directly goes to Ubuntu without giving an  option to boot windows 7..
please help 


thanking in anticipation



Please do help.....

---

### Post by Bucky Ball on 2012-03-29
Wondering what release you are using. 10.04 LTS, 11.10, etc ...

If you can open a terminal (should be in Applications>Accessories or somewhere like it) you could try inputting:

```
sudo update-grub
```... reboot, and see if that picks up the Windows install. Have you just got your data files or you actually have Windows program files and the stuff that was on the same drive Windows was???

Also wondering ... are you just not getting a menu where you can pick operating systems when you boot???

Hit 'escape' or 'shift' after the BIOS boot (depends on the release) and you will get that menu. Windows may already be on it ...

---

### Post by Mark Phelps on 2012-03-29
Wubi installs from INSIDE Windows.  So, even though I've not used it, I wasn't aware that it had an "alongside" option.

Are you sure you didn't boot from Ubuntu and use that option and the Slider to shrink Win7 and THEN install alongside?

If you did the latter, you probably corrupted the Win7 OS filesystem in the process, as shrinking the OS from outside using Linux utilities sometimes does that.

---

