---
title: "Noob question: Tarball from Sourceforge"
date: 2012-05-14
forum: Packaging and Compiling Programs
---

### Post by jhargis1012 on 2012-05-14
Hello all.

I am taking a Java course and am pretty new to programming (and Linux, for that matter).

I was looking around for some sample games in Java to tinker with them, and came across this page: [http://creepsmash.svn.sourceforge.net/](http://creepsmash.svn.sourceforge.net/)

I clicked the "Download GNU Tarball" link. I downloaded the tarball, and now I have no idea what to do with it. I'm hoping to be able to open this game up in Eclipse and take a look at the code.

Thanks for any help or suggestions!

---

### Post by matt_symes on 2012-05-14
Hi

You need to unpack it.


Open a terminal, navigate to the directory you downloaded it to, and type


```
tar -xvf creepsmash.tar.gz
```


That will create a directory wher it will be unzipped to called creepsmash


You can also use tool in the GUI as well.


Kind regards

---

### Post by jhargis1012 on 2012-05-15
Excellent, thank you.

Now that I've done that, is there a way to import the entire application into Eclipse to view and edit the code? I flipped through the folders and I see lots of different Java classes. Are they meant to be viewed individually or is there some kind of overarching application in there somewhere that calls to the individual classes?

Thanks in advance.

---

### Post by matt_symes on 2012-05-15
Hi

You can import them into eclipse or copy the source directory to the src directory in your workspace then refresh. I have not had a good look at the source.

I don't like eclipse as an IDE and it has been a good while since i have (had to) use(d) it. :P

As i suspect my knowledge of eclipse is out of date, I suggest reading this

[http://www.eclipse.org/documentation/](http://www.eclipse.org/documentation/)

Kind regards

---

### Post by jhargis1012 on 2012-05-15
Thank you, that is helpful.

---

