---
title: "CUPS server error"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by ztac on 2013-01-31
Hello..
I got this error when I add a new printer.

CUPS server error
There was an error during the CUPS operation: 'server-error-internal-error'.

Please help..

---

### Post by omeomi on 2013-01-31
Can you provide a little bit more information? 

Which Ubuntu version do you run? What printer? Which driver did you select? Did you use the command line or web interface ([http://localhost:631/]("http://localhost:631/")) to add the printer?

---

### Post by ztac on 2013-02-03
> **omeomi said:**
> Can you provide a little bit more information? 

Which Ubuntu version do you run? What printer? Which driver did you select? Did you use the command line or web interface ([http://localhost:631/]("http://localhost:631/")) to add the printer?
I am using ubuntu 12.04 and i am trying to add epson lq300+ii to printers in administration menu..After adding ppd file (eplq.ppd) and clicking apply, the error appears..

CUPS server error

---

### Post by tgalati4 on 2013-02-03
Look through the files in /var/log/cups for any clues.

---

### Post by ztac on 2013-02-04
> **tgalati4 said:**
> Look through the files in /var/log/cups for any clues.
**error log
Returning  IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/Epson-LQ-300+) from localhost

Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf
**

I opened the cupsd.conf and this is what on the line 16:
SystemGroup lpadmin

---

### Post by tgalati4 on 2013-02-04
My SystemGroup is on line 3, so that is strange. And it is set to the correct value.

You can change loglevel warnings then reboot cups:

       LogLevel debug2
       LogLevel debug
       LogLevel emerg
       LogLevel error
       LogLevel info

from:

```
man cupsd.conf
```

It's possible that your cups installation is badly broken.  Try removing and reinstalling.  Did you update your kernel lately?  Did you edit /etc/hosts?

You should have localhost defined:

tgalati4@Dell600m-mint14$ cat /etc/hosts
127.0.0.1	localhost

---

