---
title: "Help a Noob fix his FSTAB! (Mount a HDD on boot for network share via samba)"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by DocStrangeLove on 2012-08-26
So after I successfully fixed my samba installation, apparently I got a little carried away reading advice from posts, and edited my fstab without really knowing exactly what I was doing...  as a result I messed up my permissions, and I can't seem to fix them.

My goal was to auto-mount a FAT32 partition at boot-up time because it is my network share drive (I intend to install two more, once this one works).  So, following some instructions having to do with someone else sharing a network drive, I added the following line to my fstab:

```
/dev/sdc1    /media/Music    vfat    default,umask=002   0    0
```

Realizing my mistake I later changed the permission to 000, and then eliminated it completely in favor of the following line:

```
/dev/sdc1    /media/Music    vfat    defaults    0    0
```

But I still have no write permission on my drive, even when I access it locally...  I tried chmod -R 777 to the Music directory but that hasn't worked either...  HELP!

---

### Post by DocStrangeLove on 2012-08-26
P.S. I don't know if it's relevant, but here's some more system information...

It's a 7-yr old computer (with a 5-yr old processor) and the Media drive (sdc) is a 160G ATA Western Digital . My motherboard is so old that my primary hard drive (sda) is IDE, and the two internal ATA drives I have installed are connected via a PCI SATA-II controller (card).

---

### Post by lolpenguin on 2012-08-26
I somehow don't think the filesystem should be vfat...
Otherwise it looks right.

---

### Post by Paqman on 2012-08-26
FAT32 doesn't accept permissions, so you have to set them in fstab when the drive is mounted. You can't chmod them. In other words, you were on the right track!

It should have worked with umask=000, as that completely removes all restrictions (ie: same as doing chmod 777). Try that again and see what you get. Removes the "defaults" part from the options, as you aren't using the default options any more.

EDIT: vfat is correct, btw.

---

### Post by DocStrangeLove on 2012-08-26
> **Paqman said:**
> FAT32 doesn't accept permissions, so you have to set them in fstab when the drive is mounted. You can't chmod them. In other words, you were on the right track!

It should have worked with umask=000, as that completely removes all restrictions (ie: same as doing chmod 777). Try that again and see what you get. Removes the "defaults" part from the options, as you aren't using the default options any more.

EDIT: vfat is correct, btw.


BOOM! Done, and done.
TYVM!!!

And now on to a new post to solve my video problems...

---

### Post by DocStrangeLove on 2012-08-26
ditto

---

### Post by Paqman on 2012-08-26
> **DocStrangeLove said:**
> BOOM! Done, and done.
TYVM!!!

And now on to a new post to solve my video problems...

Just so you're aware, setting umask=000 leaves you with absolutely no restrictions on that drive. That's probably fine for a storage drive on your own network, but it is possible to set more secure permissions if you want.

For example: umask=111 would remove execute permissions for everybody.

You can also set ownership of the drive through fstab (by specifying a uid or gid). That would allow you to set different permissions for yourself and for others, for example. Say you wanted to give yourself full access, but restrict all other users to read-only, you'd add: uid=1000,umask=033 (assuming your uid is 1000).

---

### Post by DocStrangeLove on 2012-08-26
I need to know a bit more about uids and gids before I do that--e.g., does setting the group permissions for "sambashare" affect all the guests logged in to the network--but that's very helpful thanks!

---

### Post by Paqman on 2012-08-26
> **DocStrangeLove said:**
> I need to know a bit more about uids and gids before I do that

Fair enough, just wanted to make sure you were aware that setting permissions to super-permissive like I suggested wasn't the only option.

> 
--e.g., does setting the group permissions for "sambashare" affect all the guests logged in to the network--but that's very helpful thanks!

I'm not really boned up on Samba, but if that's a group that Samba uses then I would expect it to. You might find that Samba simply refuses to work at all if it doesn't have the required access to the share.

---

