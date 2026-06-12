---
title: "[SOLVED] Default Groups"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by victorbrca on 2008-07-31
I was trying to install VBox and I think somehow I screwed the groups for my user, I'm not able to sudo anymore.

This is what I ran:
```
$ sudo usermod -G vboxusers [user]
$ id
uid=1000(user) gid=1000(user) groups=114(vboxusers),1000(user)
```

How can I fix this? I still have root access to the box.

Thanks!!

Vic.

---

### Post by drs305 on 2008-07-31
Well, here are my listings from *id*:
```

uid=1000(drs64) gid=1000(drs64) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),29(audio),30(dip),40(src),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),129(sambashare),1000(drs64)

```

But if you have sudo capability through another user or recovery mode (without sudo) the command would be:
```

sudo adduser *username* admin

```

---

### Post by victorbrca on 2008-07-31
> **drs305 said:**
> Well, here are my listings from *id*:
```

uid=1000(drs64) gid=1000(drs64) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),29(audio),30(dip),40(src),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),129(sambashare),1000(drs64)

```

But if you have sudo capability through another user or recovery mode (without sudo) the command would be:
```

sudo adduser *username* admin

```

Thanks. I have another server I installed at the same time with similar setup, so I'll use the groups I have there!! 

I thought "usermod -G" would add the group to the "Other groups" of that user!!  :-S


Vic.

---

