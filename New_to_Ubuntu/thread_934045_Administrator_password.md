---
title: "Administrator password"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by tarallo on 2008-09-30
Hi all,

just new on the forum and very very beginner on Linux. Here my problem:
after many efforts (and much time...) I finally installed Xubuntu on an old laptop (presario 1200 C566). No problem until I connected to the net and updated the system: since then admin password is no longer accepted. Now I have no idea how to do! I read that the pwd is stored not encrypted somewhere in a log file, but no clue how to recover it
Anybody can help...thank you

---

### Post by wilsong on 2008-09-30
I am sorry, I was under the impressions that you had set a Root password, and disabled sudo, and had forgotten your root password.  I was misunderstood, If your same password that you use to log in with, does not work when you try a sudo task, then there may be some other options, i dont have any good recommendations unfortunately.

---

### Post by tarallo on 2008-09-30
Wilsong,

the fact is that I do remeber the pwd (it is the one I log in) but after updateing the OS it is no more considered valid for administrative tasks

---

### Post by spiderbatdad on 2008-09-30
> **wilsong said:**
> If you cannot remember the root (su super user) password to your system, your best bet is probably reinstall. Sorry.

This is terrible advice, especially to someone who just declared how difficult the installation was. The password can easily be changed: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

But it sounds like you need to add yourself to the sudoers group: [http://www.pendrivelinux.com/2007/10/05/how-to-add-a-user-to-the-sudoers-list/](http://www.pendrivelinux.com/2007/10/05/how-to-add-a-user-to-the-sudoers-list/)

The root password should remain locked. Use sudo for administrative commands. To relock the root password: sudo passwd -l root

---

### Post by sisco311 on 2008-09-30
1.) Can you log in with the password?

Press Ctrl+Alt+F1 and try to log in to the virtual terminal.
Press Ctrl+Alt+F7 to go back to the x session.

2.) Is your user in the admin group?

Open a terminal and check it:
```
id *username*
```

3.) Did you enable the root account?

4.) Did you edit the sudoers file?

5.) Any error messages when you try to run an application as root?

From a terminal try:
```
gksu mousepad
```
and
```

sudo -s
```and post the error message(if any).

---

### Post by tarallo on 2008-10-01
Dear all,

I will try you multiple suggestions and keep you posted... cross my fingers.

Thank you

---

### Post by tarallo on 2008-10-06
Back with some results:

1) I changed the pwd of my account following the link [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword). After few changes I could understand that a pwd made of numbers only could possibly be thge issue... TBC Now it is ok (letter pwd)

2) I could enable the root account. No pb
3) I tried to add myself to the sudoers group as per [http://www.pendrivelinux.com/2007/10...-sudoers-list/](http://www.pendrivelinux.com/2007/10...-sudoers-list/).
Once I added my user to the list I cannot save and quit... ctrl+X does not work 

now I am stucked!!

---

