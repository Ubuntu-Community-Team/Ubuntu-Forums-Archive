---
title: "KDevelop, QT3,  KDevelop Interface..."
date: 2006-09-24
forum: Programming Talk
---

### Post by elpuerco on 2006-09-24
OK I have decided to stick to my guns and go with C++ as it was a language I used in the past.

I have installed KDevelop and all related stuff thru Adept

I have installed QT3 and all related stuff thru Adept

I can open KDevelop, KDevelop Interface Designer and QT Designer IDEs

I have attempted a number of times to run the tutorial at:

[http://women.kde.org/articles/tutori...uirements.html](http://women.kde.org/articles/tutori...uirements.html)

This tutorial states running locate qstring.h should returnthe path to the file thus confirming QT3 is installed but I dont get a path returned and yet the QT Designer works?

Also trying to work thru the tutorial ignoring the qstring.h issue I notice my KDevelop IDE does not match that of the tutorial.

I get errors when I build/make/install as the tutorial says but simply execute program results in a running program?

I have now read that you can create a form in KDevelop Interface Designer and import into KDevelop.  So do I not need to use QT3?

Strangely I know how to program and years ago also was advanced in C++ using Borland under Windows, but alas I'm stumped here.

I am struggling as I dont even know if I have everyhing installed or have too much instlled?

Is it the case that I could following the tutorials here:

[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

Entering them in KDevelop and get them to work?

If it is the case that I can create forms in KDev Inter Degsigner rather than QT3 then this would I think simplify things.

Any help would be gratefully received in order for me to get up and running as so far I have spent two days just trying to figure out what IDE I should use and whether I even have it installed correctly:confused: 

I am unable to access the user manuals or help files as although Adept says the docs are installed KHE help says they are not available?
Thnx in hope.....

---

### Post by MWAAAHAAA on 2006-09-24
> 
This tutorial states running locate qstring.h should returnthe path to the file thus confirming QT3 is installed but I dont get a path returned and yet the QT Designer works?


This probably means that you have not updated your slocate databse yet to reflect the newly installed packages. Try running 'updatedb'.

> 
Also trying to work thru the tutorial ignoring the qstring.h issue I notice my KDevelop IDE does not match that of the tutorial.


How old is the tutorial? Is the version of KDE you are using the same as used in the tutorial? Also, there are different IDE modes when using kdevelop. Settings->Configure kdevelop->User interface should be helpful.

> 
I get errors when I build/make/install as the tutorial says but simply execute program results in a running program?


This is not very descriptive. What errors?

> 
Strangely I know how to program and years ago also was advanced in C++ using Borland under Windows, but alas I'm stumped here.


Knowing how to write a program and using an IDE are two completely different things. Even the compiler you are using now presumably is different as it is probably gcc and not some borland compiler you are using with kdevelop.

> 
I am struggling as I dont even know if I have everyhing installed or have too much instlled?

Again, what errors are you getting when building your program?

> 
Is it the case that I could following the tutorials here:

[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

Entering them in KDevelop and get them to work?


Sure, why not? Kdevelop is basically a front end for your compiler. If you write code that works with the compiler, it should build. This should be totally independent of kdevelop. BTW, seems like a very nice site, didn't know about it yet!

---

### Post by elpuerco on 2006-09-24
Hi, thanks for the response.

OK the updatedb resolved the locate qstring.h ;) 

How old is the program?  DOH!!!! 2004 crap sorry I did not see that :oops: 

Therefore I can ignore those errors as the tut is out of date!

I get this error when trying to access the KDevelop Handbook or the KDev Degsigner Handbook? 

There is no documentation available for /kdevdesigner/kdevdesigner.html.

I created a form.ui in KDev Designer and then opened it in KDeveloper so was pleased with that, but have not a clue what to do?

Accessing the hanbooks and an up to date tutorial would be of enormous benefit....[-o< [-o< [-o<

---

### Post by elpuerco on 2006-09-24
Can anyone help me please?

I have spent two days now simply trying to get an IDE to work let alone try to learn how to program??

I have founf part of the problkem for the KDevelop missing docs by changing the settings but cannot get the same to work for KDev Design.

I don't quite understand how the setup has not simply performed a default setup with everything working?

All I want to do is read the doc to learn how to use the apps which I cant do cos I get get the sodding docs to be located??

:confused: :confused: :confused: :confused:

---

### Post by elpuerco on 2006-09-25
:confused: :confused: :confused: 

Is there no one who can throw me a bone?

I have trolled the net and can't find how to get into the kdevdesigner handbook.

The must be some one out there who can access this through their setup and tell me the settings I need to do this?

:confused: :confused: :confused:

---

### Post by MWAAAHAAA on 2006-09-25
You might have more luck trying the programming forum.

---

### Post by elpuerco on 2006-09-25
I thought this was the Programming forum?

---

### Post by elpuerco on 2006-09-25
:KS :KS :KS :KS 

By the power of Grey Skull......Boa Constructor!

KDevelop, KDevDesigner....?? nah removed and my journey has begun with BC and Python

:KS :KS :KS :KS

---

