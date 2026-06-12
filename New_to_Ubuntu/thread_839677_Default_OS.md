---
title: "Default OS"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-06-24
I'm dual booting Ubuntu and Windows XP, I'd like XP to be the default OS but I have no clue how to do that.

Thanks,
Ed

---

### Post by ibuclaw on 2008-06-24
Can you open up the menu.lst file and paste the entire contents of it on screen?
```
gedit /boot/grub/menu.lst
```

Regards
Iain

---

### Post by tribble222 on 2008-06-24
Backup your menu.lst:

$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

Then open your /boot/grub/menu.lst file

$ gksu gedit /boot/grub/menu.lst

and find where it says "## default num".  Below that, change the 0 in "default 0" to the appropriate menu entry you want to set to default.

---

### Post by ibuclaw on 2008-06-24
> **tribble222 said:**
> Backup your menu.lst:

$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bakup

Then open your /boot/grub/menu.lst file

$ gksu gedit /boot/grub/menu.lst

and find where it says "## default num".  Below that, change the 0 in "default 0" to the appropriate menu entry you want to set to default.
You are correct tribble222. But first, we must help the OP figure out which number it is :)

Off the top of my head, I think it is "**4**". But I'd prefer to check his current boot order, just incase.

Regards
Iain

---

### Post by WRDN on 2008-06-24
To change the default OS, you need to edit the menu.lst file.

In the terminal type:

```
sudo gedit /boot/grub/menu.lst
```

Now, find the line that says "Default 0", and change the number to the entry in the GRUB list that corresponds to Windows. Count from 0 and ensure you count "Other Operating Systems:" entry as a line.

For example, in the entries below:

Ubuntu 8.04
Ubuntu 8.04 (Recovery Mode)
Other Operating Systems:
Windows XP Home Edition

Windows is the 3rd entry, so I would change the entry in the menu.lst file to

```
Default 3
```

Also, you should uncomment 'updatedefaultentry' line and set it to true. To uncomment the line, just remove the # before it. It should be changed to:

```
updatedefaultentry=true
```

---

### Post by esteckis on 2008-06-24
If your a newbie like me, I use startup Manager and it is in the synaptic where you can add remove programs.

---

### Post by Pjotr123 on 2008-06-24
If you use startupmanager, it's a lot easier. Check this:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)

(number 1 )

---

### Post by Whatrymes on 2008-06-24
tahks! The startupmanager works like a charm. I'm a windows user until today, I'm use to the easy way. Thanks again.

Ed

---

