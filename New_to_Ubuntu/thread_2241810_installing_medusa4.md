---
title: "installing medusa4"
date: 2014-08-28
forum: New to Ubuntu
---

### Post by Shawn_Hawkins on 2014-08-28
I am trying to install Medusa4, a cad program and it has been a while since I worked in Ubuntu. 
The installation guide says:
MEDUSA4 Personal 5.2.1 is a 32 bit application. It requires different 32 bit runtime libraries. On
a Linux - 64 bit - Operating System usually these libraries must be installed by the user.
For running MEDUSA4 Personal a csh or tcsh shell is required. If there is no csh or tcsh
shell installed, install it, for example, using the following command: ```
apt-get install csh
```

That goes fine but then it says:
For the installation you have to be superuser (root). Open a terminal and run the file
```
medusa4_v5_2_1_linux_personal.sh.
```

this is the return:
```
root@HAL:~# medusa4_v5_2_1_linux_personal.sh.
medusa4_v5_2_1_linux_personal.sh.: command not found
root@HAL:~# 
```

---

### Post by claracc on 2014-08-29
When you run the command:

```
medusa4_v5_2_1_linux_personal.sh.
```

The . at the end is not part of the program, so you have to run:

```
medusa4_v5_2_1_linux_personal.sh
```

---

