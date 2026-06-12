---
title: "Default root password?"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by suicideking on 2013-07-15
Noob question: :confused:
I recently installed Ubuntu 12.04 on my laptop. I can install things using the password for the user account I created. However, when at command prompt, if I type 'su' it asks for a password. I've tried the password I chose, it doesn't work. Is there a default password? If not, how do I gain root using 'su'.

---

### Post by sisco311 on 2013-07-15
The root account password is locked by default. Instead of su you can use sudo. Please see: [uhelp]community/RootSudo[/uhelp] for more details.

---

### Post by oldrocker99 on 2013-07-15
IF your laptop is a Chromebook, the default password is 'user.' The Ubuntu OS does not grant the user root access, even if your user type is Administrator, without that user's password. The command you need to use is sudo (Super User DO), which will ask for your password and grant you temporary root access.

To use su, for example:

sudo su

It will ask for a password, which is not echoed to the screen, no asterisks either. You then have a root shell. Be aware that the root shell in particular assumes that you know exactly what you're doing.

"With great power comes great responsibility."

---

### Post by Cheesemill on 2013-07-15
One thing to consider is that the preferred method to get a root shell in Ubuntu isn't to use 'su' or 'sudo su'.

If for some reason you do need to get to a root shell you should use the command...
```
sudo -i
```

---

### Post by suicideking on 2013-07-15
Thanks guys, that's what I was looking for! 

It's a Dell Laptop that I installed Ubuntu 12.04 on. 

I used to use Red Hat 6 probably 10+ years ago and used 'su'. Sounds like 'sudo' should be all that I need.

---

