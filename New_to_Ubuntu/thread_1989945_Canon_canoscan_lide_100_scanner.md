---
title: "Canon canoscan lide 100 scanner"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by czgirb on 2012-05-29
As title:
I tried to install Canon Lide100 base on the following tutorial:
[http://ubuntuportal.com/2012/02/how-to-get-an-canon-canoscan-lide-100-scanner-to-work-in-ubuntu-11-10linux-mint-12.html](http://ubuntuportal.com/2012/02/how-to-get-an-canon-canoscan-lide-100-scanner-to-work-in-ubuntu-11-10linux-mint-12.html)

> 
The above command will download and put the sane-backends in your  home directory. The next step is to compile the file. Still in the  terminal, go to the directory sane-backends and configuration using the  command:
 **cd sane-backends** [B]./configure --pfefix=/usr --sysconfdir=/etc --localstatedir=/var
[/B][B]
[SIZE=4][B][FONT=Arial]
My result is:[/FONT][/B][/SIZE]
[/B][FONT=Lucida Sans Unicode]* czgirb@ubuntu:~$ cd sane-backends
* czgirb@ubuntu:~/sane-backends$ 
* czgirb@ubuntu:~/sane-backends$ ./configure --pfefix=/usr --sysconfdir=/etc --localstatedir=/var
* configure: error: unrecognized option: `--pfefix=/usr'
* Try `./configure --help' for more information[/FONT][B]

Is there anything wrong?
Please guide me

PS:
I used Ubuntu 10.04
[/B]

---

### Post by nothingspecial on 2012-05-29
It should be** prefix** not **pfefix**

---

### Post by codemaniac on 2012-05-29
I can see a typo error , --**pfefix **instead of --**prefix **!!

<edit>Sorry for the redundant post .Me and NSP were just miliseconds apart ;)</edit>

---

### Post by czgirb on 2012-05-29
Thank you

---

### Post by czgirb on 2012-05-29
SORRY! It's not finished. SORRY!

I follow all the instruction, which written on:
[http://ubuntuportal.com/2012/02/how-to-get-an-canon-canoscan-lide-100-scanner-to-work-in-ubuntu-11-10linux-mint-12.html](http://ubuntuportal.com/2012/02/how-to-get-an-canon-canoscan-lide-100-scanner-to-work-in-ubuntu-11-10linux-mint-12.html)
[http://bdhacker.wordpress.com/2011/04/25/canon-lide-100-scanner-in-ubuntu-with-sane-installation-permission-fixes/](http://bdhacker.wordpress.com/2011/04/25/canon-lide-100-scanner-in-ubuntu-with-sane-installation-permission-fixes/)

My Ubuntu **detect** my scanner
> 
czgirb@ubuntu:~$ lsusb
Bus 002 Device 002: ID 046d:c054 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04a9:1904 Canon, Inc. 
Bus 001 Device 002: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
So I go to Applications > Graphic > Simple Scan, but the result is **Failed to Scan** ... close **Simple Scan**. Post this, and re-open** Simple Scan**.> 
**No Scanner Detected**
Please check your scanner is connected and powered on
Have a clue?

3-minutes ago:
> 
czgirb@ubuntu:~$ sudo scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

czgirb@ubuntu:~$ lsusb
Bus 002 Device 002: ID 046d:c054 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04a9:1904 Canon, Inc. 
Bus 001 Device 002: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
czgirb@ubuntu:~$
Have a clue?

**updated on may 29, 2012 2343**
Please help ...
Thank you

---

### Post by czgirb on 2012-05-29
sorry double post ... please delete

---

### Post by nothingspecial on 2012-05-29
Thread renamed as the previous title no longer reflects the question.

---

