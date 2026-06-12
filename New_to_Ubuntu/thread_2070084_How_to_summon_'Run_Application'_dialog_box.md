---
title: "How to summon 'Run Application' dialog box?"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Vladimir Pavic on 2012-10-12
Dear friends, 

 How to activate the 'Run application' dialog box in Ubuntu 12.04? In my case key combination Alt+F2 doesn't work, as it only turns wireless connection on and off. I tried to fiddle around in key shortcut settings to change the key combination, but I didn't succeed. I changed 'Show the run command prompt' to key combination Alt+Q (which worked very well in my 10.04.) Nope! What to do?
 

 Thanks.

---

### Post by vasa1 on 2012-10-12
I don't know how to help you but I would just like to suggest that you should be very careful when changing keyboard shortcuts.
Now that you're on Unity, quite a few shortcuts will have functions that they didn't have earlier.
Also, it's my fear (without proof) that updates may reset shortcuts.

---

### Post by stinkeye on 2012-10-12
Use the unity plugin in CCSM.
May also need to disable the key in the gnome compatibility plugin. (this the same setting as in keyboard shortcuts)

---

### Post by Vladimir Pavic on 2012-10-12
While appreciating Vasa1's warning, I dared to follow Stinkeye's suggestion - and I have succeeded! :) I changed the key combination to Super+Alt and it works! I hope this will help others with the same problem.

Thanks!

---

### Post by DuckHook on 2012-10-12
vasa1 is probably correct and the next upgrade may reset your shortcut. The underlying problem is likely due to the fact that your computer BIOS assigns the <Alt> + <F2> key combo to toggling your internal wireless card. Most laptops have a separate <Fn> key for this, but on some, the <Alt> key is used. Thus, the BIOS is intercepting your key combination as a system call and pre-empting your OS. This has the added disadvantage that other <Alt> + combos will dim your screen, eject your CD and even switch your primary monitor on you while you are working. You can usually disable this truly stupid "feature" in the BIOS and get back all of your <Alt> + <Fx> capabilities.

---

