---
title: "Did I Install this Program Correctly? Getting an Error"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by JessicaTsang on 2013-04-22
[FONT=Verdana, Arial, Helvetica, sans-serif]Hey there,
[/FONT]
I'm running Ubuntu 12.10 right now and I'm completely lost and I was wondering if I installed the Litecoin client correctly.

I went here: 


[https://github.com/litecoin-project/litecoin/downloads](https://github.com/litecoin-project/litecoin/downloads)

Downloaded the version for Linux and unzipped in the downloads folder. Now I found the Litecoin qt file and when I opened it, the program launched.

[FONT=Verdana, Arial, Helvetica, sans-serif]The problem is everytime I click on the program I get the message that it is not in the found in this directory; [/FONT][COLOR=#000000][FONT=verdana] /home/$user/.litecoin folder and that the program is probably already running.

How can I ensure that this is installed correctly?

Thanks~~~!![/FONT][/COLOR]

---

### Post by schragge on 2013-04-22
I presume you already have *libqtgui4* installed as it is needed to run the application. Could you please post the error message verbatim?

---

### Post by JessicaTsang on 2013-04-23
Sure, thanks for the interest.

Cannot obtain a lock on data directory /home/jessica/.litecoin
Litecoin is probably already running

---

### Post by schragge on 2013-04-23
Check that the directory exist. As this is a hidden folder, you need to press **Ctrl**+**H** in Nautilus (Ubuntu file manager) to display it.
In terminal, it can be shown with ```
ls -l ~/.litecoin
```
See [uhelp]community/UsingTheTerminal#Starting_a_Terminal[/uhelp]

---

### Post by JessicaTsang on 2013-04-25
It shows blkoo1.dat
blkindex.dat
database
db.log
debug.log
peers.dat
wallet.dat

Should I take the wallet.dat and move it to another location and encrypt it?

---

### Post by JessicaTsang on 2013-04-25
Alright, so when I moved the wallet.dat into my truecrypt folder, there is still a copy in my home folder. Do I get rid of it?

---

