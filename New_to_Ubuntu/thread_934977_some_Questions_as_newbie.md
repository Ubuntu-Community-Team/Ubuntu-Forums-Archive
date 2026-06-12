---
title: "some Questions as newbie"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Dacker on 2008-10-01
hello....
as a new user in linux i'm getting stuck in some commands and therefore i've some questions:

Q1: when i type ```
df -a
``` to return a list of all my mounted partitions one of the viewed result was 
```
securityfs                   0         0         0   -  /sys/kernel/security
```
 
 so what's the file being used for?  and why is being included into the kernel ?

Q2: when i try to shutdown the computer everything goes fine until the moment of offing the power, the pc will still on and the ubuntu logo will remain until i use the manually method :D .........

too much question still go around but i would be enough with that until now ........ :confused:

---

### Post by Bachstelze on 2008-10-01
1. SecurityFS is some internal kernel infrastructure you most likely don't want to worry about if you're new. Google is your friend if you really want details.

2. Poor ACPI, blame Intel.

---

### Post by SupaSonic on 2008-10-01
I always use this
```
df -h
```

---

### Post by Zill on 2008-10-01
> **Dacker said:**
> ...Q2: when i try to shutdown the computer everything goes fine until the moment of offing the power, the pc will still on and the ubuntu logo will remain until i use the manually method...
If it is an old PC try adding line "apm power_off=1" to /etc/modules eg.
```
sudo nano /etc/modules
```
Add line to end
```
apm power_off=1
```
Hit ctrl-o to save then ctrl-x to exit nano text editor.

Reboot.

---

### Post by Sycron on 2008-10-01
Do you have snd-hda-intel ?

---

### Post by Dacker on 2008-10-01
> **SupaSonic said:**
> I always use this
```
df -h
```

```
df -h  &   df -a
``` are two different things ```
df -a
``` is to show the hidden file, actually when you add -a falg to any viewer command is going to show what's the hidden like ```
ls -a
``` 
but the ```
df -h
``` is a way of sorting....:o   

thank you for your replying .....

---

### Post by Dacker on 2008-10-01
```
apm power_off=1
```

i've tried this cmd before and repeat it once again but nothing has changed....

---

### Post by Dacker on 2008-10-01
> **Sycron said:**
> Do you have snd-hda-intel ?


hey bro try to simplify more ....

---

### Post by Dacker on 2008-10-01
guys around here nobody can solve the power off problem .......


:confused:

---

### Post by Nxion on 2008-10-01
> **Dacker said:**
> guys around here nobody can solve the power off problem .......


:confused:

Bu chance is it a Dell Optiplex 745? I have that model at work and I have the same issue. The strange thing is that it only seems to be with Hardy Heron (8.04), if I use Feisty Fawn (7.04) all is fine. Strange.....

---

### Post by Dacker on 2008-10-01
the thing that make it more stranger was working fine with windows but once i installed ubuntu the thing has occurred ....... :confused:  i attempt to change in the modules of the power's value but.... puzzled over](*,)

---

### Post by Nxion on 2008-10-07
> **Dacker said:**
> guys around here nobody can solve the power off problem .......


:confused:


Ok, after alot of digging I found this. After I modified /etc/init.d/halt and /etc/init.d/reboot scripts it worked. I actually had to remove the "i" flag from both scripts and TADA!!. No more issues, my machine shutdown ad restarted and logged of fine with out issue. Let me know if you need more info on how to accomplish this.

Nx

---

### Post by HellNoire on 2008-10-07
I'd be hoping for a little more info on how to solve this power off issue.

---

### Post by Nxion on 2008-10-07
> **HellNoire said:**
> I'd be hoping for a little more info on how to solve this power off issue.

Once I am home tonight I will walk you threw on how to fix it. I would do it now but I am not in front of my machine.

---

### Post by Nxion on 2008-10-14
> **HellNoire said:**
> I'd be hoping for a little more info on how to solve this power off issue.

**Make sure you follow this EXACTLY as it says. these files are key to your system.**

OK, lets start by editing "/etc/init.d/halt" first.

Open a terminal and type this:

```
sudo gedit /etc/init.d/halt
```

Once it is open look for this lines I have highlighted in [COLOR=Red]red[/COLOR]:

> 
[COLOR=Red]    log_action_msg "Will now halt"
    sleep 1
    halt -d -f -i $poweroff $hddown[/COLOR][COLOR=Red][/COLOR]

In gedit, it will give you the number of all the lines in the file. The above snippet is on lines 55, 56 and 57. OK, now what you need to do is remove the "i" flag. so delete it from the file so now lines 55,56 and 57 should look like this:

> [COLOR=Red]
    log_action_msg "Will now halt"
    sleep 1
    halt -d -f $poweroff $hddown[/COLOR][COLOR=Red][/COLOR]

Make sure there is no extere spaces or the script might not work and we might have issues when the machine reboots.

After you edit the file make sure to save and close. Now we move on the the other file.

OK, now lets edit "/etc/init.d/reboot".

Open a terminal and type this 

```
sudo gedit /etc/init.d/reboot
```

Once it is open look for the linnes I have highlighted in [COLOR=Green]green[/COLOR]:

> [COLOR=Green]# Message should end with a newline since kFreeBSD may
    # print more stuff (see #323749)
    log_action_msg "Will now restart"
    reboot -d -f -i[/COLOR]

In gedit, it will give you the number of all the lines in the file. The above snippet is on lines 18, 19, 20 and 21.. OK, now what you need to do is remove the "i" flag again. So delete it from the file so now lines 18, 19, 20 and 21 should look like this:

> [COLOR=Green]# Message should end with a newline since kFreeBSD may
    # print more stuff (see #323749)
    log_action_msg "Will now restart"
    reboot -d -f[/COLOR]

Again.... Make sure there is no extere spaces or the script might not work and we might have issues when the machine reboots.

After you edit the file make sure to save and close. 

OK, now here comes the ultimate test, reboot and see what happens. It should now reboot and shutdown without issue.


Hope this helps.

---

