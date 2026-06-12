---
title: "MacBook Display Issues"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by Maxadax on 2012-12-17
Hi,

I installed Ubuntu about a week ago (for the second time) and I've realized I'm having a kind of 'temperature' issue with my display, as you can see in the picture the display seems to be tinted a shade of blue.

[IMG]http://i.imgur.com/EVwhE.jpg

It doesn't seem to be a problem with Ubuntu itself because when I take screen shots and view them on other devices they seem to be perfectly fine.

[IMG]http://i.imgur.com/ujgo9.png

Does anyone know if there a fix to this? Perhaps there's an application?

Thanks!

---

### Post by audiomick on 2012-12-17
Yes, that does look like the hardware is not displaying properly.

How old is the machine? My first thought is that the display is getting old. Do you have a dual boot, so that you can compare to the macintosh OS?

I have an intel machine with nVidia drivers for the graphics card. In the utility for that there is a page for colour correction. If the problem is there right from boot, and doesn't change with time, you might like to look for something like that.

If the problem does change as the machine warms up, I wouldn't try and fix it there. That would indicate maybe a heat problem or something that you really need to get to the bottom of.

I'm not sure how to get to the monitor utility on the unity desktop. I think it is in a menu that opens from an icon on the upper right in system settings. You could also try typing "monitor" in the search box in the dash.

---

### Post by Maxadax on 2012-12-17
> **audiomick said:**
> Yes, that does look like the hardware is not displaying properly.

How old is the machine? My first thought is that the display is getting old. Do you have a dual boot, so that you can compare to the macintosh OS?

I have an intel machine with nVidia drivers for the graphics card. In the utility for that there is a page for colour correction. If the problem is there right from boot, and doesn't change with time, you might like to look for something like that.

If the problem does change as the machine warms up, I wouldn't try and fix it there. That would indicate maybe a heat problem or something that you really need to get to the bottom of.

I'm not sure how to get to the monitor utility on the unity desktop. I think it is in a menu that opens from an icon on the upper right in system settings. You could also try typing "monitor" in the search box in the dash.

Thanks,

I have a dual boot with OS X and the display seems to be showing fine so it must be a software issue of some kind. I searched 'NVidia' in the software centre and I'm installing NVidia binary X.Org driver ('version 173' driver).

EDIT: The driver didn't seem to fix it.

---

### Post by audiomick on 2012-12-17
> **Maxadax said:**
>  I searched 'NVidia' in the software centre and I'm installing NVidia binary X.Org driver ('version 173' driver).

EDIT: The driver didn't seem to fix it.

Do you actually have an nVidia graphics card? I don't know what apple puts in there. You can find out for sure with
```
lshw -C video
```

---

### Post by Maxadax on 2012-12-18
> **audiomick said:**
> Do you actually have an nVidia graphics card? I don't know what apple puts in there. You can find out for sure with
```
lshw -C video
```

Yeah, I have an NVidia GeForce 320M I believe.

---

