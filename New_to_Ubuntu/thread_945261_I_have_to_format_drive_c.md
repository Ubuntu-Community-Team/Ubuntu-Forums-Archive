---
title: "I have to format drive c:"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-10-12
I have windows as well as linux mint installed on my system.

Windows is acting funny again, and i cant fix it. here is the post i made on windows tech forums, but no one could solve it.

> I have noticed that recently my startup speed has reduced. Also once my laptop starts it works ok with normal speed, but after being used for 4 to 5 hours it just stops responding or its response is so slow that after clicking on the start button i have to wait for 2 minutes before it opens. even a right click takes this much time.

the only option left for me is a hard reset. but when the computer restarts again, the speeds are normal and as they should be. The problem starts again after 5 hours of usage, and the cycle continues.


so.... any ideas as to what may be causing this???


I have avira antivirus free, regularly updated.

I have scanned my system with the latest ad aware 2008, it found nothing.

I have sygate firewall free installed 

so the only option left for me is to format drive c and then re install windows.


What im asking is if i format drive c and then reinstall windows, will it effect my linux installation and the grub loader at start?

or if someone could fix my windows problem and save me the trouble of going through the format, i would be grateful :)

---

### Post by eternalnewbee on 2008-10-12
As far as I know windows won't even see Linux...

---

### Post by hyper_ch on 2008-10-12
by reinstalling windows it will overwrite grub and you'll have to restore it. There are tons and tons of howtos out there in order to achieve that. Either use supergrub disk or a desktop cd or ....

---

### Post by seshomaru samma on 2008-10-12
yes windows will overwrite grub
to restore grub - see my post [here ]("http://ubuntuforums.org/showpost.php?p=1769691&postcount=5")

---

### Post by bumanie on 2008-10-12
The above two posts are correct re what you need to do if you reinstall windows. 
Your windows problem sounds like a process is using most of the cpu on your system. When the computer starts going slowly have you looked at system monitor and tried to ascertain which process seems to be taking over the cpu? I recently fixed a windows machine behaving in a similar manner by finding which process was going haywire and removing it. It then worked again upon reinstall - assume its files had been corruted somehow (service pack 3 live update was the main suspect). It is worth looking at the system processes before going to a full reinstallation - I know it is difficult to get into system monitor when the computer is behaving this way, but with a bit of patience and perseverence, it's usually possible.

---

