---
title: "Pidgin will not start"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by blegs38552 on 2008-09-28
Running Ubuntu 8.04 with all updates. I launched Pidgin this morning and added my AIM info. Logged on successfully.

Closed out, restarted and tried to start app again. All I get is a spinning wheel for a few seconds, but it doesn't proceed any further. I am connecting wirelessly and both my Firefox and my Evolution apps are running fine.

I tried reinstalling through Synaptic Package Manager, but no luck - still just starts the spinning wheel.

---

### Post by zmjjmz on 2008-09-28
I'm sorry to hear that, but I'm afraid you've posted in the wrong forum.

Anyways, open a terminal (Applications>Accessories>Terminal) and type ```
pidgin
``` then hit enter.
Hopefully you should see some text appear regarding how well Pidgin is starting; post that output here (in a ```

``` tag)

---

### Post by overdrank on 2008-09-28
Moved :)

---

### Post by steveneddy on 2008-09-28
You may try reinstalling if launching from the terminal fails.

---

### Post by mindoms on 2008-09-28
no need to reinstall it.
just delete or rename your pidgin config.
close pidgin and in terminal type:
```
killall pidgin
```
just to make sure no (zombie) instance af pidgin is running
```
mv ~/.purple ~/purple_safe
```
to rename the pidgin setings folder.
when you start pidgin the next time, pidgin forgot all settings and logs and you need to set up all accounts again. but it should work

---

### Post by nbayiha on 2008-09-28
Just use Kadu kadu. I think the have a deb package :D

---

