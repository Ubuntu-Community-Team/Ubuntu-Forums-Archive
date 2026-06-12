---
title: "LILO Help"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by 0ni on 2008-06-13
When I boot up Ubuntu 8.04 using LILO, do you know, or have any way of finding out exactly get printed out onto the screen.
 
I would like a log or a file that contains exactly what is printed out, or what is printed out on a typical installation. For example, I get:
 
LILO Loading linux........................
...................................................
 
 
And so on until it has finished booting.
 
I would be very grateful for this, thanks

---

### Post by ajmorris on 2008-06-13
hi there,
i dont really understand what you want... do you want to see text for what lilo is doing when it says it is loading linux? It only shows that just before your bootsplash shows... and all it does is a filesystem check. If you want, you can also turn off your bootsplash.
However, why do you want to use LILO instead of GRUB? LILO is considered somewhat depricated these days...

AJ

---

### Post by ET! on 2008-06-13
you can try typing dmesg (as root) in terminal.

---

### Post by 0ni on 2008-06-13
> **ajmorris said:**
> hi there,
i dont really understand what you want... do you want to see text for what lilo is doing when it says it is loading linux? It only shows that just before your bootsplash shows... and all it does is a filesystem check. If you want, you can also turn off your bootsplash.
However, why do you want to use LILO instead of GRUB? LILO is considered somewhat depricated these days...

AJ

I wanted this for my website so that it looks like a linux installation is loading in the backround without a bootsplash.

> **ET! said:**
> you can try typing dmesg (as root) in terminal.

Thanks, this worked.

---

### Post by andrew.46 on 2008-06-15
Hi:

> **ajmorris said:**
>  LILO is considered somewhat depricated these days...


Well, Lilo is still going strong with Slackware and it is a *very* solid performer.

    Andrew

---

### Post by svar1 on 2008-06-19
My problem is a bit different. I already have a couple of 
 other distros which boot using lilo. So I definitely  will
 not be using grub and do not want hardy to mess with my lilo.
 Ideally I would like to tell it to  create a boot image for lilo
 and perhaps the relevant initrd, but store them somewhere where it is harmless, say /tmp.
 Can I do that from the alrternative iso dvd?

Also, it looks like I am never prompted for a root password, yet when I boot the system, I cannot su(or login as root) because it requires root password, which I was never asked to set.

---

### Post by gtdaqua on 2008-06-19
> **andrew.46 said:**
> Hi:

[QUOTE=ajmorris;5177430]
LILO is considered somewhat depricated these days...

Well, Lilo is still going strong with Slackware and it is a *very* solid performer.

    Andrew[/QUOTE]

I think the post meant to say lilo is not as much focused as GRUB as far as Ubuntu-editions are concerned. This is true even though LILO is maintained and going strong with Slackware.

Try sticking the GRUB in Slackware and the masters there would say 'dont u want o use LILO?' and the questioner would say 'grub is rock-solid in ubuntu..so why not use here??'

:)

---

