---
title: "How to change username of PC?"
date: 2014-11-17
forum: New to Ubuntu
---

### Post by flaymond on 2014-11-17
This is a little  problem that i need help...i can't change the PC username...actually..i don't know how to.

When i open terminal...it will appear like this


user@user<computer name>


how can i change that...?

---

### Post by Lars Noodén on 2014-11-17
The fast way is to edit /etc/hostname to change the name of your machine.  

```

sudo nano -w /etc/hostname

```

Then you have to restart for the changes to take effect accross the whole system.

---

### Post by flaymond on 2014-11-17
its not working...i already reboot...here the picture


1. [http://minus.com/l5VHsJ6eOwczn](http://minus.com/l5VHsJ6eOwczn)

2.[http://minus.com/lboDd13Fb7I3M7](http://minus.com/lboDd13Fb7I3M7)

---

### Post by plucky on 2014-11-17
Create a new user in **System Settings > User Accounts**.

Make it an administration account.

When that is working correctly you can delete the original **user** account.

Or reinstall and put in a proper username when asked in the install dialogue.

Good Luck

---

### Post by Lars Noodén on 2014-11-17
I thought you were talking about the host name.  If you are talking about the shell prompt that Bash is showing you then you can edit the shell environment variable PS1.  See the [bash manual](http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html) section "PROMPTING" for all your options.

```

PS1='\u \w \t\$ '

```

If you want to make the prompt change permanent, the changes go in ~/.bashrc

---

### Post by flaymond on 2014-11-17
plucky, that was not i meant...i mean the (i don't know how to say) 'interprog-Aspire'. I need to change that...the username was ok (I actually set the name and put it 'user'), 

When you open the terminal

you will see on the screen...


<your account username> @ <Pc username>

---

### Post by flaymond on 2014-11-17
ohh..ok thanks for help..both of you...plucky..i can use your info in the future :D

---

