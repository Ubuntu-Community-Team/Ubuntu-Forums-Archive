---
title: "password management"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by DarinB on 2008-09-06
i was listening to a tech podcast and they mentioned password managers to keep all your online passwords straight...Does our world have an app for that????

---

### Post by tamoneya on 2008-09-06
i believe keepass has been ported to linux as keepassx.

[http://www.keepassx.org/](http://www.keepassx.org/)

it is also in the repos:
```
sudo apt-get install keepassx
```

---

### Post by DarinB on 2008-09-06
where can i find these?
keepassx:
 Depends: libqt4-core (>=4.3.2) but it is not installable
 Depends: libqt4-gui (>=4.3.2) but it is not installable

---

### Post by tamoneya on 2008-09-06
what repositories do you have enabled?
```
cat /etc/apt/sources.lst
```

---

### Post by ggaaron on 2008-09-06
There is KWallet, gnome-key-ring, and some apps (like firefox) have their own password managers build in.

---

### Post by DarinB on 2008-09-06
darin@darin-desktop:~$ sudo cat /etc/apt/sources.lst
cat: /etc/apt/sources.lst: No such file or directory

i thought i had a few enabled????????

---

### Post by DarinB on 2008-09-06
i thought it is better to use a third party app for that and i use gnome desktop not kde isn't kwallet for kde and i use swiftweasel for my p4

---

### Post by ggaaron on 2008-09-06
Gnome has it's keyring. This are all applications made for the same purpose, which is the best I don't know, but Gnome keyring and KWallet are both surely used by many people.

---

### Post by FakeOutdoorsman on 2008-09-06
I used to use Revelation when I was using Gnome, but then I moved to Openbox and didn't want to install any Gnome extras.  Now I just use encfs to encrypt a folder with various files, one of which is a text file with passwords.  Easy to use and also lightweight.

---

### Post by Red Rebel on 2010-12-25
Hello All, 

   Part of my migration to Ubuntu includes having a similar password manager like "1Password" for Mac OS X. "1Password" is an applet for Safari that will keep all passwords encrypted using 256 bit (AES) encryption. Not only will it keep  passwords, it will also log in to any user account automatically.  A very convenient feature, and a must have for a complete password manager. Simply click on its icon on Safari tool bar, and a drop down menu will show all available actions. "1Password has a strong password generator that can be configured to meet the password requirements of any site. Once password is generated for new or existing site,  simply click on the "fill" button, then it will ask to save login, or save new password to existing login.  This is the best all around password manager I have ever seen. If not already available, I would love to see something like it for the Ubuntu community since it prides itself on security. If anyone knows of a similar password manager, please reply to this post. Please take a look at the screenshots I have attached below. 



Thanks, 

RR

---

### Post by karthick87 on 2010-12-25
+1 on post #2

---

### Post by Elfy on 2010-12-25
Closed the 2 year old thread - things change - start another please.

---

