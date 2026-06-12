---
title: "Destroying USB's"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by mmacintosh on 2008-07-02
Hello, 

Can someone tell me how to securely destroy USB drives?

Thanks
MAM:KS

---

### Post by benfindlay on 2008-07-02
As in securely physically destroy them, or securely destroy the data on them?

---

### Post by ukripper on 2008-07-02
> **mmacintosh said:**
> Hello, 

Can someone tell me how to securely destroy USB drives?

Thanks
MAM:KS

You can use many things to destroy your usb. one option is to use blast furnace(normally found in steel plants) to melt the metal bit and circuits at 1600 degrees C .

Easy option is to securely wipe your data or or encrypt the whole drive if it is working and then destroy it.

if it is not working then use the first method blast furnace.

---

### Post by mmacintosh on 2008-07-02
First to get the data off and then destroy the unit itself?

thanks

---

### Post by gerben1 on 2008-07-02
Probably just leaving it in glass of water for a few days will erode the circuitry enough for the unit to be unusable (as a data storage device) and for the data to be irretrievable. Add some salt to speed it up, or even put some voltage on the pins.

---

### Post by benfindlay on 2008-07-02
Take a look at this: [http://www.cyberciti.biz/tips/linux-how-to-delete-file-securely.html]("http://www.cyberciti.biz/tips/linux-how-to-delete-file-securely.html")
and this: [http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

In terms of physical destruction; melting, chemical dissolution will all get the job done, but access to facilities with such capabilities may be problematic, not to mention the H+S concerns involved!

Theres always the big hammer approach! ;)

Hope this helps!

---

### Post by Xerp on 2008-07-02
It doesn't seem very environmentally friendly to simply destroy a perfectly good piece of technology. Securely erase the data and then give the USB drive away if you don't want it :)

[http://ubuntuforums.org/showthread.php?t=204667&highlight=secure+delete](http://ubuntuforums.org/showthread.php?t=204667&highlight=secure+delete)

---

### Post by thebinaryblob on 2008-07-02
you could just use the dd command in a terminal
it writes to a file on a byte-by-byte basis, and could
be used to completely wipe a drive

**for example:**
if your usb drive was /dev/hdb you could use
'dd if=/dev/zero off=/dev/hdb'
make sure you have the right device file though

this should destroy all of the data on the drive, but still leave
the drive usable (assuming the command completes successfully though)
read this: [http://16systems.com/zero/index.html]("http://16systems.com/zero/index.html")

---

### Post by chewearn on 2008-07-02
For shredding, it might be better to use /dev/random rather than /dev/zero

---

### Post by thebinaryblob on 2008-07-02
or /dev/urandom

but its not really necessary, as you could just print the contents
of the drive to a terminal with 'dd if=/dev/drive' to make sure
its blank

---

### Post by sailor2001 on 2008-07-02
it's all magnetic..........just neutralize it with a magnet

---

### Post by Daggo on 2008-07-02
I did an experiment in grade school by leaving a tooth in a glass of coke for a week. It eroded the tooth. Maybe you could leave your usb ina glass of coke for a week and it would erode it just as good. =)

---

