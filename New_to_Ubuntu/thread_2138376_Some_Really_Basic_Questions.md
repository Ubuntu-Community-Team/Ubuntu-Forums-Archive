---
title: "Some Really Basic Questions"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by JohnFeist on 2013-04-23
I've just installed 12.04 including the GUI.  I have to admit that I'm a bit frustrated in trying to use it.  I've been running an ancient version of Fedora for a number of years.  I decided to migrate to Ubuntu based on all the good press I've seen.  To start, I allowed the install to prompt me for various options to determine my keyboard.  It determined that I have a U.S. with international...  That would appear to be correct.  Unfortunately when I tried to write this note and tried to enter I've it comes up with the capital I and then ue with an accent over the u.  How do I reset my keyboard to the correct one (I'm in the U.S. with a standard IBM U.S. keyboard).

A real simple question, how do I put application icons on the desktop and not just the launcher?

Is there a usable "Getting Started" document available somewhere online?

When I did the install, I checked the LAMP option.  I'm not finding any of the components.  Is there one package I can download to install Apache, MySQL and PHP?  If I need to do a reinstall of Ubuntu as the easiest way to do that install, please tell me what I missed on the last go round.

Thanks for any help.

John

---

### Post by Iowan on 2013-04-23
If you click on Dash (the top  icon in the stack...) and type "keyboard" you *should* see an option for "Keyboard Layout". Click the "+" at the bottom left to add another keyboard layout. Mine is labeled **English(US)**

---

### Post by Bashing-om on 2013-04-23
JohnFeist; Hi Welcome to the forum.

For a good starter's guide to ubuntu 12.04. take a gander at this one:
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)
It has a section on server administration that may assist you.[INDENT=2]
my 2 pounds worth

[/INDENT]

---

### Post by papibe on 2013-04-23
> **JohnFeist said:**
> How do I reset my keyboard to the correct one (I'm in the U.S. with a standard IBM U.S. keyboard).
Open 'Keyboard Layout'. There you can check the current layout, and add/remove others.
> **JohnFeist said:**
> A real simple question, how do I put application icons on the desktop and not just the launcher?
Search for the program you want to create a shortcut to, then drag it to the desktop. It's very simple. Note the the dashboard works maximized by default so you may need to  'Unmaximaze' it.
> **JohnFeist said:**
> Is there a usable "Getting Started" document available somewhere online?
[Unity Guide]("http://ubuntu-za.org/sites/default/files/unity-5-10-0-final-pdf.pdf") on PDF (recommended).
[Online Ubuntu manual]("http://ubuntu-manual.org/").
Here's a well know [video]("http://ubuntuforums.org/showthread.php?t=2026920&highlight=unity+video") tutorial.
> **JohnFeist said:**
> Is there one package I can download to install Apache, MySQL and PHP?
Use 'tasksel' to instal the whole lamp stack. More details [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by JohnFeist on 2013-04-24
Thank you to everyone who replied.  I'm off and running.  All the suggestions were spot on.

---

### Post by JohnFeist on 2013-04-24
This is a follow on to the above.  Why is it that when I try to launch an application that I've put on the desktop I get a warning about an unsafe launcher, but when I open the app from the launcher or Dash, everything is fine?  

Does it matter that every app is owned by root (both owner and group)?  Can I/should I change that?  If so, how do I do that as i would have thought that since I am logged in and have admin rights I shouldn't have to?

Finally, how do I access as root (e.g. via su)?  When I did the install I was only asked for a password for my account which has admin privileges.

Thanks again for any assistance.

Best regards,

John

---

### Post by Bashing-om on 2013-04-24
JohnFeist;
In respect to starting an application from the desktop: what permissions are set on the iconic launcher ?
The great thing about linux (as ubuntu is a distro of) is the security model that it is based on. Permissions and access to system files is a great big deal !
If You create something as the administrative user, then it is owned by "root". (as an aside - working as "root" in your home directory can have devastating results, "root" is not needed to work most things in your own home)

See these tutorials for explanations and howtos:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm)

Remember, you only want to be "root" and use the privileges (sudo is suggested) only when absolutely required, and even then with discretion. [INDENT=2]
just try'n to help

[/INDENT]

---

### Post by col48 on 2013-04-24
JohnFeist

About privileges.....

The first user (set up while doing the installation) is only the administrator in the sense that his/hers is the password needed to do system-administrative tasks.  In normal use - ie running programs - no user has root privileges.

To do tasks which do require root privileges, a terminal command must be preceded by 'sudo', 'gksudo' or 'su' and the user will be re-prompted for the password (unless this has already been requested in the same terminal session in the last few minutes).

---

### Post by boron on 2013-04-24
thanks for the link to the guide - very useful :)

---

### Post by JohnFeist on 2013-04-25
Once again, thank you for all the information.

---

