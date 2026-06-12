---
title: "Ubuntu Help"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by ken of eastriggs on 2008-08-28
Hi I am very new to Ubuntu my grey hairs match my grey cells so please be kind it takes me a long time to absorb all this tech stuff. I have loaded Ubuntu and got my email set up on Evolution and got my internet connection set up on wired and wireless. I must have done something wrong when updateing using Update Manager. I now get an error message as follows E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct the problem also E: -cache->open()failed, please report. Problem is I do not know how to either of this requests can you help.

You may need to explain in very simple terms as I do not have a great technical knoweldge ( just warning you that I am thick ). But I am a tryer.

Many many thanks in anticipation for the help regards ken of eastriggs

---

### Post by stunningman on 2008-08-28
please tell what you were updating.

---

### Post by oilchangeguy on 2008-08-28
simply open a terminal (command line) and type
sudo dpkg --configure -a and press enter.

---

### Post by ken of eastriggs on 2008-08-28
Hi Oilchangeguy, Many thanks for the help did that and all went OK but then hit further snags went wrong on choice of mysql or pgsql seems that now update manager stay on when I run it so hope that it will update if needed. Get nowhere if I chose mysql if I chose pgsql it tells me to install postgresqi before i can continue with configuration. It seems to be conected with acidbase I have no idea what acidbase is about I just OKd all the install options available.

Sorry to be a pest and many many thanks for your help I hope it is not a bore. As ever.... ken of eastriggs

---

### Post by bodhi.zazen on 2008-08-28
Try:

```
sudo apt-get update
```

Then upgrade or install away ...

---

### Post by ken of eastriggs on 2008-08-28
Hi Helpers and many thanks, I am getting to know my way around thanks to you all, it looks like i need to install postgresql and I think I need a file location after the sudo install postgresql again I dont know about file locations. Any help would be greatly appreciated. Thanks for all your patience and time.... ken of eastriggs

---

