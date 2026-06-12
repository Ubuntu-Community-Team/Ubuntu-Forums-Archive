---
title: "need help blacklisting  still A noob"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by ontherooftop on 2008-06-17
I dont know what this is but I have to do this , here it is.

 If you have the file rtl8187.ko in the /lib/modules directory tree then you have two options to blacklist it. Failure to do this will mean that the ieee80211 r8187 module described on this page will fail to work properly. Here are the options:

    *
      Move the file to another area on your system as follows then do “depmod -ae”. Move /lib/modules/k#/kernel/drivers/net/wireless/mac80211/rtl818x/rtl8187.ko to a safe place. The “k#” and/or other parts of the path will be different for your distribution/system. Use “locate 8187.ko” or “find /lib/modules -name *8187*” to find the full path. After moving it, do “depmod -ae”.
    *
      Edit /etc/modprobe.d/blacklist and add “blacklist rtl8187” as a new line.

In both cases, reboot your system afterwards.
 


can anyone tell me what to do to blacklist this , in terminal or
any other ways , thanks.

---

### Post by pytheas22 on 2008-06-17
Sure, it's actually a lot easier than you might think.  As the second option says, you just need to add the module to the list of modules that are blacklisted.  So open the blacklist:
```

sudo gedit /etc/modprobe.d/blacklist
```

and add to the bottom of the file this line:
```

blacklist rtl8187
```

Or if you just want to run a command to automatically edit the file, you could run:
```

sudo -s
echo "blacklist rtl8187" >> /etc/modprobe.d/blacklist
```

which will append the line you need (>> means append to file).

---

