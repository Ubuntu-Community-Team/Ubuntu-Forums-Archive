---
title: "/dev/tty*"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-11-13
hi all
can sum1 plz explian what does this fol means??? a little bit in detail plz as i m new to it:(
nasir@NASIR:~$ ls /dev/tty*
/dev/tty    /dev/tty23  /dev/tty39  /dev/tty54      /dev/ttyS10  /dev/ttyS26
/dev/tty0   /dev/tty24  /dev/tty4   /dev/tty55      /dev/ttyS11  /dev/ttyS27
/dev/tty1   /dev/tty25  /dev/tty40  /dev/tty56      /dev/ttyS12  /dev/ttyS28
/dev/tty10  /dev/tty26  /dev/tty41  /dev/tty57      /dev/ttyS13  /dev/ttyS29
/dev/tty11  /dev/tty27  /dev/tty42  /dev/tty58      /dev/ttyS14  /dev/ttyS3
/dev/tty12  /dev/tty28  /dev/tty43  /dev/tty59      /dev/ttyS15  /dev/ttyS30
/dev/tty13  /dev/tty29  /dev/tty44  /dev/tty6       /dev/ttyS16  /dev/ttyS31
/dev/tty14  /dev/tty3   /dev/tty45  /dev/tty60      /dev/ttyS17  /dev/ttyS4
/dev/tty15  /dev/tty30  /dev/tty46  /dev/tty61      /dev/ttyS18  /dev/ttyS5
/dev/tty16  /dev/tty31  /dev/tty47  /dev/tty62      /dev/ttyS19  /dev/ttyS6
/dev/tty17  /dev/tty32  /dev/tty48  /dev/tty63      /dev/ttyS2   /dev/ttyS7
/dev/tty18  /dev/tty33  /dev/tty49  /dev/tty7       /dev/ttyS20  /dev/ttyS8
/dev/tty19  /dev/tty34  /dev/tty5   /dev/tty8       /dev/ttyS21  /dev/ttyS9
/dev/tty2   /dev/tty35  /dev/tty50  /dev/tty9       /dev/ttyS22  /dev/ttyUSB0
/dev/tty20  /dev/tty36  /dev/tty51  /dev/ttyprintk  /dev/ttyS23  /dev/ttyUSB1
/dev/tty21  /dev/tty37  /dev/tty52  /dev/ttyS0      /dev/ttyS24  /dev/ttyUSB2
/dev/tty22  /dev/tty38  /dev/tty53  /dev/ttyS1      /dev/ttyS25

---

### Post by Wim Sturkenboom on 2012-11-13
[LIST]
[*]tty are terminals
[*]ttyS are serial ports
[*]ttyUSB are, to my knowledge, devices for communication via USB (e.g. USB to serial converters)
[*]never heard of ttyprintk, possibly syslog output via some port
[/LIST]

---

### Post by Impavidus on 2012-11-13
So they're all low level I/O interfaces, no ordinary files in the windows sense. Don't worry, you won't need them.

---

### Post by syednasirraza on 2012-11-14
thnx for reply...it would be even more beneficial for me if sum1 can refer an article describing these terminals and I/O interfaces

---

### Post by blade4 on 2012-11-14
Here you go : 

[http://ubuntuforums.org/showthread.php?t=833765](http://ubuntuforums.org/showthread.php?t=833765)

The discussion is small but it touches all the basics . 

BTW , to access a tty terminal the command is Ctrl+Alt+F1 - use it if you ever get your system hung . You'll have to log into it though .

---

### Post by syednasirraza on 2012-11-16
> **blade4 said:**
> Here you go : 

[http://ubuntuforums.org/showthread.php?t=833765](http://ubuntuforums.org/showthread.php?t=833765)

  .

thanks alot...got it

---

