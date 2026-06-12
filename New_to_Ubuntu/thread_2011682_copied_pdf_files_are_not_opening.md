---
title: "copied pdf files are not opening"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by mustafi05 on 2012-06-27
i have a problem. i am using precise (12.04).when i save a pdf file in home folder , i can open it. but when i copy it to a pen drive , the pdf file in the pen drive does not open any more. how should i manage this so that i can open the copied file too? thanks in advance.

---

### Post by ajgreeny on 2012-06-27
For more info on why this happens open one of the copied files on the pendrive with evince, or whatever application you are using, in terminal with command ```
evince /media/diskname/filename.pdf
``` and see if any errors appear.

---

### Post by mustafi05 on 2012-06-28
its saying '** (evince:17072): WARNING **: Error setting file metadata: No such file or directory' .  while opening with evince it is stating " error opening file : permisssion denied"

---

### Post by mustafi05 on 2012-09-16
i have sorted out the problem. actually if you remove the .pdf extension by changing the name , the pdf file opens in ubuntu when it is in hard drive. but it does not open when copied in any other media. i just put  .pdf after the name and the file opens without any problem. hope any other people facing the same problem will be benifited.

---

