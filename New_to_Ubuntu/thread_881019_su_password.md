---
title: "su password?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Carcharoth on 2008-08-05
very little experience here. 

we want to install Java, and have downloaded the RPM. Ubuntu 7.
the instructions say to log in as su (super user as I recall).
when I installed I gave it a password for the user account. to the best of my memory, I only ever used that password. I do not recall ever giving it a su password. 

the log in password works fine, so I am not just mis-typing.

what next?

---

### Post by kellemes on 2008-08-05
> **Carcharoth said:**
> very little experience here. 

we want to install Java, and have downloaded the RPM. Ubuntu 7.
the instructions say to log in as su (super user as I recall).
when I installed I gave it a password for the user account. to the best of my memory, I only ever used that password. I do not recall ever giving it a su password. 

the log in password works fine, so I am not just mis-typing.

what next?

su by default will ask for your root password, Ubuntu has no root account setup.
So use sudo instead, this will ask for your user account password to give you root privileges.

---

### Post by Qchan on 2008-08-05
> **Carcharoth said:**
> very little experience here. 

we want to install Java, and have downloaded the RPM. Ubuntu 7.
the instructions say to log in as su (super user as I recall).
when I installed I gave it a password for the user account. to the best of my memory, I only ever used that password. I do not recall ever giving it a su password. 

the log in password works fine, so I am not just mis-typing.

what next?

[b][color=darkred]
If you're running Ubuntu, you already have Java installed by default. If you're looking to install Java extras, you can click on Applications --> Add/Remove Programs. Do a search for Java and check the box that corresponds to what you want. After that, click Apply.
[/b][/color]

---

### Post by dew5 on 2008-08-05
you can in addition switch to root using

sudo -i

This is risky however as you may change settings.  You should be ok though.

So in Terminal(Applications>Accessories>Terminal) Type the aforementioned code.

dew5

---

### Post by gandaran on 2008-08-05
> we want to install Java, and have downloaded the RPM.

you can't install a RPM package in ubuntu, if you really prefer the sun package download the .bin package.

or make it easier for yourself, open you synaptic package manager, scroll down to **sun-java6-plugin** check-mark for install and click the apply button, this is all you have to do to get sun java installed.

---

### Post by dew5 on 2008-08-05
gandaran...

let him/her use the terminal.

Better in the long run

dew5

---

### Post by Carcharoth on 2008-08-05
in a word, "yes".
in two words, "thank you."

[I][COLOR="YellowGreen"]outside of a dog, a book is man's best friend.
inside of a dog, it's too dark to read.[/COLOR][/I]

---

### Post by Paqman on 2008-08-05
> **dew5 said:**
> 
let him/her use the terminal.

Better in the long run


Says who? People should use whatever they want.

---

### Post by Oldsoldier2003 on 2008-08-05
Rather than argue about whether or not people should or should not use the command line, let's spend our energies helping.

---

