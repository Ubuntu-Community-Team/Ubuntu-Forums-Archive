---
title: "login failed password"
date: 2011-08-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by BigCityCat on 2011-08-27
I used the alternate install cd. I know my password but it won't recognize my password when I try to login. I know the password is correct. Not sure how to fix. Tried it with caps as well.

---

### Post by ranch hand on 2011-08-27
If you have a second, stable OS on the box (good idea) you can chroot in and run;
```

passwd <username>

```
this will bring up a prompt asking for the new password for your user (or claim the user does not exist).

Type in the password.  You will need to repeat it.

Reboot, should work.

If no second OS you will have to use a Live CD to do the job.

---

### Post by Harry33 on 2011-08-28
No need to chroot.
Just reboot the computer and press shift before grub starts to open the grub menu.
Then choose recovery mode.
From the menu, choose drop down to shell (root).
Then enter this code:
```
passwd x
```
where x is your acoount name.
Then you can enter a new password for that account name.

---

### Post by brunolabs on 2011-09-01
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/838936]("https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/838936")

---

### Post by BigCityCat on 2011-09-01
Thanks guys.

---

### Post by ihaq2 on 2011-10-03
ok, I have a problem with my login password. My grub menu doesn't appear at all, so I dont have access to terminal. I tried changing the password via live cd but that did't work as well. Please, help, because I need some info in the system ASAP. Thank you!

---

### Post by cariboo on 2011-10-03
Hold down the shift key during post and until the grub menu shows up.

BTW, because this thread is marked as solved, many people will bypass the thread, and not answer your question. It would have been better if you started a new thread, keep this in mind for the next time you have a question.

---

