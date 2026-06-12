---
title: "'nm-applet' keyring lock window at startup."
date: 2008-07-18
forum: New to Ubuntu
---

### Post by PHATSPEED7x on 2008-07-18
How do I get rid of this window at start up??? I just keep hitting the deny button.

---

### Post by Darkade on 2008-07-18
The nm-applet is the network manager applet. you probably are conected or have connected to a secure network, thus the keyring, where passwords can be saved and managed, is asking for the "general password" to let nm-applet to work.
OK, now what should you do, go to applications> accesories> passwords and encryption keys. look for the nm-applet athorization and select allow always. that should do the trick

---

### Post by PHATSPEED7x on 2008-07-21
So this window should only come up when tryingto connect to a network with a password?

---

### Post by Walter Melon on 2008-07-21
I'm having the same problem.  It shows up before it asks for the password to my secured wireless network and shows up after I connect to it.  I tried to find it using your method of Applications->Accessories->Passwords and Encryptions Keys, but there's nothing there.

---

### Post by jimmy the saint on 2008-07-22
The solution is here [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

---

### Post by Walter Melon on 2008-07-26
That link really didn't help that much but I started playing around with it and I fixed it.  If you go to System>Preferences>Encryption and Keyrings, you should see some keyrings there.  You could have one like I did or more.  

Anyway, I deleted the keyring "login" and tried to connect to my wireless network, it asked me for a new keyring password.  If you hit "deny", you'll have the same problem again and again. So put in a new password and it'll remember your wireless internet password.  You'll just have to enter it in once every time you boot up your computer.

---

### Post by sky_lover on 2009-03-19
Hi.
I have the same problem. Everytime I logon there's a pop up asking me for the keyring password. I tried my root password but it doesn't work...
I read your solutions to the problem but none of those worked for me, because everytime you said "go to applications-->..." I don't have the things you said to look for, like "passwords and encryption keys" or "encryption and keyrings"...
I have xubuntu (I didn't install it myself so I know very little about it... and yes I am a complete noob at this) so maybe that's why we have different options and I can't find the same things you can. Still there must be a way to make that thing disappear.
I also tried the solution posted in the link but if I can't connect to the internet I also can't install anything that needs to be downloaded...
Anyone can help me?? I really appreciate it :)

Take care

---

### Post by Black Trench Coat on 2009-04-08
Try this, worked for me:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by mulan on 2009-07-30
That last one worked for me too. As I use Xubuntu 9.04 libpam-gnome-keyring is allready installed so installing it again ain't really no option.

thanks

---

