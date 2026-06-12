---
title: "Plymouth not showing at all"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by yakinikku on 2012-06-09
Hi guys,

I just setup another dual boot system manually yesterday (no WUBI).  The system boots fine and what not, but after the installation the ubuntu logo on the plymouth screen was in VGA resolution.  So I googled around and found that the solution that worked for 10.04 was still a viable solution, with the addition of the setting the handoff to 7 (I can't remember the exact terminology at the moment).  Anyhow, after I did that, plymouth does not show at all anymore.  Now all I get is a really verbose boot screen.  Any ideas how I can fix this?  TIA

---

### Post by matt_symes on 2012-06-09
Hi

Did you edit the grub kernel command line ?

Open a terminal and type

```
cat /proc/cmdline
```

Post the output back here. Which version of Ubuntu did you install ?

Kind regards

---

### Post by yakinikku on 2012-06-09
> **matt_symes said:**
> Hi

Did you edit the grub kernel command line ?

Open a terminal and type

```
cat /proc/cmdline
```

Post the output back here. Which version of Ubuntu did you install ?

Kind regards


Thanks for such a quick response!  It seems that in my rush to post my original post I left out some critical information.  I installed 12.04 (x86).  My computer has an nvidia video card, and I am guessing this is the source of my problem, as I have done this tons of times before and never had an issue.  I did not edit the grub kernel.  Here is the output you requested

```
BOOT_IMAGE=/vmlinuz-3.2.0-24-generic-pae root=UUID=d4ae5a81-a733-4a75-9ecf-b855c0502f5f ro

```

---

### Post by matt_symes on 2012-06-09
Hi

You need to add quiet and splash back to the grub command line.

This is mine (Your kernel is different).

```
matthew@matthew-Aspire-7540 ~ % cat /proc/cmdline                                 
BOOT_IMAGE=/boot/vmlinuz-3.5.0-030500rc1-generic root=UUID=f68fa4b1-d246-4fe8-a01b-9b7e1420b5ad ro quiet splash vt.handoff=7
matthew@matthew-Aspire-7540 ~ %
```

That will get you back to where you were.

Edit the file

```
/etc/default/grub
``` 

and re-add to this section.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Then 

```
sudo update-grub
```

Kind regards

---

### Post by yakinikku on 2012-06-09
> **matt_symes said:**
> Hi

You need to add quiet and splash back to the grub command line.

This is mine (Your kernel is different).

```
matthew@matthew-Aspire-7540 ~ % cat /proc/cmdline                                 
BOOT_IMAGE=/boot/vmlinuz-3.5.0-030500rc1-generic root=UUID=f68fa4b1-d246-4fe8-a01b-9b7e1420b5ad ro quiet splash vt.handoff=7
matthew@matthew-Aspire-7540 ~ %
```

That will get you back to where you were.

Edit the file

```
/etc/default/grub
``` 

and re-add to this section.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Then 

```
sudo update-grub
```

Kind regards

I have modified my /etc/default/grub file and updated the grub config, however if I run the cat /proc/cmdline command, I see no change.  I restarted the computer to double check and it is still in super verbose (that's what I am calling it since I don't know what the right term is ;() mode.  Thoughts?

EDIT: I should mention that I am using BURG.  Although I have not had this same problem occur on other systems with the same setup, I think that information might be important.

---

### Post by matt_symes on 2012-06-09
Hi

Can you detail exactly what you did and post links to the tutorials you followed to get where you are now.

I have no experience of BURG so i may not be the best help.

Just to make sure the other settings took can you post the outout of

```
grep GRUB_CMDLINE_LINUX_DEFAULT /etc/default/grub
```

The above is case sensitive.

Kind regards

---

### Post by yakinikku on 2012-06-09
> **matt_symes said:**
> Hi

Can you detail exactly what you did and post links to the tutorials you followed to get where you are now.

I have no experience of BURG so i may not be the best help.

Kind regards

Sure, the link I followed was: 

[http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/](http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/)


This used a script to run all the commands to supposedly fix the issue.  However, they did not work.  After running that script plymouth stopped working.  Prior to that I was getting VGA resolution with it.

I am also getting random GUI crashes.  Basically the screen goes black and I am brought back to the login screen.

Thoughts?

EDIT: I think I am just going to wipe the ubuntu partition and start over.  I keep getting an error box that says "system program problem detected" as well.  Something is clearly wrong.

---

### Post by matt_symes on 2012-06-09
Hi

The script does a couple of things.

It changes the files /etc/default/grub and /etc/grub.d/10_linux and, potentially, /etc/initramfs-tools/modules and /etc/initramfs-tools/conf.d/splash. It then rebuilds the initramfs file to load a framebuffer.

Lets check your files first. Please post the output of

```
cat /etc/default/grub
```

and

```
cat /etc/grub.d/10_linux
```

and 

```
cat /etc/initramfs-tools/modules
```

and finally

```
cat /etc/initramfs-tools/conf.d/splash
```

Reading through the script, iIt looks like you may have to type

```
sudo update-burg
```

as well as 

```
sudo update-grub
```

Kind regards

---

### Post by yakinikku on 2012-06-09
> **matt_symes said:**
> Hi

The script does a couple of things.

It changes the files /etc/default/grub and /etc/grub.d/10_linux and, potentially, /etc/initramfs-tools/modules and /etc/initramfs-tools/conf.d/splash. It then rebuilds the initramfs file to load a framebuffer.

Lets check your files first. Please post the output of

```
cat /etc/default/grub
```

and

```
cat /etc/grub.d/10_linux
```

and 

```
cat /etc/initramfs-tools/modules
```

and finally

```
cat /etc/initramfs-tools/conf.d/splash
```

Reading through the script, iIt looks like you may have to type

```
sudo update-burg
```

as well as 

```
sudo update-grub
```

Kind regards

I read the comments and it looked like he updated the script to work with BURG.  

I actually just deleted the linux partition :O.  I am going to start over and see if I get the same errors.  I know that was the hyper destructive way to go about it, but I can't remember everything I did.  That was my fault, this time I will trace my steps better.

---

### Post by matt_symes on 2012-06-09
Hi

> **yakinikku said:**
> I read the comments and it looked like he updated the script to work with BURG.  

I actually just deleted the linux partition :O.  I am going to start over and see if I get the same errors.  I know that was the hyper destructive way to go about it, but I can't remember everything I did.  That was my fault, this time I will trace my steps better.

No worries :D It was probably fixable though.

Keeping a note of what you type is always a good idea and is something i do.

I have an entire folder full of commands that i have run and steps i have taken to configure my Linux installs.

Kind regards

---

### Post by yakinikku on 2012-06-10
> **matt_symes said:**
> Hi



No worries :D It was probably fixable though.

Keeping a note of what you type is always a good idea and is something i do.

I have an entire folder full of commands that i have run and steps i have taken to configure my Linux installs.

Kind regards

Thanks :).  I agree with you about it probably being fixable.  I am going to re-do the install this weekend and I will probably get the same problem again, so I will update this thread with results soon.

---

### Post by Derek Karpinski on 2012-06-10
Although Burg is pretty bad-***, it hasn't been touched in a few years.  I'd stay away from it.

---

### Post by yakinikku on 2012-06-10
> **Derek Karpinski said:**
> Although Burg is pretty bad-***, it hasn't been touched in a few years.  I'd stay away from it.

I didn't know that.  It's a shame, it is so much more beautiful than GRUB.  I will be reinstalling soon, I hope I can get it sorted this time.  Will update later. :popcorn:

---

