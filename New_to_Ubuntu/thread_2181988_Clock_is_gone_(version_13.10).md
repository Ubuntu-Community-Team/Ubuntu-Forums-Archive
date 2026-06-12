---
title: "Clock is gone (version 13.10)"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by Krabun on 2013-10-19
Ubuntu 13.10
I lost my clock in the system tray. In 'System settings' -> tab 'Time and date' the options are all greyed out.

---

### Post by howefield on 2013-10-19
Open a terminal and try the following command.

```
killall unity-panel-service
```

---

### Post by Krabun on 2013-10-19
Thanks! Worked like a charm.

---

### Post by borischan on 2013-10-19
I had the same problem yesterday, got the clock working, today it disappeared again..... Hope I don't have to do this every time I start up

---

### Post by Fozz on 2013-10-20
Tried this and it didn't work for me. clock panel is greyed out

---

### Post by jakslev2 on 2013-11-03
This is an issue that happens to me every 3 or 4th time i login. Is it a compiz problem?

---

### Post by coffeecat on 2013-11-03
@jakslev2, have you updated your system in the last couple of days? I believe a fix has been issued for this bug:

[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1239710](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1239710)

---

### Post by howefield on 2013-11-03
Are you fully up to date, this seemingly has been fixed in a recent update.

Edit : Whoops, ninja'ed :)

---

### Post by lakshmijiju on 2013-12-03
Thanks. works fine !

---

### Post by jimmyh1972 on 2013-12-03
If you dont like Unity desktop try another like gnome or cinnamon

sudo apt-get install gnome-desktop OR cinnamon

either of them is much more friendly-use

---

### Post by karl.umea on 2014-01-05
Worked like a charm. Thanks!

---

### Post by Stefano_Drei on 2014-04-25
> **howefield said:**
> Open a terminal and try the following command.

```
killall unity-panel-service
```


Thank you again.
The command [COLOR=#000000][FONT=Ubuntu Mono]killall unity-panel-service[/FONT][/COLOR] worked back in December and January on 13.10, since then I have not had any problem with the panel/clock - I have been running 14.04 since early March - then today the clock went missing again, and killing the unity-panel-service still works.

---

### Post by mobrien118 on 2014-05-09
> **Stefano_Drei said:**
> Thank you again.
The command [COLOR=#000000][FONT=Ubuntu Mono]killall unity-panel-service[/FONT][/COLOR] worked back in December and January on 13.10, since then I have not had any problem with the panel/clock - I have been running 14.04 since early March - then today the clock went missing again, and killing the unity-panel-service still works.

I JUST upgraded to 14.04 and immediately started having this issue. It never happened to me in any previous version. Does anyone know what the actual cause is yet?

Thanks,

--mobrien118

---

### Post by alexsmith on 2015-05-06
> **howefield said:**
> Open a terminal and try the following command.

```
killall unity-panel-service
```

Just had the same issue in 14.04.2 and the killall unity-panel-service worked for me too.

```

$ cat /etc/issue
Ubuntu 14.04.2 LTS \n \l

```

---

