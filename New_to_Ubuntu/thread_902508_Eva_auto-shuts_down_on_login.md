---
title: "Eva auto-shuts down on login"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by tilai on 2008-08-27
I installed Eva QQ from the repository and on the first occasion it worked fine. However, on subsequent attempts, the program will just close down on logging in. I checked the processes on the System Monitor, and Eva just disappear each time.

The QQ account details and password remain saved when I 'uninstalled' and reinstalled through Synaptic or through Applications -> Add/Remove.

Is there a way to remove all trace of Eva? Or how to get it to work again?

---

### Post by Het Irv on 2008-08-27
You could try ```
sudo apt-get purge eva
```  Just replace eva with how the program was name, if eva doesn't work.  That should delete all files associated with the program.

---

