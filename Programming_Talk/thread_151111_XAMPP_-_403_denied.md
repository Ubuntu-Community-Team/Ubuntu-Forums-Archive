---
title: "XAMPP - 403 denied"
date: 2006-03-27
forum: Programming Talk
---

### Post by Vinze on 2006-03-27
Hey, I installed XAMPP for Linux and it worked fine, but then one day all of a sudden it gave a 403 Forbidden error when I tried to view my pages... Surely I have done something stupid, but I have no idea what. I am in the root group which has read rights.

I reinstalled (read: re-unpacked) it but I still have the same problem, any ideas?

](*,)

---

### Post by invalid on 2006-03-27
I have not used XAMPP personally, so I don't know specifics.. I can only make a broad suggestion.

Check the file permissions to make sure they are not only readable by you, or the root user, but by others as well. Typically the permissions would be 644 on a standard file, and 755 on a standard directory. If either of these are different, it would result in a 403.

---

### Post by Vinze on 2006-03-28
OK... That's weird, I'd swear I'd tried that. Ah well, it works now, thanks :D

---

