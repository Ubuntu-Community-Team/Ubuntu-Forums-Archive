---
title: "Eclipse CDT Troubles"
date: 2010-01-09
forum: Programming Talk
---

### Post by eewoz on 2010-01-09
I am running Eclipse CDT that I installed using Ubuntu Software Center.  When I make a simple Hello World program I get an error message saying ```
undefined reference to `main' 
```

If I add the canned C Hello World project to the workspace I still have the same problem.  But if I add the canned C++ Hello World project to the workspace the Hello World program that I wrote will then compile and run without any issues.


I also have Eclipse installed in a folder in my home directory that was made from a download from the Eclipse website.  This version does not have this problem but I can only create projects when I run this version of Eclipse as root.


Are issues like this par for the course with Eclipse and Ubuntu?  This is very discouraging.  Does anyone have any ideas what is going on?

Thanks.

---

### Post by not_a_phd on 2010-01-10
> **eewoz said:**
> 
Are issues like this par for the course with Eclipse and Ubuntu?  This is very discouraging.  Does anyone have any ideas what is going on?
Thanks.


Interesting. I have encountered the same error message when demonstrating eclipse with a hello app. The cause (for me) was not saving the new source file prior to building. 

What is more troubling is your description of not being able to run eclipse except in root. I run a downloaded install from my home directory in Karmic, and have no difficulties (except making the java buttons work in gnome - see other eclipse threads in this forum for the fix). I don't see why you should need root privileges *unless* your workspace directories are outside of your home directories.

To answer your last question: I think that issues like this are par for the course with eclipse. I will not say eclipse+ubuntu, just eclipse. I have run eclipse in windows with similar quirks, and know a colleague that runs  it in centOS with similar results.

I have generally had success working with eclipse by observing the following:
1. I do not use eclipse from the repositories. I work off of an install from my home directory, and regularly pull the nightly build off of the eclipse download site.I

2. I heavily rely on this forum when I can't get through a problem!

---

### Post by eewoz on 2010-01-10
> **not_a_phd said:**
> 

What is more troubling is your description of not being able to run eclipse except in root. I run a downloaded install from my home directory in Karmic, and have no difficulties (except making the java buttons work in gnome - see other eclipse threads in this forum for the fix). I don't see why you should need root privileges *unless* your workspace directories are outside of your home directories.



I gave a weak description of what was happening with the downloaded version of Eclipse.  I have the same problem you described with the java buttons but only when I run Eclipse as a user.  When I run it as root I do not have the java button problem.  I have since gotten up to speed on how to fix and/or get around the java button problem.  

Do you find this forum more helpful for these sorts of problems compared to the Eclipse forums?  That has been the case for me.

---

### Post by not_a_phd on 2010-01-11
> **eewoz said:**
> Do you find this forum more helpful for these sorts of problems compared to the Eclipse forums?  That has been the case for me.

Yes I do. Go Brown!!

---

