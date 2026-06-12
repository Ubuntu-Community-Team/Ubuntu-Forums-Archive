---
title: "Help me install the drivers for creative X-FI"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by zooLiz on 2008-05-14
Hey, I want sound on my computer and I noticed that creative had released a beta driver that I wanted to try. I did as it said and wrote ./installer in the terminal. After all the agree och text i had to scroll through it started installing. I got to this point:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Fel 2
make: *** [install] Fel 2
Installation Unsuccessful
zooliz@zooLen:~/Skrivbord/XFiDrv_Linux_US-1.18$ 
zooliz@zooLen:~/Skrivbord/XFiDrv_Linux_US-1.18$ 
zooliz@zooLen:~/Skrivbord/XFiDrv_Linux_US-1.18$ 
zooliz@zooLen:~/Skrivbord/XFiDrv_Linux_US-1.18$ 

I'm using ubuntu 8.04 if that's needed
What could this mean? Please explain how to proceed if you have any clues.

Thanks

---

### Post by shifty_powers on 2008-05-14
```
sudo ./installer
```

this gives it admin rights and the ability to create files temporarily... ;)

---

### Post by zooLiz on 2008-05-14
Ok, but why is the installation unsuccesfull? Is there anything that I could do to make it work? Maybe I'm missing some programs or drivers?

---

### Post by shifty_powers on 2008-05-14
have you tried my suggestion? if that doesn't work then get back to me ;)

---

### Post by zooLiz on 2008-05-14
You mean add sudo? Yeah I had to do that to even make it go through as long as it did.

---

### Post by shifty_powers on 2008-05-14
heh, ok.

try posting the contents of config.log

---

### Post by zooburner on 2008-05-14
HIya there

Sorry I can't help, other than to say i have exactly the same problem with the same driver.  I've tried alsorts but cannot get it working, which really is a shame as everything else seems to work right out of the box.

Perhaps its needs MB drivers (in windows the inf. files), who knows but finding useful information is very hard. 

Later im goinmg to remove my Xf1 Fatality and see if i have better luck with the on-board sound 

:0

---

### Post by shifty_powers on 2008-05-14
bad news by the looks of it.

look [http://ubuntuforums.org/showthread.php?t=571656&highlight=creative+driver](http://ubuntuforums.org/showthread.php?t=571656&highlight=creative+driver)

---

