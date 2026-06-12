---
title: "To Install Printer on Lubuntu 16.04 - Need to install CUPS"
date: 2016-05-28
forum: New to Ubuntu
---

### Post by Download_Descenden on 2016-05-28
Really a bit of information for someone new to Lubuntu - previously CUPS was pre-installed so you go into System Tools - Printers and so on. But in 16.04 you now have to install CUPS - open the terminal and then type sudo apt install cups

And now the Add box will no longer be greyed out, and there won't be a  "printing service not available. Start service on this computer or connect to another server" message.

---

### Post by oldrocker99 on 2016-05-28
Please don't use a larger font when posting; it's the equivalent of shouting,

That said, it's a good tip. I never had a problem connecting a printer myself.

---

### Post by andytv on 2016-09-14
I tryed install xerox-phaser-3010 on lubuntu16.04 .......I install cups and xerox driver from official site but printer didnt work , 

after install this everything work perfectly

sudo apt-get install libcups2:i386 libcupsfilters1:i386 libcupsimage2:i386

---

### Post by ltrtiger2 on 2016-09-16
Ran into this very issue shortly after a clean install of 16.04. CUPS was, indeed, the answer. Good tip.

---

### Post by mydailey on 2017-08-11
Thank you.

---

