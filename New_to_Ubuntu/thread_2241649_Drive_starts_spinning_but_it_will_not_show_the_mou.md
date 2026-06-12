---
title: "Drive starts spinning but it will not show the mounted disc"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by viktor5 on 2014-08-27
Hi guys,
I'm on Lubuntu 14.04 and I just noticed[SIZE=3][FONT=UbuntuRegular]that if a insert a CD of any kind, the Drive will start spinning but it will not show the mounted disc.[/FONT][/SIZE][COLOR=#333333][FONT=UbuntuRegular]

[SIZE=3]That's what I tried so far:[/SIZE]
[/FONT][/COLOR]> [FONT=Ubuntu Mono]$ sudo mount -o ro,unhide,uid=1000 /dev/cdrom /mnt/cdrom[/FONT]mount: mount point /mnt/cdrom does not exist
[COLOR=#333333][FONT=UbuntuRegular]
 [SIZE=3]These are my last two lines of dmesg after having inserted a cd rom(the drive started to spin):[/SIZE]
[/FONT][/COLOR]> [ 7215.976049] end_request: I/O error, dev fd0, sector 0
[ 7216.000069] end_request: I/O error, dev fd0, sector 0
[COLOR=#333333][FONT=UbuntuRegular]

[SIZE=3]What can I do to make it work?

Thanks for your help[/SIZE][/FONT][/COLOR]

---

### Post by yancek on 2014-08-27
I don't use Lubuntu but a couple of suggestions, check the /media directory to see if it is there as a lot of newer distributions use that directory as a mount point for access.  You might try changing your command from:  /dev/cdrom to /dev/sr0 (that's a number zero not a Letter O).

---

