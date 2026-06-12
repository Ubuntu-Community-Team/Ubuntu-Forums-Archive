---
title: "unzip problem"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by martin15s on 2008-04-23
hi - absolute new beginner trying to unzip a downloaded file - seem to have followed instructions from SWORD project but cannot get it to unzip - please seeterminal dialoue below - hope I have the right place - reagards martin15s  

:martin@martin-desktop:~$ cd /usr/share/sword
martin@martin-desktop:/usr/share/sword$ unzip /home/martin/Documents/WEB.zip
Archive:  /home/martin/Documents/WEB.zip
error:  cannot create mods.d/web.conf
checkdir error:  cannot create modules/texts/ztext/web
                 unable to process modules/texts/ztext/web/ot.bzv.
checkdir error:  cannot create modules/texts/ztext/web
                 unable to process modules/texts/ztext/web/ot.bzs.
checkdir error:  cannot create modules/texts/ztext/web
                 unable to process modules/texts/ztext/web/nt.bzz.
checkdir error:  cannot create modules/texts/ztext/web
                 unable to process modules/texts/ztext/web/nt.bzv.
checkdir error:  cannot create modules/texts/ztext/web
                 unable to process modules/texts/ztext/web/ot.bzz.
checkdir error:  cannot create modules/texts/ztext/web
                 unable to process modules/texts/ztext/web/nt.bzs.
martin@martin-desktop:/usr/share/sword$

---

### Post by SunnyRabbiera on 2008-04-23
well you can just extract the zip on your own without the terminal by right clicking the zip file and selecting "extract here"

---

### Post by martin15s on 2008-04-23
hi thanks for quick reply - no go as it breaks down into 2 files -- mod.d and modules - if I try to etract them to the sword directory I get a command line error. thanks martin15s

---

### Post by Cypher on 2008-04-23
In a terminal, run the following command and show us the output
```

unipz -l /home/martin/Documents/WEB.zip

```

---

### Post by martin15s on 2008-04-23
hi - details below - thanks v much
 
martin@martin-desktop:~$ unipz -l /home/martin/Documents/WEB.zip
bash: unipz: command not found
martin@martin-desktop:~$ unzip -l /home/martin/Documents/WEB.zip
Archive:  /home/martin/Documents/WEB.zip
  Length     Date   Time    Name
 --------    ----   ----    ----
     1213  10-07-07 06:17   mods.d/web.conf
   241150  10-07-07 06:17   modules/texts/ztext/web/ot.bzv
      468  10-07-07 06:17   modules/texts/ztext/web/ot.bzs
   387640  10-07-07 06:17   modules/texts/ztext/web/nt.bzz
    82460  10-07-07 06:17   modules/texts/ztext/web/nt.bzv
  1050743  10-07-07 06:17   modules/texts/ztext/web/ot.bzz
      324  10-07-07 06:17   modules/texts/ztext/web/nt.bzs
 --------                   -------
  1763998                   7 files
martin@martin-desktop:~$

---

### Post by Cypher on 2008-04-23
Ahh..sorry, missed this intially..you are trying to uncompress this to the /usr/share directory without "sudo" Privs..

So try this
```

cd /usr/share/sword
sudo unzip /usr/home/martin/Documents/WEB.zip

```
You will enter your password when prompted and the files should extract..

---

### Post by martin15s on 2008-04-23
ok until I try to input password - then keyboard locks up.........

---

### Post by annda on 2008-04-23
does the keyboard really lock up, or can't you just see what you are typing? this is normal behavior - passwords do not appear on screen.

try typing your password and hitting enter.

---

### Post by martin15s on 2008-04-23
no - the cursor remains still when I type - when I press enter "authentication failure". Had no problems with terminal this morning - got into root ok....

---

### Post by martin15s on 2008-04-27
many thanks for all the help from a very grateful newbie - problem finally resolved with the code from Cyoher - and a corrected password - it gives me hope for my future with Ubuntu - farewell Mr Gates......

---

