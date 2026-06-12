---
title: "Delete password?"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by bobmunro on 2013-01-23
what happens if you delete your password and then cannot change or do anything because you no longer have an original password? i'm on ububtu 12.10.

---

### Post by oldos2er on 2013-01-23
Post moved to its own thread. In the future please start your own thread rather than posting in someone else's.

---

### Post by coldcritter64 on 2013-01-23
> **bobmunro said:**
> what happens if you delete your password and then cannot change or do anything because you no longer have an original password? i'm on ububtu 12.10.
If Ubuntu is the only installation and you don't normally get a grub screen, hold down the **shift** key during boot up. If you have more than one OS installed grub will show and all you have to do is select the recovery option for your Ubuntu kernel. You don't need a password here, you get sent to a menu system.

In 12.04 console, to make the root drive writable I have had to run a fsck check on the drive (one of the menu options), the drive gets changed to writable when you do, this is necessary for the next step to fix the password. Not sure about 12.10 I am assuming it hasn't changed.

After the check completes return to the menu and select "Drop to root terminal", or worded very similar, the root terminal is what you need. In the root terminal enter the following commands,

```
ls /home
``` This is only to check the drive is mounted, you will see user home folders if it is. Not entirely necessary, I use it as a precaution for if the drive is not mounted the next command will fail.
```
passwd <insert-your-username>
``` You will be asked to enter a Unix password and confirm it by entering it again. If the 2 match OK your password will now be set on your user account. Cheers.

Edit: type "exit" then press "Enter" to get back to the menu from the root terminal. IIRC the top option will let you then continue a normal boot. Or type "reboot" and press "Enter" (don't include any quotation marks with any of the commands in this edit).

Edit 2: I just noticed your bean count and join date, welcome to the forums :)

---

### Post by Cheesemill on 2013-01-23
In recent versions of Ubuntu the root partition is mounted as read-only in recovery mode, so you will have to remount it with write permissions before you can change your password.

For a full walkthrough on how to reset your password with screenshots check out this page...
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

While you're there you should check out the rest of the site, it's an invaluable resource for users new to Ubuntu.

---

### Post by deadflowr on 2013-01-23
> **bobmunro said:**
> what happens if you delete your password and then cannot change or do anything because you no longer have an original password? i'm on ububtu 12.10.

Well then like cheesemill said, you'll need to follow the instructions in the link provided.
However, if by chance before deleting the password, you had set the user to autologin and disabled the lock setting in system settings, you could run Ubuntu without ever needing a password.
Though eventually, the bloat of updates, and the inability to change system functions, such as adding new programs, would cause headaches.

---

### Post by bobmunro on 2013-01-23
still got problems. after following the instructions and getting a "password successfully updated" i get a sign saying "authentification token manipulation error"  "password unchanged"

---

