---
title: "[SOLVED] wireless networking help"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Lukky on 2008-05-18
i am trying to get wireless up and running on my Hp dv6815nr with the Atheros 5007. 
   Under the windows wireless drivers it shows the Driver that I installed from Atheros. It says hardware present but when I click to configure my wireless networking everything is faded and i cant configure anything.
   
Thanks Dustin

---

### Post by ajmorris on 2008-05-18
hi there,
can you please post the output of ```
sudo lspci
```

Also, you say you installed the drivers from Atheros, are these the windows drivers and you installed them with ndiswrapper, or are these the native linux drivers?

AJ

---

### Post by hyper_ch on 2008-05-18
output also in addition to the above mentioned the following:


```

lsusb

```

```

iwconfig

```

```

ifconfig

```


```

cat /etc/network/interfaces

```


```

cat /etc/resolv.conf

```

---

### Post by Lukky on 2008-05-18
Thanks guys I got it working somehow. When I turned it on today it gave me a message to connect to a wireless network. Not real sure what I did, but it works. maybe I never restarted after configuring the network settings?

Thanks Dustin

---

