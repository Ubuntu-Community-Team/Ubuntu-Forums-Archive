---
title: "how do i login to main root"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by perlsyntax on 2008-06-22
Before i login in on my gdm i wantt to know how i can get to the root desktop on Ubuntu so i can do some raw socket programming.

---

### Post by iaculallad on 2008-06-22
Login using the "Restore Mode" option on your GRUB boot menu.

---

### Post by dane_braddy666 on 2008-06-22
I don't believe ubuntu allows you to login as the root user - try using the sudo command from the terminal when launching programs / procedures to run them as root after logging as the normal user.

Hope this helps.:)

---

### Post by iaculallad on 2008-06-22
> **dane_braddy666 said:**
> I don't believe ubuntu allows you to login as the root user - try using the sudo command from the terminal when launching programs / procedures to run them as root after logging as the normal user.

Hope this helps.:)

By default, Ubuntu's root account is disabled. A way to "tinker" your system as in raw socket programming as root is to login using the "Restore Mode".

---

### Post by Oldsoldier2003 on 2008-06-22
> **iaculallad said:**
> By default, Ubuntu's root account is disabled. A way to "tinker" your system as in raw socket programming as root is to login using the "Restore Mode".

sudo -i works too, no need to reboot.

---

### Post by perlsyntax on 2008-06-22
You mmean when i am at grub i just push esc that how i get into it?

---

### Post by iaculallad on 2008-06-22
Yap, and you could also use the **sudo -i** option when you're logged to your GDM.

---

### Post by dane_braddy666 on 2008-06-22
> **Oldsoldier2003 said:**
> sudo -i works too, no need to reboot.

by running this command does the system then run everything as root even through GUI?

If so it could save ALOT of time when I have a tinker session.

And could I then create a new user... and have this command run at login - effectivly creating a root account?

---

### Post by DGortze380 on 2008-06-22
just enable your root account and work from a terminal. Contrary to popular belief, the world will not end if you enable root. Just select a secure password, don't share it with anyone, and remember, no matter what (root account or not), physical access=root access.

Just run "sudo passwd" for a terminal to set a root password.
"su" to switch user to root.
All without quotes ofcourse.

EDIT:
Just launch any programs you need form the terminal while logged in as root. The program should run as root.

---

### Post by Oldsoldier2003 on 2008-06-22
> **dane_braddy666 said:**
> by running this command does the system then run everything as root even through GUI?

If so it could save ALOT of time when I have a tinker session.

And could I then create a new user... and have this command run at login - effectivly creating a root account?

no to run a gui program with root priveleges you need to launch it using gksu

sudo -i just starts a "root shell" for that terminal session

---

### Post by dane_braddy666 on 2008-06-22
> **DGortze380 said:**
> just enable your root account and work from a terminal. Contrary to popular belief, the world will not end if you enable root. Just select a secure password, don't share it with anyone, and remember, no matter what (root account or not), physical access=root access.

Just run "sudo passwd" for a terminal to set a root password.
"su" to switch user to root.
All without quotes ofcourse.

EDIT:
Just launch any programs you need form the terminal while logged in as root. The program should run as root.

this is usually how i roll... however the the root access only lasts as long as that terminal session is open.... does sudo -i extend that beyond the terminal session?

** answered in previous post **

---

### Post by DGortze380 on 2008-06-22
> **dane_braddy666 said:**
> this is usually how i roll... however the the root acess only lasts as long as that terminal session is open.... does sudo -i extend that beyond the terminal session?

Not sure, I just shrink the terminal and work on another desktop so I don't accidentally close it. SAVE OFTEN!

---

### Post by perlsyntax on 2008-06-22
thanks that helps alot:):)

---

### Post by dane_braddy666 on 2008-06-22
> **DGortze380 said:**
> Not sure, I just shrink the terminal and work on another desktop so I don't accidentally close it. SAVE OFTEN!

very sound advice.

---

