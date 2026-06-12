---
title: "dpkg was interrupted"
date: 2014-08-07
forum: New to Ubuntu
---

### Post by okkie on 2014-08-07
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

halfway through installing the wine program I got this message above. Computer now frosen sort of. Any help pse

---

### Post by QIII on 2014-08-07
Hello!

Could you give us a better description of "frozen sort of"?

Did you try to run the command suggested?

---

### Post by okkie on 2014-08-08
to run this command I need super user privilages' dpkg --configure -a'
If I cannot run dpkg --configure -a on my own computer after I was instructed to do so,I consider that sort of frozen as I can do nothing.
I have in many years also not seen the word 'superuser' anywhere.
I have just installed 14.04.1 and am busy preparing the computer to suit my needs.
I need wine and it is in the suppositories.I have used it for years.If I must not use it, please tell me so and also how to become a superuser.
Thks

---

### Post by okkie on 2014-08-08
ps
The computer is not frozen completely,I have access to everything exept at this stage to install wine ,problems installing google earth and I am sure a few more to come, but that is all part of the game. sorry for the misunderstanding

---

### Post by claracc on 2014-08-08
I suposse it refers to run the command , i.e.:

```
sudo dpkg --configure -a
```, you will be asked by your pass, enter it and it is all.

Please see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by okkie on 2014-08-08
thanks a lot, problem solved

          SOLVED

---

### Post by claracc on 2014-08-08
You are very welcome.

Glad you got fixed your problem.

As problem is solved please, mark the thread as solved but with "thread tools" menu in the right upper part of the web page.

Thanks.

---

