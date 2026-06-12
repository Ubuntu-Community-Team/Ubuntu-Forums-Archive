---
title: "Conky help with hddtemp"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Tom--d on 2008-06-12
I cannot get hddtemp to work in Conky.

I can see it in terminal, 
```
tom@Laptop:~$ sudo hddtemp /dev/sda
[sudo] password for tom: 
/dev/sda: TOSHIBA MK1237GSX: 36°C
tom@Laptop:~$ 

```

And in Conky I need,
```

hddtemp

dev, (host,(port))

Displays temperature of a selected hard disk drive as reported by the hddtemp daemon running on hostort. Default host is 127.0.0.1, default port is 7634. 
```
AS listed here under hddtemp, [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

and with hddtemp, I need this:
```
        -d, --daemon
              Execute hddtemp in TCP/IP daemon mode (port 7634 by default). (shown in man hddtemp)
```
and done that, 
```

tom@Laptop:~$ sudo hddtemp /dev/sda -d
tom@Laptop:~$
```
To work with my conky.

Ive tried theses in my conky and these are the out puts:
```
 ${hddtemp /dev/sda 7634} = N/A
${hddtemp /dev/sda, (127.0.0.1,(7634))} = N/A
${hddtemp /dev/sda, 127.0.0.1:7634} = N/A
${hddtemp /dev/sda 127.0.0.1:7634} = N/A
${hddtemp 127.0.0.1:7634} = N/A
${hddtemp /dev/sda 127.0.0.1 7634} = ERR
${hddtemp /dev/sda 127.0.0.1:7634} = N/A

```

And nothing.

Where am I going wrong?

Thanks, 
Tom

---

### Post by Tom--d on 2008-06-12
Anyone?

---

### Post by spiderbatdad on 2008-06-12
Maybe the .conkyrc thread will be of some help:[http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc)

More commonly, I've seen it configured as:
Temp: ${acpitemp}

---

