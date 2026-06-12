---
title: "cannot print w/ hp 1102w"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by consumer42 on 2012-12-26
i recently updated from 10.04 to 12.04 and can no longer print. i've spent the last three hours browsing/troubleshooting, but nothing is working.

i've followed about a half dozen strategies for solving this, and would appreciate any help. i know its impossible for you guys to help without details, but i'm not sure what info to give or where to find it.

i have reinstalled cups. when i tried to reinstall the hp driver the wizard didn't seem able to find the printer. when i open the "job attributes" window, the "job-printer-state-message" says "/usr/lib/cups/backend/hp failed".

---

### Post by fantab on 2012-12-26
Assuming that your upgrade went smooth, otherwise; I would suggest that you completely remove and reinstall '**hplip**'. Also delete any hplip and cups (dot).files you may be having. Then search for any remaining 'hp' in your 'file system' using 

```
$ sudo nautilus
```and delete them, if you find any.

Then check for Repositories using Synaptic and see if you have all the requisite repositories/sources  enabled. If you are in doubt use this [**online tool**]("http://repogen.simplylinux.ch/") to regenerate the repos, copy/paste the generated 'sources' into /etc/apt/sources.list using:
```
$sudo gedit /etc/apt/sources.list
```(You may have to enable 'Universe', 'Multiverse' and 'Backports' sources ).

Then 'apt-get update'.

Having satisfied yourself, you can move on to reinstall 'hplip' and 'hplip-gui'. (use Synaptic to see if cups or hp backend is installed). Make sure your printer is switched on and connected before you run the hplip-gui/ device manager. 
You must also set your printer as 'default printer' from System Settings- Printers.

---

### Post by newbie-user on 2013-01-29
Hopefully not reviving a dead thread...

I just got a p1102w today. Had issues at first with 12.04 where it just wouldn't print. I just opened a terminal, ran 
```
hp-plugin -i
```
It ran, until it couldn't find the firmware in /usr/share/hplip/data/firmware. It turns out it that the firware file is incorrectly named hp_laserjet_professional_p1102w.fw.gz when it should be named hp_laserjet_professional_p_1102w.fw.gz (notice the underscore after the "p"). Once I renamed the file, everything loaded correctly after running ```
hp-plugin -i
``` again. Now it prints just like it should.

---

