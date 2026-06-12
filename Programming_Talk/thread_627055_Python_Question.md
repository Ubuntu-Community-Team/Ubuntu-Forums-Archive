---
title: "Python Question"
date: 2007-11-29
forum: Programming Talk
---

### Post by nesh87 on 2007-11-29
Hey guys,

i got myself a new huawei e220 modem and im _trying_ to create a python program to do all the connecting for me. Ive created a very simple and "first draft" of the gui. What i want to do is check if the modem is plugged in and treated as a modem instead of a storage. 

```

p = os.popen('ls /dev/ttyU* | wc -l')
x = p.readline()
p.close()

```

this works fine. If it doesnt return the output however, im trying to call the script provided with someone to start the modems. (cant remember who it is but the script is called huaweiAktBbo-i386.out so credit goes to him). When i try to read the output of running the script i only get the first line instead of all 3.

First question:
how do i get all lines of output:
```

Hladam HUAWEI E220 a prepnem na modem - bbo 06
4 set feature request returned -1
Prepnute-OK, Mas ttyUSB0 ttyUSB1 (cez usbserial vendor=0x12d1 product=0x1003)
pozri /proc/bus/usb/devices
```

instead of getting only:
```
Hladam HUAWEI E220 a prepnem na modem - bbo 06
```

My second question is how do i call wvdial and keep my GUI responding instead of it turning gray since the command i called doesnt end until i close it.

Third and final question, i have a text view in my gui, how would i get the terminal output of wvdial into the text view.

Im sorry for the amount of questions but please bear with me. Oh and please go easy on the answers, i'm very new to Python.

Thanks

---

### Post by LaRoza on 2007-11-29
Use readlines, not readline.

---

