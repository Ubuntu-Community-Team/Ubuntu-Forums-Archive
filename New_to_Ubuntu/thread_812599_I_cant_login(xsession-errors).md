---
title: "I cant login(xsession-errors)"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by library on 2008-05-30
Dear all,
I have another problem of login on ubuntu 7.04 desktop. When I try to login getting the following error message
*Your session only lasted less than 10 seconds.If you have not logged out yourself,this could mean thatthere is some installation problem or that you may be out of diskspace.try logging in with one of the failsafe sessions to see if you can fix this problme*

I have tried to go to select session and selected failsafe  terminal and it sends to me to command terminal but I dont know what to do.
thank you for your help
lib

---

### Post by iaculallad on 2008-05-30
Try pressing Ctrl+Alt+F1 to drop to command line login then use your username and  password to authenticate.

At the CLI: Issue the following commands.

```
sudo chown username:username /home/username/.ICEauthority
```

```
sudo chmod 600 /home/username/.ICEauthority
```

```
sudo /etc/init.d/gdm restart
```

---

