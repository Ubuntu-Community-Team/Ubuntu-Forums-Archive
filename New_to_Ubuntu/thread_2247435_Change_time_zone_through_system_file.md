---
title: "Change time zone through system file"
date: 2014-10-07
forum: New to Ubuntu
---

### Post by Aiuna on 2014-10-07
Hello!

I can't change time zone. I tried: sudo dpkg-reconfigure tzdata, but it doesn't change

Current default time zone: 'Europe/Moscow'
Local time is now:      &#1057;&#1088;. &#1086;&#1082;&#1090;.  8 05:42:06 MSK 2014.
Universal Time is now:  Wed Oct  8 01:42:06 UTC 2014.

:~/engineering/masterThesis$ date
&#1057;&#1088;. &#1086;&#1082;&#1090;.  8 10:45:00 IRKT 2014

The last time I wanted to change the time zone I opened some system file (I don't remember the name) and cut one symbol (#). Now I can't find either the file or the site with an advice to work with it. 

Thanks :)

---

### Post by pissedoffdude on 2014-10-07
Hi,

Try
```
sudo ln -s /usr/share/zoneinfo/Europe/Minsk /etc/localtime
sudo hwclock --systohc --localtime
```

Assuming you want localtime and not UTC.  Also, if a localtime link already exists, run the command with a -sf

---

### Post by stalkingwolf on 2014-10-08
try right clicking on the clock and then click preferences

---

### Post by Aiuna on 2014-10-28
> **stalkingwolf said:**
> try right clicking on the clock and then click preferences

I did it, but after I reboot the laptop the wrong time appears again.

---

### Post by Aiuna on 2014-10-28
> **pissedoffdude said:**
> Hi,

Try
```
sudo ln -s /usr/share/zoneinfo/Europe/Minsk /etc/localtime
sudo hwclock --systohc --localtime
``` 

It changes the time I see when I log out. But doesn't change the icon when I'm logged in. 

I also tried to search the history with history | grep sudo, but it shows just the last 1 thousands commands. I suspect that I changed the time zone before)

---

### Post by whitesmith on 2014-10-28
Maybe this will help you: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime). Cheers!

---

### Post by Aiuna on 2014-10-28
> **whitesmith said:**
> Maybe this will help you: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime). Cheers!

I installed ntp, it looks like it synchronised the time I see when I log out.

---

### Post by Aiuna on 2014-11-14
I made it!

The system time I changed was ~/.profile

So I edited timezone there :rolleyes:

---

