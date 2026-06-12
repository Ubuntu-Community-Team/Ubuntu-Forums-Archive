---
title: "[SOLVED] Need to keep my disk partition but only be able to boot to windwos"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by tuffguy45 on 2008-09-26
So, they gave me a laptop to use at work and now they need to let one of the sales reps borrow it. So I need to make it so that grub doesn't come up and it just boots straight to Windows but be able to reverse it so that once they are done I can fix it so that I can get back to being able to select to either boot to linux/windows.

---

### Post by wolfen69 on 2008-09-26
boot to the windows cd as if you were going install xp. then choose recovery console and type ```
fixmbr
```choose the windows installation to fix (usually #1), and hit enter. just follow any prompt and reboot when done. then later on you can just restore grub to get the dual boot back.

---

### Post by Ocxic on 2008-09-26
or just set your windows partition as default in grub (menu.1st), and set the menu timer for like2-3 seconds

---

### Post by Ptero-4 on 2008-09-26
Or go to the /boot/grub/menu.lst file and change the number in the "default" line to the number of the entry pointing to wintendo (you do this by counting each kernel entry that doesn´t have the "recovery" mode in it, then counting one for the memory test entry and the one after that is the wintendo one, also be aware that it counts from 0), then uncomment the "hiddenmenu" line, then type sudo update-grub at the console. This makes grub hide the menu and autoboot wintendo. Then when they´re done with the computer you change the "default" line back to 0 and comment the "hiddenmenu" line (both in the /boot/grub/menu.lst file) and type sudo update-grub, this makes the menu show and autoboots into ubuntu.

---

### Post by -Zeus- on 2008-09-26
Ptero-4, your comment is pretty unintelligible.

tuffguy45, do this: press Alt+F2 and type ```
gkeu gedit /boot/grub/menu.lst
```

Where you see the line ```
#hiddenmenu
``` change it so it says ```
hiddenmenu
```

Also change the line ```
timeout    10
``` to ```
timeout   1
```

Also, find this line ```
default   0
``` and change it to what ever number windows is -1 (eg, if windows is the 5th entry in GRUB, set this to 4) ```
default   4
```

---

### Post by Ptero-4 on 2008-09-27
> **-Zeus- said:**
> Ptero-4, your comment is pretty unintelligible.

tuffguy45, do this: press Alt+F2 and type ```
gkeu gedit /boot/grub/menu.lst
```

Where you see the line ```
#hiddenmenu
``` change it so it says ```
hiddenmenu
```

Also change the line ```
timeout    10
``` to ```
timeout   1
```

Also, find this line ```
default   0
``` and change it to what ever number windows is -1 (eg, if windows is the 5th entry in GRUB, set this to 4) ```
default   4
```
Oops. was doing it by memory (not on a linux box ATM).

---

### Post by tuffguy45 on 2008-09-27
Just to avoid making another topic about it when It comes back to me, how do I get back the file in order to edit it since Its going to automatically boot to windows.

Edit: Nevermind, I figured it out because the fourth partition is actually my Dell Utility Partition. However, If I just press escape it goes back to the menu and I can get back there and change the default to do what I want it do.

---

