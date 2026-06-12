---
title: "problem dont find package dkms"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by nawaz1 on 2012-08-20
nawaz@nawaz-desktop:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-headers-2.6.20-15-generic is not possible, it cannot be downloaded.
Reinstallation of build-essential is not possible, it cannot be downloaded.
E: Couldn't find package dkms


tell me what i do

---

### Post by matt_symes on 2012-08-20
Hi

> linux-headers-2.6.[COLOR=Red]**20**[/COLOR]-15

This is an old, old version you are trying to install.

What version of *buntu are you using ?

Where did you get it from ? How did you install it ?

Can you post the output from the terminal of...

```
cat /etc/lsb-release
```

Did you mean to install this version ? If you did then have you changed you sources file to point to an old repository ?

Kind regards

---

### Post by lukeiamyourfather on 2012-08-20
That kernel is from 2007 give or take. You're probably using a version of Ubuntu that is no longer supported so the repositories are no longer online. One option would be to install the package from the original install disc (if it exists there) or upgrade to a newer version of Ubuntu that is supported.

---

### Post by matt_symes on 2012-08-20
Hi

If you do want to use that old version, look for the repositories here...

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

If you don't know how to change the repos to point to these then i would suggest you have installed an old version by mistake and i would install a new version.

Kind regards

---

### Post by nawaz1 on 2012-08-20
i am using ubunti 12.04LTS  (precise)
tell me with command to install latest linux header plz

---

### Post by matt_symes on 2012-08-20
Hi

Open a terminal and type

```
cat /etc/lsb-release
```

and 

```
uname -r
```

Please post the output back here to get help.

Kind regards

---

### Post by NikTh on 2012-08-20
Hi , 
can you please provide the info that @Matt_symes asked ? 

```
cat /etc/lsb-release && uname -r
``` 
Thanks

---

### Post by nawaz1 on 2012-08-20
[FONT=&quot]nawazbaig@ubuntu:~$ cat /etc/lsb-release
[B]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"[/B]
[/FONT]


[FONT=&quot]nawazbaig@ubuntu:~$ [/FONT]uname -r[I][B][FONT=&quot] 
3.2.0-23-generic-pae[/FONT][/B][/I]


[I][B][FONT=&quot]plz help
[/FONT][/B][/I]

---

### Post by NikTh on 2012-08-20
> **nawaz1 said:**
> 
Reinstallation of linux-headers-2.6.20-15-generic is not possible, it cannot be downloaded.



> **nawaz1 said:**
> [FONT=&quot][B]
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"[/B]
[/FONT][FONT=&quot]nawazbaig@ubuntu:~$ [/FONT]uname -r[I][B][FONT=&quot] 
3.2.0-23-generic-pae[/FONT][/B][/I]


Hi , 
compared above posts , something is not right here. 
Please give the results of 
```
sudo apt-get update 
ls /etc/apt/sources.list.d/ 

```**Do not forget** to put the results inside ```
 tags. [noparse][code]the results here
```[/noparse] 
Thanks

---

### Post by nawaz1 on 2012-08-20
i dont have net connectivity !!! plz give me some way

---

### Post by matt_symes on 2012-08-21
Hi

> **nawaz1 said:**
> i dont have net connectivity !!! plz give me some way

Then how do you expect apt-get to install a new kernel and headers for you ? apt-get requires internet access to download a new kernel

As the last poster pointed out, something is not right with your system.

lsb-release is saying you have Precise installed - as you have said.

uname -r is suggesting you have booted into a very old kernel. 

Have you attempted to install your own kernel ? 

Can you select a new kernel from the grub menu when the system starts up ?

Is this a fresh install or an upgrade from a previous version ?

If you have no internet access from the PC, what are you using to post these messages ? I assume it's a different PC or a phone ?

Please answer the above questions with as much detail as possible.

The best option for you may be to download the kernel debs for Precise, copy them onto your precise install and install them manually.

You can find the kernels for precise here...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

You can download them onto a pen drive, and install them into precise from there. Select the best kernel for your architecture.

[I]However, to fix your system correctly, to ensure we do not break anything and to understand what is actually going on with the system you have installed, we could really do with some extra information to find out why you are in the situation you are in (it's unusual to say the least).

[/I]If you can find a  way, please post the output (as stated above) of...

```
grep -v ^# /etc/apt/sources.list
```

Please also post the output of...

```
ls -l /boot/vmlinuz*
```

That is a small L after ls.

Finally, please post the output of 

```
dpkg -l dkms
```

Once again, a small L after dpkg.

---

