---
title: "Printing in Linux - CUPS"
date: 2008-10-27
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-10-27
Hi  everybody,
I'm going to write an print accounting program on Linux for a network, and I have some questions :

1) Can I share a printer under Linux for a windows and Linux network ?
2) Can I control jobs (pause, stop, resume ... ) with CUPS as they come to the server ???
If the answers is no, Is there any way ?
Thanks for your consideration

---

### Post by slavik on 2008-10-27
Yes and Yes.

I also recommend you look into Pykota.

---

### Post by hosseinyounesi on 2008-10-27
Thanks, but how ? (I don't want to use PyKota)

---

### Post by slavik on 2008-10-27
Tea4Cups ...

this is not a simple thing, since you have to write your own backend and such. (I have never done anything similar to this ...)

---

### Post by nvteighen on 2008-10-27
Just for you to know, you can interface to the CUPS server through its API. I once created a little C application that printed stuff...

All you need is the 'libcupsys2-dev' package. The API docs are located at [http://localhost:631/help/?TOPIC=Programming&QUERY=](http://localhost:631/help/?TOPIC=Programming&QUERY=) (yeah, you can access them through the CUPS server...)

---

### Post by hosseinyounesi on 2008-10-28
Thanks, And anyone installed Pykota on Linux ? I got that it has been tested on Debian, how about openSUSE, Fedora or UBUNTU ?

---

### Post by slavik on 2008-10-28
since CUPS is not different between different distros, I gather that Pykota would work on all of them ;)

---

### Post by hosseinyounesi on 2008-10-29
You are right. It is not important for cups, but how about PyKota ?
Maybe they have used something that is only available on Debian based. Anyone tested it on RPM based, for example CENTOS or openSUSE ?

---

### Post by slavik on 2008-10-29
umm, Pykota requires Python and CUPS ...

---

### Post by hosseinyounesi on 2008-10-29
ok ok, thanks And I'm now going to test it :)

---

### Post by gimmejimmy on 2008-10-30
This looks like just what I need, but I can't open pykota.com.  That is the site isn't it?

---

### Post by hosseinyounesi on 2008-11-03
[http://www.pykota.com/](http://www.pykota.com/)  ?
That's right and it works. I'm trying to install it, but there is an error :

[COLOR="Navy"]The following command will be launched to import the PDF print queue into PyKota's database and reroute it through PyKota :
pkprinters --add --cups --description "Printer created with pksetup" "PDF"
Do you agree ? y[/COLOR]
[COLOR="Red"]Traceback (most recent call last):
  File "/usr/bin/pkprinters", line 31, in <module>
    from pykota.tool import Percent, PyKotaTool, PyKotaCommandLineError, crashed, N_
ImportError: cannot import name Percent[/COLOR]

Anyone knows what is it ?

---

### Post by hosseinyounesi on 2008-11-14
Fixed by downloading the latest version :)

---

