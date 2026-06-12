---
title: "[SOLVED] opera 9.62. amd64...deb install fails"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by 3katie3 on 2008-11-02
I could sure use some help with installing opera browser.

i downloaded the most recent version, (hardy heron) named
opera_9.62.2466.gcc4.qt3_amd64.deb
saved in my "documents" file, and the gdeb (?) package installer popped up to install it and put it on the application/internet menu and an icon-link on desktop.

but nothing happens when i click them. 

i've removed it and reinstalled it several times.  i searched the ubuntu forums for opera.   there were some posts but they were way advanced, and didnt seem to be install problems.  at least it gave me hope that ubuntu users are able to install opera for their web browser.

i did use the properties button and enabled the "application/executable" feature.

hope there is help here.

---

### Post by brandoncolorado on 2008-11-02
> **3katie3 said:**
> I could sure use some help with installing opera browser.

i downloaded the most recent version, (hardy heron) named
opera_9.62.2466.gcc4.qt3_amd64.deb
saved in my "documents" file, and the gdeb (?) package installer popped up to install it and put it on the application/internet menu and an icon-link on desktop.

but nothing happens when i click them. 

i've removed it and reinstalled it several times.  i searched the ubuntu forums for opera.   there were some posts but they were way advanced, and didnt seem to be install problems.  at least it gave me hope that ubuntu users are able to install opera for their web browser.

i did use the properties button and enabled the "application/executable" feature.

hope there is help here.

Hi Hi,

Go to terminal:
Applications >  Accessories > Terminal

Type in:
"opera"  (without quotation marks)

Are you getting an error there?  That could help to find the problem.

---

### Post by brandoncolorado on 2008-11-02
Also, here are some great instructions:

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by 3katie3 on 2008-11-03
Hi Brandon,

gosh, your cat in the hat made me laugh.

i did what you said with the terminal and got this back:

administrator@administrator-laptop:~$ opera
/home/administrator/lib/opera/9.62/opera: 1: Syntax error: "(" unexpected
administrator@administrator-laptop:~$ 

i tried to open the opera 9.62/opera file, but i dont have any editor that i know of that will read it.  the included text processor wont, nor the office suite.

so now i'll take a look at the link you posted, and let you know what happens.

thanks so much.  really appreciate your help.

---

### Post by brandoncolorado on 2008-11-03
> **3katie3 said:**
> Hi Brandon,

gosh, your cat in the hat made me laugh.

i did what you said with the terminal and got this back:

administrator@administrator-laptop:~$ opera
/home/administrator/lib/opera/9.62/opera: 1: Syntax error: "(" unexpected
administrator@administrator-laptop:~$ 

i tried to open the opera 9.62/opera file, but i dont have any editor that i know of that will read it.  the included text processor wont, nor the office suite.

so now i'll take a look at the link you posted, and let you know what happens.

thanks so much.  really appreciate your help.

You are running a 64 bit system right?  That file is for 64 bit.  

Try the repository option from that link I sent you, but be sure to uninstall the .deb install you did first.  The repository thing is a lot easier than you would imagine.

---

### Post by 3katie3 on 2008-11-04
Hi Brandon--

the good news is that following your advice, opera is now running in Ubuntu!!!

it was eventful though--after i uninstalled the broken opera, everything froze up.  would not even reboot into ubuntu after manual shut down.   had to uninstall ubuntu, and reinstall ubuntu with Wubi-8.04.1-rev506.exe  then reinstall a fresh download of deb opera for amd64.

but it had a  happy ending.  also following your suggestion, i added the opera/linux/ubuntu repository with the apt application, and it upgraded itself by downloading about 50 files.

something i dont understand is why opera-ubuntu is having connecting problems to sites i visit all the time?  or it seems to time out.    and it seems that firefox is faster and more reliable in connecting.   

have you had that experience?    maybe i have to dink around with the configuration settings in opera.

thanks so much for your help, Brandon.   Opera is running now.  

     : )


i have more questions but the newbie guide said to keep one main idea per thread.

---

