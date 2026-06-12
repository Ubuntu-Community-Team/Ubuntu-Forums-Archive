---
title: "[SOLVED] Can't connect to network"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by hmich176 on 2008-08-11
Hi, I have an HP Pavilion dv6000 with Ubuntu 8.04.  For some reason, I can't connect to the network.  Password and such hasn't changed.  What I did do, however, was take my laptop over to my friend's house and then bring it back home.  Since then, I haven't been able to reconnect.  I don't think this is a network problem, as I've turned off the network and back on and my desktop has been able to reconnect.  

I do know that the computer can find the network, it just can't find the network key (I guess) and I don't know what to do from here.  

Thanks!

---

### Post by OffAxis on 2008-08-11
The encryption on your network key may have been flipped from WEP to WPA or disabled. Check the network manager and make sure it's right.
Also check the length of the key and make sure it's correct (64-bit, for example).

You could also try disabling encryption at the router and try getting an 'open', unencrypted connection. If you find success there then you can try turning the security back on.

---

### Post by prshah on 2008-08-11
> **hmich176 said:**
> I don't think this is a network problem, as I've turned off the network and back on and my desktop has been able to reconnect.  

1) Try restarting the network; open a terminal (Applications-Accessories-Terminal) then give the command ```
sudo /etc/init.d/networking restart
```

2) If that doesn't work, try ```
sudo dhclient wlan0
```

3) Ifnone of those work, post the results of the previous commands along with:```
iwconfig
sudo iwlist wlan0 scan
``` Replace wlan0 with the actual interface name (which you can find out from the iwconfig command).

---

### Post by hmich176 on 2008-08-11
> **prshah said:**
> 1) Try restarting the network; open a terminal (Applications-Accessories-Terminal) then give the command ```
sudo /etc/init.d/networking restart
```

2) If that doesn't work, try ```
sudo dhclient wlan0
```

3) Ifnone of those work, post the results of the previous commands along with:```
iwconfig
sudo iwlist wlan0 scan
``` Replace wlan0 with the actual interface name (which you can find out from the iwconfig command).

Great!  Option 1 worked.  I'm now online on my laptop!

---

### Post by prshah on 2008-08-11
> **hmich176 said:**
> Great!  Option 1 worked.  I'm now online on my laptop!

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

