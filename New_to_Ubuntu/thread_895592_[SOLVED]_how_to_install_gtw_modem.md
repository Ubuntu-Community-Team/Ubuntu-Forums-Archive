---
title: "[SOLVED] how to install gtw modem"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-20
hey guys! i just installed xubuntu on my laptop and it runs 3x faster than xp, great! my problem is my modem is not detected.  i follow the instructions on help, download scanmodem.gz, visit linmodems.org but can follow instructions how to download the driver for my modem. my modem is GTW V.92 voice modem.  Please help! thanks...

---

### Post by DamonChyld on 2008-08-20
Hmm, did you try this [http://ubuntuforums.org/showthread.php?t=879061?](http://ubuntuforums.org/showthread.php?t=879061?)

---

### Post by vikramaditya on 2008-08-20
Open terminal and cut/paste the following:
```
sudo apt-get install setserial
```
Then run this:
```
setserial -g /dev/ttyS[01]
```
If it outputs something like this:
> /dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
Then the modem has been detected & you create a link with:
```
sudo ln -s /dev/ttyS0 /dev/modem
```
Finally, use **wvdial** to get connected.  Hope it all works for you! :)

"Thanks" to forum member **tinivole**, whose work I have shamelessly plagiarized above.

---

### Post by Joeb454 on 2008-08-20
Please do not create duplicate threads, it's against forum policy

---

