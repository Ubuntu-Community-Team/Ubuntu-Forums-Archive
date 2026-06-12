---
title: "PartImage"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by Mike Zahorik on 2012-12-31
Well, I have another quick question. I just downloaded PartImage. I have used this program quite a bit, but with Knoppix 6.2.1. I think that the program was installed, at least the center said it was. But..... how do I start this program, I can't find it in the menus. Must I always start PartImage through the terminal?

Thanks Mike

---

### Post by monkeybrain2012 on 2012-12-31
Well Partimage doesn't support ext4, which means it is useless for most current Linux installations (and it doesn't support NTFS either, so what is it for???). It seems that the project has been long dead.

---

### Post by Cheesemill on 2012-12-31
Fsarchiver is a good alternative:
[http://www.fsarchiver.org/Fsarchiver_vs_partimage](http://www.fsarchiver.org/Fsarchiver_vs_partimage)

---

### Post by Mike Zahorik on 2012-12-31
I know that it does work just fine on NTFS. I will attempt to use it on EXT4 and see what happens before I condemn it.  And if not I can convert back to EXT3.

The general question is how does a new program get into the gnome menu system? Must you write a small batch file and exe it from a menu item?

Mike

---

### Post by Mike Zahorik on 2012-12-31
Well.... I found under System Tools something called main menu and I created a menu item called Part Image and it works. But how do I group these items into a menu list that is the way I want to look at them?

Mike

---

### Post by sudodus on 2012-12-31
I used PING (which is a live front-end to partimage), and I was happy with it for ext3 and ntfs file systems. But when I installed my first ext4 system, I had to find something else.

Now I use Clonezilla, which is a live front-end to several tools. I think Partclone is the most modern tool, and it works very efficiently with all file systems, that I use. It is much faster than PING with partimage, so I recommend that you download Clonezilla and make a boot CD/USB drive and start using it, or if you work with a big system, use Clonezilla server edition.

[[COLOR="Red"]http://clonezilla.org/[/COLOR]]("http://clonezilla.org/")

---

