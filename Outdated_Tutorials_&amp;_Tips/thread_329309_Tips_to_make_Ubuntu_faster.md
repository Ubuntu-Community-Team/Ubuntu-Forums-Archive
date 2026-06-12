---
title: "Tips to make Ubuntu faster"
date: 2007-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by raul_ on 2007-01-01
I don't know if these guides have been posted here before but here they are anyway. I also found some prelinking guides but since prelinking and preloading is already explained here in the forums i'll stick with this article which is divided in 3 parts:

Part 1: [http://www.linuxjournal.com/article/8308]("http://www.linuxjournal.com/article/8308")

Part 2:
[http://www.linuxjournal.com/article/8317]("http://www.linuxjournal.com/article/8317")

Part 3:
[http://www.linuxjournal.com/article/8322]("http://www.linuxjournal.com/article/8322")

This guide has some really good tips if you want to load OpenOffice or Firefox in 2 seconds. It also tells you how to disable some of the shells that are always loaded in memory (6) in order to free some.

NOTE: Enabling DMA may not work with SATA drives. There is a really good chance that you're SATA drive is already doing a good job, so if you own one, just skip that step :cool: 

Keep in mind that i didn't create this guide, i'm only providing links to it, so the credits are not for me :mrgreen:

UPDATE: It seems that Edgy fresh installed doesn't have the /etc/inittab file. If this is your case do the following steps:
```

sudo nautilus

```

browse to the /etc/event.d folder and rename the tty files you don't want to "tty<number>.bak" . For example, if you only want 2 virtual consoles running, rename tty3,4,5 and 6 to tty1.bak, tty2.bak and so on. If you want them again, just rename them to the original name (removing the .bak extension)

---

### Post by franestepona on 2007-01-02
Thanks for the guide man, great help.

---

### Post by earobinson on 2007-01-02
hehe, neat!

---

### Post by raul_ on 2007-01-02
Hey my first replies after a few days :mrgreen: it took so long to be approved that when it was, it was 5 pages behind. 

Anywayz, glad i could help ;)

---

### Post by lucis on 2007-01-02
The first link details editing /etc/inittab, but apparently in Edgy inittab no longer exists. I don't know what would be the new upstart equivalent.

---

### Post by raul_ on 2007-01-02
it exists in my computer :-k running edgy here

---

### Post by lucis on 2007-01-02
> **raul_ said:**
> it exists in my computer :-k running edgy here

Heh, I was worried when I found mine to be nonexistent. I thought I had screwed something else up. :D After Googling around though it looks like it was superseded by upstart's new configuration scheme.

---

### Post by Waappu on 2007-01-02
Hi

Good tips.

raul_ have you upgradet from Dapper because you seems to have /etc/inittab ??

---

### Post by raul_ on 2007-01-02
Yes, i never did a clean install since Hoary :) i guess i'm just lucky

---

### Post by raul_ on 2007-01-02
You guys that don't have the inittab file, try checking /etc/event.d , and see if you can find the tty lines there

---

### Post by Waappu on 2007-01-02
Hi

Does that tip reduce virtual consoles count for you ?

---

### Post by Waappu on 2007-01-02
Hi

I found /etc/event.d folder, but don't know what to do whit it =)

---

### Post by raul_ on 2007-01-02
Actually i never use virtual consoles. Just in case i left 2, but i think even 1 should be enough. Then again, this is a home computer. The max i do with it is college works, but that only includes programming (for now)

---

### Post by raul_ on 2007-01-02
> **Waappu said:**
> Hi

I found /etc/event.d folder, but don't know what to do whit it =)

can you please post the output of

```

cd /etc/event.d/
ls -a

```

---

### Post by Waappu on 2007-01-02
Hi

Here is output from my /etc/event.d
> 
jla@acx:/etc/event.d$ ls -a
.                   rc0           rc2  rc6          sulogin  tty4
..                  rc0-halt      rc3  rc-default   tty1     tty5
control-alt-delete  rc0-poweroff  rc4  rcS          tty2     tty6
logd                rc1           rc5  rcS-sulogin  tty3
jla@acx:/etc/event.d$ 

raul_ after you changed /etc/inittab it realy reduce virtual console count for you? I'm asking because you have Edgy and I'm intrested how things going if you upgrade =)

---

### Post by raul_ on 2007-01-02
I don't know because i didn't try that :mrgreen: i had already disabled them by deleting the tty entries in /etc/event.d . That makes my ctrl+alt+F2-F6 take me to a blank screen, from which i exit by pressing ctrl+alt+F7 .

So i think you can safely remove (and possibly backup) the tty files that you don't want

PS: if you go to the terminal and do "ps aux | grep tty" it should return 6 entries. if i do that it only returns 1 (the one i left) so i guess it's safe to say that i only have 1 virtual console in memory ;)

I'm going to edit the post btw

---

### Post by Waappu on 2007-01-02
Hi

Ok. Thanks for tips =)

---

### Post by sicofante on 2007-01-30
Everytime I find a thread like this I just ask myself: Why on earth don't they [whoever makes or distributes the software] simply make it fast by default?

---

### Post by K.Mandla on 2007-01-30
Some of them do, it's just that there's usually a sacrifice in the easy-to-set-up department. ;) If you want one built fast by default, take a look at [Arch Linux]("http://www.archlinux.org").

---

### Post by bhuvi on 2008-10-25
> **raul_ said:**
> I don't know if these guides have been posted here before but here they are anyway. I also found some prelinking guides but since prelinking and preloading is already explained here in the forums i'll stick with this article which is divided in 3 parts:

Part 1: [http://www.linuxjournal.com/article/8308]("http://www.linuxjournal.com/article/8308")

Part 2:
[http://www.linuxjournal.com/article/8317]("http://www.linuxjournal.com/article/8317")

Part 3:
[http://www.linuxjournal.com/article/8322]("http://www.linuxjournal.com/article/8322")

This guide has some really good tips if you want to load OpenOffice or Firefox in 2 seconds. It also tells you how to disable some of the shells that are always loaded in memory (6) in order to free some.

NOTE: Enabling DMA may not work with SATA drives. There is a really good chance that you're SATA drive is already doing a good job, so if you own one, just skip that step :cool: 

Keep in mind that i didn't create this guide, i'm only providing links to it, so the credits are not for me :mrgreen:

UPDATE: It seems that Edgy fresh installed doesn't have the /etc/inittab file. If this is your case do the following steps:
```

sudo nautilus

```

browse to the /etc/event.d folder and rename the tty files you don't want to "tty<number>.bak" . For example, if you only want 2 virtual consoles running, rename tty3,4,5 and 6 to tty1.bak, tty2.bak and so on. If you want them again, just rename them to the original name (removing the .bak extension)
i renamed tty<number> to tty<number>.bak but still i can press ctrl+alt+<number> to login there

---

