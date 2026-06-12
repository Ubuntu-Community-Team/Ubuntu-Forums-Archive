---
title: "Using KPPP to set up dialup connection in Ubuntu 11.10"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by DankVantam on 2011-11-11
I have set up Ubuntu 11.10 on an old desktop for my Aunt and am trying to get dialup set up using KPPP.  According to the directions provided by the ISP, setup using KPPP is supposed to be easy.  However, I am able to set up the connection just fine until I get to the tab on the GUI where I am supposed to enter DNS information.  According to the instructions, I am supposed to be able to select Automatic configuration but that option is greyed out.  
 
I should also mention that this was formerly a Windows Vista machine and I am attempting to use the PCI modem that came with it.  I have a USB dialup modem that I purchased and can use if need be but I'd like to use the existing modem if it will work.  Being a complete Ubuntu newbie, I don't know how to check to see if Ubuntu even recognizes the modem.
 
If anyone can help me get dialup set up on Ubuntu 11.10 using any tool that will be easy for my computer-illiterate Aunt to use, I would very much appreciate it.

---

### Post by Rodney9 on 2011-11-11
This site may be of help - [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

### Post by jtarin on 2011-11-11
To see if your PCI modem is detected by the system issue the command ```
lspci
``` in a terminal and look at the output.

---

### Post by DankVantam on 2011-11-14
Thanks.  I'll give that a try.

---

### Post by DankVantam on 2011-11-14
Thank you.  I already know that some of those options won't work for me but there are some that I haven't tried yet.

---

### Post by lkraemer on 2011-11-17
The best thing to do is purchase an External Hardware Modem and use
wvdial to get it working before using a GUI for the Modem.  

But, if you want to try the the PCI WinModem go to [www.linmodems.org](www.linmodems.org) and
download their script.  Then send Marvin and those fine folks the results
in PLAIN TEXT.  They will gladly tell you what is needed to get the modem working, if it is possible.

You could also have a look inside the Computer and then search their archives for information on that Make & Model.

If you don't have a Dialup Provider, I'd suggest [www.Copper.net](www.Copper.net).

If you want an old guide I've posted:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)
Posting #4

lk

---

### Post by DankVantam on 2011-12-16
> **lkraemer said:**
> The best thing to do is purchase an External Hardware Modem and use
wvdial to get it working before using a GUI for the Modem.  

But, if you want to try the the PCI WinModem go to [www.linmodems.org](www.linmodems.org) and
download their script.  Then send Marvin and those fine folks the results
in PLAIN TEXT.  They will gladly tell you what is needed to get the modem working, if it is possible.

You could also have a look inside the Computer and then search their archives for information on that Make & Model.

If you don't have a Dialup Provider, I'd suggest [www.Copper.net](www.Copper.net).

If you want an old guide I've posted:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)
Posting #4

lk
lk,

Thank you very much for your detailed reply.  I went with an external modem and getting closer but it still kicks me out after about 2 seconds with exit code 19.  I think that it is because I do not have chap secrets configured correctly.  I will print out as much as I can from your guide and bring it with me when I try again for the 5th time.

Derrick

---

