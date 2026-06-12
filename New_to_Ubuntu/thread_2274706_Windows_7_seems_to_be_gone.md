---
title: "Windows 7 seems to be gone"
date: 2015-04-21
forum: New to Ubuntu
---

### Post by ahmed32 on 2015-04-21
I just installed ubuntu on my machine but when I start my computer I see no longer the windows 7.If Please help me, in the recovery my windows 7.thank you

---

### Post by matt_symes on 2015-04-21
Hi

This forums is an English language forum.

This forum may be better for you if you don't speak English.

[http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)

EDIT:

Thanks for writing in English.

Kind regards

---

### Post by Bashing-om on 2015-04-21
ahmed32; Hi ! Welcome to the forum .

> **ahmed32 said:**
> [color=red]I just installed ubuntu on my machine[/color] but when I start my computer I see no longer the windows 7.If Please help me, in the recovery my windows 7.thank you

Show us what we are working with.
From ubuntu -> terminal (key combo clt+alt+t) ; 
Post back the results - Between code Tags, please - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]what is, is
[INDENT][INDENT][INDENT][INDENT]what ain't, ain't
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2015-04-22
Sounds like you've chosen to wipe out your hard drive and did a complete installation of Ubuntu. Do you have the installation disk with Windows 7 on it?

---

### Post by Mark Phelps on 2015-04-23
It's likely that you have not added Win7 to the GRUB configuration file -- which is easily done.

But ... you need to respond to the commands you were provided by Bashing-om -- so we can see the state of your machine.

We can't provide detailed help without more information.

---

