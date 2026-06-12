---
title: "mounting /dev/mapper/ubuntu--vg-root on /root failed: Invalid argument"
date: 2014-12-30
forum: New to Ubuntu
---

### Post by joanna6 on 2014-12-30
After fine lunch I wanted to work a little bit on my Ubuntu laptop ... and it didn't boot :(

Just before it stops, the output is:

mount: mounting /dev/mapper/ubuntu--vg-root on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ... done
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on root/sys failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg.

I tried Boot-Repair with recommended settings and it didn't help. The results are here: [http://paste.ubuntu.com/9647987/](http://paste.ubuntu.com/9647987/) 
Laptop is: [FONT=arial]Acer[/FONT][FONT=arial] V5-561G[/FONT]

I would appreciate any help or tip - thanks!

---

### Post by joanna6 on 2014-12-30
Solved. DryChilli's post helped.

[http://ubuntuforums.org/archive/index.php/t-1200023.html](http://ubuntuforums.org/archive/index.php/t-1200023.html)

---

