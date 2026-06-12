---
title: "create NTFS?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by nisaky on 2008-09-12
Is it possible to create NTFS partition on Ubuntu? 

I am trying to install Windows XP so i'd have tripleboot with my Ubuntu (and Fedora is here). I tried giving to windows partition with 25GB (FAT 32) but they say there is no partition on which windows could install themselfs. If i try to create partition using windows they still say say thing.  

And what type of partition should i give to windows?


BTW: I know windows sux, but...

---

### Post by KillerSponge on 2008-09-12
Windows only installs on a primary partition, have you checked that?

---

### Post by nisaky on 2008-09-12
I'll try.

---

### Post by halitech on 2008-09-12
windows will have a conniption fit if its not the first OS installed. If you need it, why not try using it in a VM?

---

### Post by nisaky on 2008-09-12
> **KillerSponge said:**
> Windows only installs on a primary partition, have you checked that?

Thanks, did that and windows can install now. But when PC restarts i get "disk error". My PC is OK all thanks to Super Grub CD.

> **halitech said:**
> windows will have a conniption fit if its not the first OS installed. If you need it, why not try using it in a VM?

I need them for games, and games wil run better on wine than VM, even some won't work anyway.



Anyone knows how to pass boot normaly?





EDIT: if it helps here is boot.ini:

```
 [boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\="Unidentified operating system on drive C." 
 
```


[SIZE=4]Don't need help anymore, I am not going to use Errors, I mean Windows.[/SIZE] :D

---

