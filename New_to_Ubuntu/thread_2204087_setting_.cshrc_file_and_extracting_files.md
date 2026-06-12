---
title: "setting .cshrc file and extracting files"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by Joana_Paulino on 2014-02-06
Problem 1) When I try to activate my .cshrc file (source .cshrc) I get the following messages

:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory.

I just have re instaled ubuntu 12.04 32 bit and created a new .cshrc file. 

Problem 2) not being able to extract .tz files. The following error pops up 'An error occurred while extracting files.' 

Any help will be welcome

thanks

---

### Post by tomearp on 2014-02-06
Can you paste the contents of the .cshrc file please?

---

### Post by Joana_Paulino on 2014-02-06
Here are the contents, it is pretty much the same of what I had before reinstaling ubuntu.
 cshrc file:
---------------------
#!/bin/csh

#
# Echo NMRPipe .cshrc commands created on Thu Feb  6 17:32:50 EST 2014
# Echo see file /home/joanapaulino/nmrpipe/README_NMRPIPE_USERS for more information.

 if (-e /home/joanapaulino/nmrpipe/com/nmrInit.linux9.com) then
    source /home/joanapaulino/nmrpipe/com/nmrInit.linux9.com
 endif

 if (-e /home/joanapaulino/nmrpipe/dynamo/com/dynInit.com) then
    source /home/joanapaulino/nmrpipe/dynamo/com/dynInit.com
 endif

 if (-e /home/joanapaulino/nmrpipe/com/font.com) then
    source /home/joanapaulino/nmrpipe/com/font.com
 endif

setenv PATH </home/joanapaulino/spinev>:${PATH}
setenv SPINEV </home/joanapaulino/spinev>

alias nmrDraw 'nmrDraw &'
alias bruker 'bruker &'
alias varian 'varian &'
------------------------------------------------
Thanks

---

### Post by tomearp on 2014-02-06
I would say try removing the < and > characters from around </home/joanapaulino/spinev>

---

### Post by brokenhachi on 2014-02-06
what command/options are you using to untar? I think you need to use gunzip to untar a .tz file ```
gunzip file.tz | tar -xzvf -
```

---

### Post by oldrocker99 on 2014-02-06
I've sometimes had problems untaring a file, but file-roller almost always works, for what it's worth.

---

### Post by Joana_Paulino on 2014-02-06
Thanks you so much guys!!! All problems solved =)

---

