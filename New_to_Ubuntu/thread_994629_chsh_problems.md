---
title: "chsh problems"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by ryan6 on 2008-11-26
new to linux

trying to change shells. my default shell is bash

when i run chsh and input password, it asks what shell i want. i input /bin/csh, just like it says in the etc/shells file, but then it tells me that ¨/bin/csh is an invalid shell¨ 

so i try some other ones. finally i get /bin/sh to work. but the shell is still bash. i pull up a new terminal, and its bash as well.

dont know what the problem is. i tried to upload the output of the commands i typed but dont know how to copy and paste it into the post. it wasnt in the FAQs.

o, one more problem, i cant type apostrophes, the apostrophe button makes me push it twice and all i get is a tic mark ´. any suggestions? thanks

---

### Post by RealPSL on 2008-11-27
Regarding you first question I do not believe that CSH is installed by default so that would explain your error. You can install it from "System > Administration > Synaptic Package Manager" by search for "csh" right clicking it and then choosing Mark for Installation and then clicking Apply. Or from the command prompt with ```
sudo apt-get install csh
```. Once you have the shell installed you can run the command ```
chsh -s /bin/csh
``` to install that as your default shell. You can check the change in /etc/passwd with ```
grep your_username_here /etc/passwd
``` you should see /bin/csh as the end of the line.

---

### Post by ryan6 on 2008-11-27
thanks for your reply, but i did what you said and it doesnt seem to be working. your were right about it not being installed before hand but i included the install command in the code after i had already installed it

it still does not change shells, and even the default is still bash when i pull up a new terminal

```

user@user:~$ sudo apt-get install csh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
csh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
user@user:~$ chsh -s /bin/csh
Password: 
user@user:~$ echo $SHELL
/bin/bash
user@user:~$ grep user /etc/passwd
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
polkituser:x:110:122:PolicyKit,,,:/var/run/PolicyKit:/bin/false
user:x:1000:1000:user,,,:/home/user:/bin/csh
user@user:~$ 

```

---

### Post by taurus on 2008-11-27
You need to log out and log back in again for the new shell to be in affect.

---

### Post by RealPSL on 2008-11-28
If you want C Shell immediately just type ```
csh
```or```
exec csh
```

---

### Post by ryan6 on 2008-11-29
awesome! it works. :D thanks for all the help

---

