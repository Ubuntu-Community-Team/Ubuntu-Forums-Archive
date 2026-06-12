---
title: "Screen Flickering"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by JohnsonGamingTV on 2012-09-21
I have a problem, i jut got ubuntu and the screen keeps flickering . how do i fix this?

---

### Post by Petro Dawg on 2012-09-21
What are the specifications of your computer (make, model)?  Is it a laptop, or desktop?

Also, what version of Ubuntu did you install?

---

### Post by JohnsonGamingTV on 2012-09-21
Im using a laptop, i dont know the exact specifications of it, but there are a few stickers on here that say "AMD Turion X2 64" and "NVIDIA" :3 lol and i dont know the version i got, i just went to the download page and clicked download :)

---

### Post by NikTh on 2012-09-21
Hi , 
please open a terminal (ctrl+alt+t keys combo) and copy-paste from here bellow commands , one at time. Press Enter after each command. One line = One command.
```
cat /etc/lsb-release 
uname -a  
lspci -nnk | grep -iA2 vga 
env | grep DESK
```Post back here the results of each command and put the results between the brackets.** [noparse]```
Here
```[/noparse]**

Thanks

---

### Post by JohnsonGamingTV on 2012-09-21
K I did the first two and it seems to have worked. the code i got for the first one was 
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

and the second one i got 
```
Linux ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by NikTh on 2012-09-22
I am waiting for the other two results. 

Above commands (I gave you) not do or changing anything , are just informational.

---

### Post by JohnsonGamingTV on 2012-09-22
the other 2 i got back 
```
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: nouveau
```

and 

```
DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity

```

---

### Post by NikTh on 2012-09-22
OK. 

now follow this .. 

From the terminal give bellow command 

```
sudo apt-get install --yes nvidia-current
``` 

it will ask you for your password. Write it carefully cuz nothing will appear (like not write anything) this is normal and press Enter. 

You will see a bunch of lines ... when installation finish , run this command in the same terminal 
```
sudo nvidia-xconfig
``` 

In the end , restart your PC and hopefully everything will be fine. 

Thanks

---

### Post by JohnsonGamingTV on 2012-09-22
OK so i did that and so far everything is fine, ill let you know if it starts acting up again but for now, thank you :)

---

### Post by NikTh on 2012-09-22
> **JohnsonGamingTV said:**
> OK so i did that and so far everything is fine, ill let you know **if it starts acting up again** but for now, thank you :)

Probably will not . 

If everything relating to this problem is OK , then come back and mark the thread as solved. 

Thanks

---

