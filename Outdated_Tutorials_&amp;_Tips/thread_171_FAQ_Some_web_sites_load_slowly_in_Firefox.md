---
title: "FAQ: Some web sites load slowly in Firefox"
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
> The latest version of Mozilla includes support for "IPv6" a new form of addressing things on the internet.

The problem is: Mozilla tries to use IPv6 before it uses IPv4 (IPv4 is the old version). When your Internet connection doesn't support IPv6, Mozilla fails to connect on the first try. In the current version of Mozilla, you can't change this, because of a bug.

To fix this issue follow these steps:
sudo nano /etc/modutils/aliases

Look for this line:
# alias net-pf-10 off # IPv6

Change the line to: (remove the #)
alias net-pf-10 off # IPv6

Then run: sudo update-modules

---

### Post by triad169 on 2004-10-16
FYI there is a BUG that even when you do this step IPv6 still loads up.  A temporary fix was given to me by Fabio on the mailing list:

> 
modutils is used only by 2.4 kernels. mostlikely you have a 2.6 kernel
and you using module-init-tools that uses /etc/modprobe.d/ as
configuration directory.

You need to edit _also_ /etc/modprobe.d/aliases too and run update-modules.

Check that /etc/modules.conf is update properly.

This is the standard procedure. but that's not enough.

Apparently there is another bug somewhere between the kernel and
module-init-tools that even if you ban ipv6 will still allow some
applications to trigger the load of the module.
Personally i don't remember if this is the normal behavior or not.

ntpdate is the first one in the boot process that shows this behavior,
but there are others.

so a simple workaround is to rename or remove the ipv6 module from
/lib/modules/`uname -r`/kernel/net/ipv6/ipv6.ko.
FYI: This will spawn an extra error message during the boot process.

For reference [https://bugzilla.ubuntu.com/show_bug.cgi?id=2443](https://bugzilla.ubuntu.com/show_bug.cgi?id=2443)

Fabio

Triad

---

### Post by elwis on 2004-10-24
[QUOTE=triad169]FYI there is a BUG that even when you do this step IPv6 still loads up.  A temporary fix was given to me by Fabio on the mailing list:



Triad[/QUOTE]
 Is this fix the one to do? Cause my web are terrible slow... Terrible indeed :(

---

### Post by jdong on 2004-10-24
[QUOTE=triad169]FYI there is a BUG that even when you do this step IPv6 still loads up.  A temporary fix was given to me by Fabio on the mailing list:



Triad[/QUOTE]
I can confirm that you must also change the alias entry in /etc/modprobe.d. However, changing those two files removed ipv6 for me. (To check, do an ifconfig and see if ipv6 addresses have been assigned. If no, then your slowness is due to something else!)

---

### Post by elwis on 2004-10-26
[QUOTE=jdong]I can confirm that you must also change the alias entry in /etc/modprobe.d. However, changing those two files removed ipv6 for me. (To check, do an ifconfig and see if ipv6 addresses have been assigned. If no, then your slowness is due to something else!)[/QUOTE]
 What am I supposed to change in /etc/modprobe.d/aliases?
Should I comment out the ipv6 line or what?

---

### Post by sala on 2004-10-26
sama here. i do not understand witch changes i should made and witch not???
this site refreshing make me sick... i allmost tryed to find my windows xp cd the other day 8-[

---

### Post by elwis on 2004-10-26
[QUOTE=sala]sama here. i do not understand witch changes i should made and witch not???
this site refreshing make me sick... i allmost tryed to find my windows xp cd the other day 8-[[/QUOTE]

Oh NO, don't do that to yourself! Remember, you could always find another distro.. but don't throw yourself in the hands of those hooligans from Redmond, they will consume your soul you know ;)

---

### Post by flygmaskin on 2004-10-26
[QUOTE=elwis]Oh NO, don't do that to yourself! Remember, you could always find another distro.. but don't throw yourself in the hands of those hooligans from Redmond, they will consume your soul you know ;)[/QUOTE]
 Is there some way to do this without rebooting. It hate rebooting :)

---

### Post by jdong on 2004-10-26
[QUOTE=flygmaskin]Is there some way to do this without rebooting. It hate rebooting :)[/QUOTE]

To answer 2 questions:

1. in modprobe.d, alias net-pf-10 to off. dont' comment the line, that doesn't help!

2. Yes. use ifconfig to bring all interfaces down, rmmod ipv6, then bring all your interfaces up again. To me, that's more trouble than hitting CTRL ALT DEL.

---

### Post by ffderrick on 2004-11-08
Thanks for all the great help in this thread.
I followed your advice and it fixed my slow internet problem.
In summary:

```
sudo nano /etc/modutils/aliases
```
      Change the line to: (remove the #)
      alias net-pf-10 off # IPv6

```

sudo nano /etc/modprobe.d/aliases
```
      Comment out
      #alias net-pf-10 ipv6

```

sudo update-modules
``` 

```
cd /lib/modules/2*/kernel/net/ipv6
sudo mv ipv6.ko hide-ipv6.ko
```

Last I had to reboot.

Thanks again for all the help.
I'm not sure all these steps are necessary, but it fixed my problem.
I suppose when the bug is fixed in mozilla, we can safely return these settings to normal.

---

### Post by zenwhen on 2004-11-09
This is the solution I used:

[IMG]http://zenhardwhere.com/images/problem-solved.png[/IMG]

---

### Post by digital_k on 2004-11-13
I tried this, and I have noticed a dramatic speed increase. Thank you! :grin:

---

### Post by CardinalSin on 2004-11-16
Hi

The "about:config" made my internet surfing 100 times faster. Thank you very much for the hint.  =D>

---

### Post by FLeiXiuS on 2004-11-17
zenwhen thats a really good way to use it also.  It'll only improve firefox, where as disabling the module its self will be system wide.

---

