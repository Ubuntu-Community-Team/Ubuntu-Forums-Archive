---
title: "execute downloaded files (including WINE)"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by peterbmetcalf on 2013-04-30
Someone in the forum recommended using WINE for slower computers in order to execute downloaded files. However, if I am not mistaken, WINE is an executable file that must be downloaded. How does one execute WINE in linux/ubuntu?
Thanks very much.

---

### Post by oldos2er on 2013-04-30
> **peterbmetcalf said:**
> Someone in the forum recommended using WINE for slower computers in order to execute downloaded files. 

Non sequitur? [Wine]("http://www.winehq.org/") is software used to run some Windows programs under Linux; it has nothing to do with "slower" computers.

> **peterbmetcalf said:**
> However, if I am not mistaken, WINE is an executable file that must be downloaded. How does one execute WINE in linux/ubuntu?
Thanks very much.

You don't run Wine by itself, you use it invoke a Windows program, for example ```
wine ~/.wine/drive_c/Program\ Files/Internet\ Explorer/iexplore.exe
```

Can you give some more details e.g. Ubuntu version, and which programs you're trying to run?

---

### Post by The Cog on 2013-04-30
That's ugly. This is better:
```
wine ~"/.wine/drive_c/Program Files/Internet Explorer/iexplore.exe"
```

---

### Post by monkeybrain2012 on 2013-04-30
> **The Cog said:**
> That's ugly. This is better:
```
wine ~"/.wine/drive_c/Program Files/Internet Explorer/iexplore.exe"
```

Why? This is still ugly. :) If you have an .exe file you just click it. It will run if WINE is installed.

---

### Post by Baldrick_NZ on 2013-05-01
> **monkeybrain2012 said:**
> ...It will run if WINE is installed.

Not necessarily. 

It runs some seamlessly, some with minor issues, some with major issues (eg: iTunes), and some not at all.

If your windows program is fairly common, you can check it's workability under Wine here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

As always, check the software centre, as there is often a native Linux program which might be an acceptable alternative, or maybe even the same thing as Windows, eg: VLC, Firefox, Opera, Google Chrome, etc... Using Windows programs should always be a last resort under Linux.

---

### Post by monkeybrain2012 on 2013-05-01
> **Baldrick_NZ said:**
> Not necessarily. 

It runs some seamlessly, some with minor issues, some with major issues (eg: iTunes), and some not at all.

If your windows program is fairly common, you can check it's workability under Wine here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

As always, check the software centre, as there is often a native Linux program which might be an acceptable alternative, or maybe even the same thing as Windows, eg: VLC, Firefox, Opera, Google Chrome, etc... Using Windows programs should always be a last resort under Linux.

I know that. What I meant was that if the .exe file runs under WINE, it will run by simply clicking it without having to use the command line. I think the context should have made it clear. :)

---

