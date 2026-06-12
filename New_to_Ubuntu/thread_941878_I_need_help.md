---
title: "I need help"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by a12r13a90 on 2008-10-08
Im trying to install Ubuntu 8.04 onto my laptop, a Compaq Presario. I have an installation cd but when i put it in it and tell it to install ubuntu to my computer, 2 errors come up. the one im concerned about says something about how i need to go linuxwireless.org and download firmware version 3. The message appears so fast however i can not get the whole url. Further,when i did find that information, how would i get that information into my installation?? Any help is much appreciated.. Sorry for my newbie questions haha

---

### Post by Helios1276 on 2008-10-08
Ok, I don't know much about Linuxwireless.org or a firmware upgrade:confused:..I would say burn another disc slowly ( x8 ) and try again. Unless this is some sort of obfuscated advertisement for that website?:)

---

### Post by Nxion on 2008-10-08
> **a12r13a90 said:**
> Im trying to install Ubuntu 8.04 onto my laptop, a Compaq Presario. I have an installation cd but when i put it in it and tell it to install ubuntu to my computer, 2 errors come up. the one im concerned about says something about how i need to go linuxwireless.org and download firmware version 3. The message appears so fast however i can not get the whole url. Further,when i did find that information, how would i get that information into my installation?? Any help is much appreciated.. Sorry for my newbie questions haha


Do you know what kind of wireless card it is?

---

### Post by bodhi.zazen on 2008-10-08
Does the wireless card work ?

If not , you can see the messages as they are stored in your logs.

```
gksu gedit /var/log/dmesg
```

[http://www.foogazi.com/2008/06/07/quickzi-how-to-log-boot-messages-in-ubuntu/](http://www.foogazi.com/2008/06/07/quickzi-how-to-log-boot-messages-in-ubuntu/)

[http://www.go2linux.org/bootlogd-to-read-boot-console-messages](http://www.go2linux.org/bootlogd-to-read-boot-console-messages)

[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by a12r13a90 on 2008-10-09
the wireless card is a HP WLAN 54g W450 Network Adapter..
i dont know if that helps and all the suggestions are greatly appreciated but im still tying to figure this out..

---

### Post by Big_Kahunaca on 2008-10-09
Can you boot into the LiveCD?

If so can you open a command prompt and type "lspci" then post what it comes up with.

---

### Post by a12r13a90 on 2008-10-09
all right i will do that and then post my results in just a few minutes

---

### Post by a12r13a90 on 2008-10-09
al right i tried booting ubuntu from the cd and the only thing that is happening is 1st i get the same error messages and then it boots to the ubuntu desktop but it is blank,.. there is no installation icon. Im thnkin that i am gonna hafta change the boot options straight from the installation menu. I have tried booting with all of the options when i press F6 on the menu. Does anyone know what i have type in on the boot options in order for it to find my wireless card.. Again everyones help is greatly appreciated!!

---

