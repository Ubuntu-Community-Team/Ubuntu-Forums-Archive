---
title: "[SOLVED] -i inffile ndiswrapper??"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-02
i couldnt get ndisgtk in kubuntu and i dont know how to use the 
ndiswrapper utility i did get,im not sure what to type to point
the program to where i have the net5416.inf file,can somone please
help me with this,i havent a clue
rick:confused:

---

### Post by caljohnsmith on 2008-08-02
To use ndiswrapper at the command line, make sure you first have both the .inf and .sys drivers for your wireless card in the same directory (any directory of your choosing). Then do:
```
sudo ndiswrapper -i /path_to_driver/net5416.inf
ndiswrapper -l  [this should show your driver is installed successfully]
sudo modprobe ndiswrapper
```

---

### Post by prshah on 2008-08-02
> **rixtr66 said:**
> i dont know how to use the 
ndiswrapper utility i did get,

> **caljohnsmith said:**
> 
```
sudo ndiswrapper -i /path_to_driver/net5416.inf
ndiswrapper -l  [this should show your driver is installed successfully]
sudo modprobe ndiswrapper
```

You also have to "modularize" the ndiswrapper driver, _before_ you modprobe it. So in the suggested commands above, add a command ```
sudo ndiswrapper -m
``` _before_ the modprobe command.

---

### Post by rixtr66 on 2008-08-02
the commands you gave were helpful,but i kept getting this:
couldnt open/home/net5416.inf no such file or directory
(with the sudo ndiswrapper -i)any way i downloaded the alternate
kubuntu iso and burned it at a slow speed,the desktop is different and it came with ndisgtk,so i was able to install
the ndis wrapper, works like a charm. thanks for the help!!
rick:)

---

