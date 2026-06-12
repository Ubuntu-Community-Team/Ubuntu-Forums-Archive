---
title: "Won't start"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by P13808 on 2008-09-14
So I boot my computer(its dual booting ubuntu and windows XP).  Grub loads.  I select ubuntu(hd1,0 i believe) and it goes to the loading screen with the bar.  It completes loading.
Then the screen goes completely blank except for a small blinking line in the top left corner.  None of the keys on the keyboard do anything.  Nor does the mouse.  
This has happened before and I managed to revive it with the restore selection in grub.  Why is this and is there another way to fix it?

---

### Post by P13808 on 2008-09-14
[COLOR="White"].[/COLOR]

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi  P13808, you might want to boot with "nosplash" instead of "quiet splash".

( Press "e" in the grub menu to change boot options ) .

That way, you may see where it's hanging and retrieve useful error messages. Good luck ;)

---

### Post by P13808 on 2008-09-14
It seems like I can't edit grub lines(I edit it , but when i go back to the main menu, i look and see it never changed!)
I managed to just deletee the quiet command in the grub commands.  Nothing changed but somehow it worked.  Any idea how?

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Press e to edit the boot entry, e again to edit the line, replace quiet splash with nosplash, enter to validate, then b to boot.

---

