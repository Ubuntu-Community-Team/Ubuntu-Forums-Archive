---
title: "root password"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by deell2 on 2008-04-23
Hi

Thanks to everybody who responded to my post this morning I have managed to install ubuntu on my laptop BUT where did I/ do I specify the root password ?  I cannot at the moment log on as root and don't remember being asked for the password during installation - or did I miss it ?

---

### Post by energy. on 2008-04-23
there isn't a bona fide root account in ubuntu.  you issue commands that need root privileges by using sudo

---

### Post by Perfect Storm on 2008-04-23
Ubuntu don't have root enable be default. Instead if you want to do/change stuff that require to change system file(s), you you **sudo** infront of that command you want to execute.

---

### Post by ace007 on 2008-04-23
you really dont want to log in as root.  You should have created a profile and been prompted for a password during the install.  That profile you created has admin priveledges. but is not the root.

If you log in as root you will never be asked for a password, and if you goof up something there is no undo button.  Likewise your computer is more secure if you are not logged in as root.

Use the sudo command at the terminal to execute your commands as a temporary root.  This is the desired way of doing business.

Why do you want root privileges? If it if for editing/installing things, just place sudo before any command.  Or if you want to run a GUI as root (not recommended) you can place gksudo in front of the command.

---

### Post by Martje_001 on 2008-04-23
Read all about it here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by jdm2 on 2008-04-23
Everybody here is right.  You need to use sudo instead of logging in as root.  I have made big mistake before while I was logged in as root.  It is better not to be logged in as root, but if you must first you need to enable and set the password for it.  

From the terminal:  sudo passwd root  Then enter the password
or
gui:  go to the user and groups area under the administration panel.  find root in there and enter in a new password.  

You have just enable root and gave it a password.  Now if you want to log into it you need to go to the login window under the administration panel and under security there will be a check box that will allow you to login as root.  All you have to do is check that and save the changes.  Now you are able to log in as root.  

Note:  I don't advise using root.  You should use sudo if you need to do something for administratoring the computer.  I know there is times when you will need root, but don't use the root account only if you have to.  It is just like windows computers.  The everyday user uses the admin or computer admin account and then the computer crashes because they don't know what they are doing.  So use sudo instead of root.   

I hope this helps.  Good luck

---

