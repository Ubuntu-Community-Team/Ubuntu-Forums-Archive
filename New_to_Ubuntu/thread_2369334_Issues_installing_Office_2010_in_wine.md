---
title: "Issues installing Office 2010 in wine"
date: 2017-08-21
forum: New to Ubuntu
---

### Post by twostops on 2017-08-21
Can someone please point me in the right direction for an answer to a communication error when trying to install MS Office

---

### Post by vocx on 2017-08-21
> **twostops said:**
> Can someone please point me in the right direction for an answer to a communication error when trying to install MS Office
Unfortunately Wine will never be able to simulate the Windows environment perfectly, so I would not count on it being able to handle a big collection of programs like MS Office.

My honest opinion is to only use Wine to install relatively small and simple programs, not big and complicated ones like Office.

You would have less problems using the LibreOffice alternative, or running the MS Office program inside a virtual machine with a virtual Windows installed. I'd rather use a virtual machine than try to deal with Wine for big programs.

Check the WineHQ to see which version of Office more or less works with which version of Wine, if you want to troubleshoot further.
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=31](https://appdb.winehq.org/objectManager.php?sClass=application&iId=31)
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=10](https://appdb.winehq.org/objectManager.php?sClass=application&iId=10)

---

### Post by QIII on 2017-08-21
Hello!

Would you please post the full text of the error message?  How exactly are you trying to install Office?

Thanks.

---

### Post by mastablasta on 2017-08-22
try installing it using playonlinux. it should work just fine.

Powerpoint, Word, Excel work ok, but others such as outlook , access etc. might have issues. 

for best results use the 32 bit version of office. if you have 64 bit OS you need to set up 32bit wine prefix.

---

