---
title: "Dear sudo, how can i type a password on my user account when it doesnt have one?"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by Crinkle on 2013-10-11
Anyone know what im supposed to type in terminal to make sudo do stuff, when the user account has no password?

---

### Post by sandyd on 2013-10-11
> **Crinkle said:**
> Anyone know what im supposed to type in terminal to make sudo do stuff, when the user account has no password?

Do you type a password to login, or do you have it set to autologin?

---

### Post by Crinkle on 2013-10-11
Theres no password for it AND it auto logs in when you click on that user. However terminal is all i can run, theres no launcher and i cant use terminal programs to repair it because it wants a non-existant password.

---

### Post by grahammechanical on 2013-10-11
Even if this user account had a password that user would still not be able to run commands with sudo if that user did not have administrator privileges. Are you the administrator? Do you have an account? If so, then you can run commands with sudo.

Regards.

---

### Post by Crinkle on 2013-10-11
Yes i have them all set as administrator accounts. Only main one has a password, and no, i cant run terminal commands on the other two, because it still asks for it. So what can i try now?

Also, why is ubuntu even setting up new accounts without a launcher/menu in the first place? This is a brand new install, nothings been tinkered with to mess anything up!

---

### Post by grahammechanical on 2013-10-11
Ah, so this is the real issue:

> [COLOR=#000000]why is ubuntu even setting up new accounts without a launcher/menu in the first place? [/COLOR]

Does the main account have a Launcher and top panel? Have the users of those accounts made any system modifications that may have caused this?

You will need to set administrator or root passwords for these accounts otherwise there is no point in setting those users as administrators.

You may be able to do this through Recovery mode. Depending on the version of Ubuntu that you are using we can get Recovery mode at the Grub menu (in 12.04) or under the Advanced Options sub-menu (in 13.04) of the Grub menu. At the Recovery menu select Network. That will set up a network connection using existing configuration scripts and also put the file system in read/write mode. When back at the Recovery menu select Root and there you can run commands. I do not know what commands you need.

Regards.

---

### Post by Crinkle on 2013-10-11
No the users have only just been setup,l first login, none of that stuff.

The main account has launcher and menu, which is why I am able to be using firefox.

Is there any way of not having passwords for those accounts at all? Even if it means removing all passwords everywhere. I know people would say thats a security issue but its not a big deal. I'm the only person who uses my computer.

---

### Post by 3rdalbum on 2013-10-12
> **Crinkle said:**
> No the users have only just been setup,l first login, none of that stuff.

The main account has launcher and menu, which is why I am able to be using firefox.

Is there any way of not having passwords for those accounts at all? Even if it means removing all passwords everywhere. I know people would say thats a security issue but its not a big deal. I'm the only person who uses my computer.

It's not just a security issue. Not having a password, or running permanently as root, will cause unexpected behaviour like crashes, programs not working or not working correctly, or even permissions problems. As a program developer I write my program assuming that the default security systems are in-place; it's a fairly safe assumption and I don't want to screw up my own security systems in order to test what happens when my program runs on your computer.

If you create a new user account with a password, that can 'sudo' but does not have 'root' access without it, you'll probably find the desktop will work fine.

---

### Post by newb85 on 2013-10-12
May I ask what the other user accounts are for, if you're the only one using the machine? 

Also, how did you go about setting up those user accounts?

---

### Post by Crinkle on 2013-10-12
Just added them in the user accounts section, no matter, I will settle for them being default users without passwords. The reason for three accounts is so i can have three customized  accounts with different types of program in it. Seeing as the sidebar is not very big (wish it could be at the bottom). One for games and internet stuff. One for music, audo and video production, and another for office related stuff. Got it solved now.

---

### Post by newb85 on 2013-10-13
First, different users won't have different types of programs.  Software packages you install on one user account (which is only possible on an account with sudo privileges and a password) will be installed for all users.

If you open User Accounts while logged in as a user with sudo privileges and a password, you should be able to add a password to any user's account.

If you mean you want different programs to be pinned to the Launcher depending on what you're using the machine for at the moment, I suggest you install a different (more flexible) Desktop Environment.  Cairo-Dock strikes me as one that might better suit your needs.  It uses Docks instead of the Launcher along the left.  You can create multiple docks, and have one for each of the uses you mentioned.  (Cairo-Dock can be run with the standard Unity interface, but it will probably be better for you if you log in to a non-Unity session.)

---

