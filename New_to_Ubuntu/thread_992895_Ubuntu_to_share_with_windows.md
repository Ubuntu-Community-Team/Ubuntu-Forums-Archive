---
title: "Ubuntu to share with windows"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by mike_new_boy on 2008-11-25
I have ubuntu 8.10 and am having difficulty accessing a share from a windows XP box. It works if I allow guests but what I cant do is create one that requires a user name and password.
I have created a samba user and a ubuntu user with the same user name and password. Then logging on as that user and created the share. The share is visible from the windows box, trying to open it produces the windows “Connect to server” dialog box but what username and password do use? The ubuntu / samba one does not work!

---

### Post by go_beep_yourself on 2008-11-25
An alternate solution would be to use winscp in Windows and openssh-server in Linux to connect with username and passwords of your Ubuntu user accounts.

---

### Post by mike_new_boy on 2008-11-25
> **go_beep_yourself said:**
> An alternate solution would be to use winscp in Windows and openssh-server in Linux to connect with username and passwords of your Ubuntu user accounts.

Would winscp work? What I want to do is map a network drive from the windows machines. I am planning two, (P) where everyone can access in read only and I think I have done that. The other (U) is to be where users keep the personal files and I do not want these to be seen by other users of the network, I had planned access to this to require a user name and password.

---

### Post by superprash2003 on 2008-11-25
enter the windows username and password

---

### Post by mike_new_boy on 2008-11-25
Thanks
My users do not have a password for windows but when I made the ubuntu / samba / and windows usernames all the same it connected fine when in windows as that user (didnt even prompt for username and password) and that share was not accessible to anyone not logged in as that use

---

### Post by superprash2003 on 2008-11-28
its always better to use advanced file sharing in windows [http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx)

---

