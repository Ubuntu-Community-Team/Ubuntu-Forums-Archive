---
title: "reconnect usb 3G dongle"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by shimazaki on 2012-04-24
Hi,

I'm a newbie in Ubuntu, so I trying to discover if there is any application or other "thing", maybe a script to automatically reconnect a usb 3G dongle if the connection drops?
I´m using a Huawei E272

thanks in advance

---

### Post by westie457 on 2012-04-24
Hi welcome to the Forum.

If you click on the Network Manager icon - the one that looks like part of a radar screen - then click Edit Connections. In the pop up window click on the Mobile tab an check the two small boxes.

Screenshot attached for clarity.

---

### Post by shimazaki on 2012-04-24
Thanks Westie457 for your quick reply
I will give it a try  :)

---

### Post by spiky001 on 2012-04-24
Hi  You can run ```
sudo killall modem-manager
```that will restart the dongle. You would have to make a script that pings google every so often and when there is no reply then have it restart modem.

---

### Post by spiky001 on 2012-04-24
Hi

I put this togeather I,m no script writer

```

#/bin/bash

# Script to restart 3dongle

if ping -c 1 www.google.com

  then
        sleep 10

  else
        sudo killall modem-manager

fi

```Nmae it Restart-3Dongle Then put it in /bin

Make it executable
```
chomd +x /bin/Restart-3Dongle
```  The sleep part can be adjusted from 10 secs to what ever you want.

If any one can make this better plz do or if something is wrong with it.

---

### Post by shimazaki on 2012-04-24
Thanks spiky001

I will test the script,

asap I will give feedback on my attemps to build my first script

---

