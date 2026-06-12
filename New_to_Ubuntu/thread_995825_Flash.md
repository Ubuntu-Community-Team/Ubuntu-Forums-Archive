---
title: "Flash"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Flirtilizer on 2008-11-28
okay.  how do i get the flash player installed.

I'm running 7.x and don't have all the updates installed.

I need too get Gtalk working if at all possible and I keep getting message t install Flash, I did but FF doesn't seem to notice it.

I may have installed it twice, not sure.

I clicked on the installer, got a pop asking to run or to run via terminal.  First time I cliked run, didn't see anything happen. So I clicked on it again and ran in terminal and it installed.  

thanks

---

### Post by bhadotia on 2008-11-28
Type this command in the terminal (Applications>Accessories>Terminal):
```
sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

---

### Post by Flirtilizer on 2008-11-28
> **bhadotia said:**
> Type this command in the terminal (Applications>Accessories>Terminal):
```
sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

Thanks, tried and got this:

rusty@rusty:~$ sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
Password:
E: Invalid operation purge
rusty@rusty:~$

---

### Post by nothingspecial on 2008-11-28
It`s 

sudo apt-get remove --purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree

---

### Post by bhadotia on 2008-11-28
> **Flirtilizer said:**
> Thanks, tried and got this:

rusty@rusty:~$ sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
Password:
E: Invalid operation purge
rusty@rusty:~$

Alright do this:
```
sudo apt-get remove flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

---

### Post by bhadotia on 2008-11-28
> **nothingspecial said:**
> It`s 

sudo apt-get remove --purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree

In intrepid (and formerly hardy) I always do:
```
sudo apt-get purge <package>
```
to remove a package (along with config). I didn't understand why this command did not work for OP. May because he is using Gutsy.

---

### Post by Dedoimedo on 2008-11-28
Hello,

If you don't like the command line, I have a tutorial explaining several methods how to obtain flash:

[http://www.dedoimedo.com/computers/flash_firefox_linux.html](http://www.dedoimedo.com/computers/flash_firefox_linux.html)

Dedoimedo

---

