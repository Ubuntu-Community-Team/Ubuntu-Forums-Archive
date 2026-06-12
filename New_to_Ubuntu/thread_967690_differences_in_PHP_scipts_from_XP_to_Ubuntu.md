---
title: "differences in PHP scipts from XP to Ubuntu"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-11-02
Hello,

I am new to Ubuntu, I am trying to change my working Web server and Web application from a Windows XP sytem over to a Ubuntu LAMP server.  Does anyone know of a guide that details the differences between the PHP code from XP to UBuntu.  I keep getting all kinds of syntax code errors.  I can work through them from top to bottom of the errors and it just starts back over with different line number errors once I get to to bottom. All of this code was working under the XP/Apache server.  All help or pointers will be appreciated.

James in GA,USA

---

### Post by sheto on 2008-11-02
If you could answer my questions, I may be able to help you.
Do you have the package *php5-cli* installed? Installing it is the first step.

I don't know much about PHP, so I don't know about compiling, but I think the code should be the same.

---

### Post by Peter09 on 2008-11-02
The ones I found were in in filepaths with / and \ and also the fact that Linux is case sensitive, so again filenames etc need to be correct.

---

### Post by jasonlfunk on 2008-11-02
also make sure you are running the same version of php on both servers. If you were running php4 on your XP machine and php5 on your new machine, that may cause some issues as well.

---

### Post by JKHinton CPBD on 2008-11-02
Hello Sheto,Peter09 & Jasonlfunk,

Thank you all for your responses.  I did not have PHP5-cli installed in either my Xubuntu laptop or Kubuntu desktop but I installed it in both and still have the same error codes in both. I will go back and check my / \ file paths and the case of each of the files and code to match.  I am running PHP5 in all of my systems.  Anything else ya'll know of to check?


Thanks again,

James in GA,USA

---

