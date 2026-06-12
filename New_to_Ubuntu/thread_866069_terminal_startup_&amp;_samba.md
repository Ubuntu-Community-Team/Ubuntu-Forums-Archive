---
title: "terminal startup &amp; samba"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-21
2 questions

1. how do I make the Ubuntu start up in the terminal instead of the gnome?

2. when I connect a windows pc to the Ubuntu, the first time it asks for a login/pw then after that, it auto logins but I want to change users, how do I change users?

---

### Post by barnabus on 2008-07-21
system -> administration -> services
enter your password
Uncheck Graphical Login Manager 

Not sure about question 2 sorry

---

### Post by WRDN on 2008-07-21
For the first question, select System > Administration > Services, click unlock and enter your password. Then, uncheck the box for "Graphical Login Manager (gdm)"

---

### Post by era86 on 2008-07-21
1. I believe if you go into sys->admin->services, you can uncheck GDM to get this effect.  To start the GUI, you can type startx.

---

### Post by waterrr on 2008-07-21
how do I get the gui back when I want it?

---

### Post by barnabus on 2008-07-21
type startx

---

### Post by bodhi.zazen on 2008-07-21
For samba my guess would be one of three problems.

1. Unmount the samba share before you switch users.

2. If you are connecting through the gui interface be sure to user the forget password immediately.

3. Is your samba share in /etc/fstab and are you using a credentials file ?

---

### Post by waterrr on 2008-07-21
when I typed startx then I did ctrl+alt+f7 to go to terminal, my terminal line disappeared, reasons?

---

### Post by waterrr on 2008-07-21
as for q #2, just discon the mapped drive

---

### Post by waterrr on 2008-07-21
new question haha

how do i give the users i added onto the samba administration privleges? (such as uploading files onto the shared folder)

---

### Post by bodhi.zazen on 2008-07-21
> **waterrr said:**
> new question haha

how do i give the users i added onto the samba administration privleges? (such as uploading files onto the shared folder)

You have to configure the samba share. Configuration depends on if the "samba" server is a windows or linux box, lol.

---

### Post by waterrr on 2008-07-21
the samba server is on a linux box

where do I go to configure samba share?

---

### Post by bodhi.zazen on 2008-07-21
Take a look at this page / section :

[https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration)

---

