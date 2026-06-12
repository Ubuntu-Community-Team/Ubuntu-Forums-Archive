---
title: "How do I install 32bit versions of the following?"
date: 2014-11-05
forum: New to Ubuntu
---

### Post by Gloris_Ian on 2014-11-05
I need to install the following libraries in their 32-bit version but the issue here is that I cannot find them anywhere? I need this so I can run SPSS 21 (legal version). They told me so, otherwise it won't work.      compat-libstdc++-33-3.2.3-61     compat-db-4.2.52-5.1     libXp-1.0.0-8     libXmu-1.0.2-5     libXtst-1.0.1-3.1     pam-0.99.6.2-3.26.el5     libXft-2.1.10-1.1  I'm totally confused with this (nothing new with me :P )

---

### Post by Mark Phelps on 2014-11-05
According to the WineHQ database, SPSS v20 is rated GARBAGE -- meaning, it won't work no matter what you do:  [https://appdb.winehq.org/objectManager.php?sClass=version&iId=27695&iTestingId=83832]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=27695&iTestingId=83832")

Unless they did something really different in version 21, you are likely to encounter the same problems.

---

### Post by Gloris_Ian on 2014-11-05
Hi ubuntu addict! Well this is actually a version 21 for linux, they changed my license upon my request. It's supposed to work but installer won't start because of the missing above files. They are needed for installer gui.

---

### Post by oldfred on 2014-11-05
Have you tried PSPP, it is in repository? Or do you have to have SPSS?
I have not used either, so it is just a suggestion.

PSPP is a program for statistical analysis of sampled data. It is a free
replacement for the proprietary program SPSS.

---

### Post by Gloris_Ian on 2014-11-05
Hey olfred! My predicament is somewhat complicated. I'm writing a PhD for which I need the following analysis: mancova, manova and discriminant (linear). I have tried PSPP and to my knowledge it has only Manova out of those analyses. I know SPSS best, used some other statistical software but not many are that intuitive and it works for me. SPSS supports all three. The only reason I'd not move to linux was because of that but I was hoping I could make it work with wine, or install a linux version, so far nothing is working. Might as well configure a dual-boot with windows 7. The option of buying another software is out of the question, I could barely afford SPSS (lol). Also there is the option to use R, but then I need to learn it, and the learning curve is quite steep and requires a lot of time which I'd rather invest in my thesis. But thank you for your warm suggestion, it is indeed welcome! =)

---

### Post by mc4man on 2014-11-05
All of those packages are .rpm's for redhat/fedora & maybe Scientific Linux (and fairly old at that, 6-7 years.
I doubt at this point you'll find any .deb's that will work on Ubuntu.

---

### Post by monkeybrain20122 on 2014-11-05
> **Mark Phelps said:**
> According to the WineHQ database, SPSS v20 is rated GARBAGE -- meaning, it won't work no matter what you do:  [https://appdb.winehq.org/objectManager.php?sClass=version&iId=27695&iTestingId=83832](https://appdb.winehq.org/objectManager.php?sClass=version&iId=27695&iTestingId=83832)

Unless they did something really different in version 21, you are likely to encounter the same problems.

SPSS runs natively on Linux. It has been rewritten in java to be crossed platform since IBM purchased it around 2006. But as mc4man said the libraries are pretty old. Maybe newer versions would work, or maybe OP needs something like CentOS or Scientific Linux which provide pretty old libraries. 

I was able to install SPSS 20 32 bit on Fedora 20 64 bit for someone, but I don't remember having to hunt for old libraries, IIRC I just ran the installer and looked for error messages then installed the missing prerequisites from yum (didn't work on Ubuntu 13.10 because of some missing libraries needed for the gui or something like that)

---

### Post by Gloris_Ian on 2014-11-06
Hey mc4man and monkeybrain20122! Thanks for reply!

Mc4man, I managed to get a workaround the issue. I tried stata 13 windows version (x64) with wine, and if anyone else is interested I filed a report on it on the wine native site. It actually runs without any issues whatsoever on my ubuntu 14.04, also, it has all of SPSS analyses plus much much more. Of course, I cannot afford it and it's a trial version of sorts, so I am considering learning R at this point, since I'd rather not mess with dual-booting.

Monkeybrain20122, I actualyl tried all versions of SPSS from the newest (22) all the way to 16, both 32 bit and 64 bit and couldn't get any of them to work, there was always some issue. Anyways, the bottom line for anyone needing complex statistics on linux: use either stata with wine or learn R.

Thanks for your suggestions and advices! :)

---

### Post by mastablasta on 2014-11-06
but wouldn't it work if one added missing libraries in the program's directory (after hunting them down of course)

---

### Post by Gloris_Ian on 2014-11-06
> **mastablasta said:**
> but wouldn't it work if one added missing libraries in the program's directory (after hunting them down of course)

Well, now you got me thinking, that could work I guess, I'm no expert. But I have no idea where to get those things mentioned in the first post. Tried googling it but couldn't find them.

---

### Post by monkeybrain20122 on 2014-11-06
Actually, stata also works natively in Linux so you don't need wine if you get the Linux version.

Now since you are learning a new package anyway I would suggest may be take a look at R. It is by far the best IMO. It is in the repo but to get regular updates use this ppa
[https://launchpad.net/~marutter/+archive/ubuntu/rrutter](https://launchpad.net/~marutter/+archive/ubuntu/rrutter)

---

### Post by Gloris_Ian on 2014-11-06
> **monkeybrain20122 said:**
> Actually, stata also works natively in Linux so you don't need wine if you get the Linux version.

Now since you are learning a new package anyway I would suggest may be take a look at R. It is by far the best IMO. It is in the repo but to get regular updates use this ppa
[https://launchpad.net/~marutter/+archive/ubuntu/rrutter](https://launchpad.net/~marutter/+archive/ubuntu/rrutter)

Thanks a LOT mate! I am just starting with R, I like the idea, even thogh I am intimidated by the complexity and learning urve. Borrowed "R in action" book. Quite noob-friendly. Could you PM me some other useful books, articles, sites and such regarding R for newcomers? Thanks anyways! :)

---

### Post by whitesmith on 2014-11-06
Have you thought about virtualizing it? I've had good luck with VirtualBox (plus the proprietary USB extension when required). VB seems a natural when you're working with a 64-bit box, but want to run 32-bit SW. It costs nothing to try! Cheers.

---

### Post by Gloris_Ian on 2014-11-07
Gonna try it later today. THanks mate! :)

---

### Post by monkeybrain20122 on 2014-11-07
> **Gloris_Ian said:**
> Thanks a LOT mate! I am just starting with R, I like the idea, even thogh I am intimidated by the complexity and learning urve. Borrowed "R in action" book. Quite noob-friendly. Could you PM me some other useful books, articles, sites and such regarding R for newcomers? Thanks anyways! :)

Hi, 'R in Action' is definitely a good choice. You can also check out the UseR! series from Springer for more specific topics. You may be interested in the book 'R for SAS and SPSS users' in particular.

There are many online resources. UCLA has a stat site for R, SAS and SPSS, which is very helpful. Checkout the site 'Quick R', upon which 'R in Action' is based. Since unlike SPSS and SAS, R is very fast developing, new packages appear all the time, to keep you up to date to the latest development as well as finding using tutorials checkout the r-bloggers [http://www.r-bloggers.com/](http://www.r-bloggers.com/)

 If you want to more in depth coverage of R programming I would recommend Norman Matloff's 'The Art of R programming' and 'open source book on probability and statistics for computer science', the second one is free to download. Google it.

If you work with a lot SPSS data you should definitely take a look at the R package sjPlot [http://strengejacke.wordpress.com/sjplot-r-package/](http://strengejacke.wordpress.com/sjplot-r-package/)
There is also an intriguing package that converts SPSS syntax to R codes, though I have never used it
[http://www.r-bloggers.com/spss-to-r-an-r-package-to-convert-spss-syntax/](http://www.r-bloggers.com/spss-to-r-an-r-package-to-convert-spss-syntax/)

---

### Post by Gloris_Ian on 2014-11-08
> **whitesmith said:**
> Have you thought about virtualizing it? I've had good luck with VirtualBox (plus the proprietary USB extension when required). VB seems a natural when you're working with a 64-bit box, but want to run 32-bit SW. It costs nothing to try! Cheers.

Hey whitesmith! Unfortunately, running SPSS through VirtualBox crashes my system. THe screen freezes and I cannot do anything else but restart it, maybe it's because I have an old PC I'm not sure. Also tried VMWare, with it nothing happens when I start it. But thanks for your suggestions! :=)

Monkeybrain, thanks alot for your exhausting list, you seem like an R enthusiast of some sort. I'll surely give it all a try after I'm done with the first book "R in action"! Also thanks for websites! Just a question, do you consider yourself an expert or intermediate at R? Regardless of answer, please tell me how long did it took you to get there? Months? Year? Two?

---

### Post by monkeybrain20122 on 2014-11-08
Hmm... I am probably an intermediate user I guess. I haven't written any R package myself, only use what are available (and there are tons) so I am actually trying to learn to get under the hood now. It is hard to say how long it will take to learn something like this..because working through books may give you a wrong idea of what you actually know. It will be a lot more useful learning wise if you actually work on a  projects. I worked in SAS before, it was helpful for me to try to implement old macros I wrote in R (if you write syntax in SPSS you may try the same exercise. Though it seems that SPSS is more limited than SAS and R, but I could be wrong, I don't really use SPSS)

Edited: I forgot to mention that there is a nice IDE for R called Rstudio. You can download the .deb from [http://www.rstudio.com/products/rstudio/download/](http://www.rstudio.com/products/rstudio/download/)

---

### Post by monkeybrain20122 on 2014-11-08
> **Gloris_Ian said:**
> Hey whitesmith! Unfortunately, running SPSS through VirtualBox crashes my system. THe screen freezes and I cannot do anything else but restart it, maybe it's because I have an old PC I'm not sure. Also tried VMWare, with it nothing happens when I start it. But thanks for your suggestions! :=)



You need around 4 Gs of ram to use VM comfortably in my experience. But like I said SPSS runs natively in Linux. Since Redhat Linux is officially supported you may try to  make a small partition to dual boot with Centos or Scientific Linux instead of using a VM, the OS takes much less space than Windows (I was able to install SPSS 20 even in Fedora 20)

---

