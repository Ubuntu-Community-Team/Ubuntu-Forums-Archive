---
title: "Password-Protected Software"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by pokemondawg2 on 2012-11-26
[FONT=Fixedsys]Okay, so every time I need to open a program that's password protected I type in my password. Okay, no big deal right? Well, after the password is entered, the program doesn't open. :confused: Any suggestions?[/FONT]

---

### Post by mlentink on 2012-11-26
My suggestion would be to be more specific. What "password-protected" software? (do you mean software that needs root-privileges?)

---

### Post by Mark Phelps on 2012-11-26
Programs are not generally password-protected; files are password-protected.

What you need to do is enter the proper password.

Need to know the type of file: document? archive? self-extracting archive?

---

### Post by pokemondawg2 on 2012-11-26
Yeah, like programs such as Software Sources that require root permissions.

---

### Post by mlentink on 2012-11-27
If you need to enter a password e.g. when changing software sources, you need to enter the password for the user you entered during setup (most likely your own account). This user belongs to the 'sudo' group, for which temporary root access is enabled. The root account as such is disabled in Ubuntu for security reasons.
If someone else installed the machine and entered their own credentials, your account most likely does not belong to the sudoers group, and you will have to ask them to either add your accoutn tom that group or make the change for you.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

