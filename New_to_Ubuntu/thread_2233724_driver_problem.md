---
title: "driver problem"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by alan32 on 2014-07-10
I am trying to install the TBS 6981 drivers I follow the instructions from the read me in the drivers section the drivers install then I change dir to the drivers dir to type in the following  [FONT=Ubuntu Mono][COLOR=#000000]# ./v4l/tbs-x86_r3.sh or any of the other v4l commands in the terminal it reports back permission denied can anyone help with this as I can go no further as the next step would be to make and install.[/COLOR][/FONT]

---

### Post by grahammechanical on 2014-07-10
Try putting sudo in front of that command and then entering your password when requested.

Regards.

---

### Post by alan32 on 2014-07-10
thanks will try that

---

### Post by Vladlenin5000 on 2014-07-10
Hi, welcome.

At the first glance I would say you need to precede the command by *sudo* just like in the following example:

```
sudo ./v4l/tbs-x86_r3.sh
```

... and you aren't supposed to run all of them, just the one for your system:
./v4l/tbs-x86_r3.sh -> Any recent Linux 32-bit distro (kernel 3.x)
./v4l/tbs-x86.sh -> for kernel 2.6.x (very old - no Ubuntu release using such kernel is currently supported)
./v4l/tbs-x86_64.sh -> 64-bit

PS - When asking for help is your job to provide the full informations regarding what steps you took so far, what is the hardware involved, Ubuntu version, etc. (any other pertinent information). It isn't my job to google search, download and open the driver/instructions just to answer your post.

---

### Post by alan32 on 2014-07-10
Thanks for the replies putting sudo in front worked great taking some time to get use to linux from win but hopefully I will get there

---

