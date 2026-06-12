---
title: "compiling MMC Mud Client"
date: 2008-12-19
forum: Packaging and Compiling Programs
---

### Post by Dlinnii on 2008-12-19
Hi, I compiled MMC Mud Client(sources - [http://mmc.mud.ru/mmc-4.1.tar.gz](http://mmc.mud.ru/mmc-4.1.tar.gz)) on ubuntu 8.10 but binary does nothing. On ubuntu 7.10 all was ok.

Any help would be greatly appreciated. Thanks!

---

### Post by Dlinnii on 2008-12-19
I found the problem, but i can't resolve it.

When i use ./mmc > errors.txt, errors.txt it gives me:
```

[?1049h[?1h=[?7l[1;22r[0;37m[H[2J[1;22r[24;1H[44m                                                                                [23;1H[0;37m                                                                                [22;1H
[31;1m-[32m:[31m- [0;37mLoading Main.pm from ./Main.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading strict.pm from /usr/share/perl/5.10/strict.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading integer.pm from /usr/share/perl/5.10/integer.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading locale.pm from /usr/share/perl/5.10/locale.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading vars.pm from /usr/share/perl/5.10/vars.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading warnings/register.pm from /usr/share/perl/5.10/warnings/register.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading warnings.pm from /usr/share/perl/5.10/warnings.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading RStream.pm from ./RStream.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading CL.pm from ./CL.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading fields.pm from /usr/share/perl/5.10/fields.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Ex.pm from ./Ex.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading LE.pm from ./LE.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Conf.pm from ./Conf.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Keymap.pm from ./Keymap.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading MUD.pm from ./MUD.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Parser.pm from ./Parser.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Symbol.pm from /usr/share/perl/5.10/Symbol.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Exporter.pm from /usr/share/perl/5.10/Exporter.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading base.pm from /usr/share/perl/5.10/base.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading CMD.pm from ./CMD.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading DCommand.pm from ./DCommand.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading UAPI.pm from ./UAPI.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Status.pm from ./Status.pm
[23;1H[22;1H
[31;1m-[32m:[31m- [0;37mLoading Ticker.pm from ./Ticker.pm
[23;1H[22;1H
[31;1m-[32m:[31m- #perl: Not a HASH reference at ./Ticker.pm line 15.
[23;1H[22;1H
-[32m:[31m- #perl: Not a HASH reference at ./Ticker.pm line 15.
[23;1H[22;1H
-[32m:[31m- #perl: Not a HASH reference at ./Ticker.pm line 15.
[23;1H[22;1H
-[32m:[31m- #perl: BEGIN failed--compilation aborted at ./Main.pm line 22.
[23;1H[22;1H
-[32m:[31m- #perl: Not a HASH reference at ./Ticker.pm line 15.
[23;1H[22;1H
-[32m:[31m- #perl: BEGIN failed--compilation aborted at ./Main.pm line 22.
[23;1H[22;1H
-[32m:[31m- Not a HASH reference at ./Ticker.pm line 15. BEGIN failed--compilation abort

ed at ./Main.pm line 22. 
[23;1H[1;24r[24;1H[m
[?1l>[?1049l[?7h2964 bytes written to the terminal, 40.44% escape sequences


```

I tried:
 ./mmc INC=".;..;/usr/local/lib/perl/5.10.0;/usr/local/share/perl/5.10.0;/usr/lib/perl5;/usr/share/perl5;/usr/lib/perl/5.10;/usr/share/perl/5.10;/usr/local/lib/site_perl"

But it gives the same :(

---

