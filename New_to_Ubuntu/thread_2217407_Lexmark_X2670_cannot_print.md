---
title: "Lexmark X2670 cannot print"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by ali2013 on 2014-04-17
OK, I just installed Ubuntu last version and I have a Lexmark printer X2670 which is a paperweight according to Openprinting. There is no driver as well for it on Lexmark page. I want to know if there is any possible way to make it work so that I can print?

---

### Post by Canterwood on 2014-04-17
[This thread]("http://ubuntuforums.org/showthread.php?t=1371708&page=2") may help you, but as I understand from the following quote:

"Thank you for contacting Lexmark Technical Support. I really do apologize for the inconvenience you have in getting this printer to work on your 64 bit machine. I understand and appreciate your desire for 64 bit Linux driver but as of now we still don't have 64 bit Linux driver available. Thank you for notifying us of your concern. I will forward your request on to our development department, as it is only through input from you, our customers, that we can make these important business decisions.

If you have any more questions or concerns, please contact me at your convenience and I will be happy to assist you. (If I am not available, another representative may reply to your request.)"

Lexmark is basically giving 64-bit Linux users the middle finger for this driver. I checked out the [Lexmark support page]("http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_X2670&page=product&frompage=null#1") for this model and even Windows drivers are not available as of this moment. I'm afraid Openprinting is right, it seems your printer has been reduced to a paperweight.

You might be able to find the lexmark-inkjet-08-driver-1.0-1.i386.deb package mentioned in the thread above hiding somewhere on the web, but it was meant for Ubuntu 8.04 32-bit so there's absolutely no guarantee it'll work.

UPDATE: Googled some for you, that package can be found [here]("http://support.lexmark.com/index?docLocale=en_US&page=content&id=DR860&locale=EN&userlocale=EN_US").

---

### Post by ali2013 on 2014-04-17
I have a 32 bit

---

### Post by Canterwood on 2014-04-17
I'm sorry I assumed you have a 64 bit version.

---

