---
title: "[Python] Plotting package"
date: 2008-11-11
forum: Programming Talk
---

### Post by elbarto_87 on 2008-11-11
Hi,

Just wondering what you guys have been using for plotting in python. I have tried a bit with matplotlib, but it seems to be a little unstable for my liking, I tend to get runtime errors (on XP) when trying to close plot windows etc. I wasn't able to get matplotlib to work at all under my ubuntu idle install. I have heard a few things about gnuplot, how does it compare?

If there is anyone out there using matplotlib without any issues I would appreciate it if you could tell me what setup you are running.

Thanks
Elbarto

---

### Post by Bichromat on 2008-11-11
> **elbarto_87 said:**
> Hi,

Just wondering what you guys have been using for plotting in python. I have tried a bit with matplotlib, but it seems to be a little unstable for my liking, I tend to get runtime errors (on XP) when trying to close plot windows etc. I wasn't able to get matplotlib to work at all under my ubuntu idle install. I have heard a few things about gnuplot, how does it compare?

If there is anyone out there using matplotlib without any issues I would appreciate it if you could tell me what setup you are running.

Thanks
Elbarto

What version of matplotlib are you using? I've run into problems with the 0.91 (Hardy) but the 0.90 (Gutsy) worked fine.

---

### Post by elbarto_87 on 2008-11-11
I am using Python 2.5 matplotlib-0.98.3. Is there an archive of older versions of matplotlib I can get my hands on. I couldn't find a link on sourceforge.

Elbarto

---

### Post by Gilabuugs on 2008-11-11
matplotlib seems to work well for me in hardy

but for gnuplot you can always save files and plot data

[http://t16web.lanl.gov/Kawano/gnuplot/datafile-e.html](http://t16web.lanl.gov/Kawano/gnuplot/datafile-e.html)

but I believe there is a python library for gnuplot, although I haven't tried that, if matplotlib continues to not work

---

### Post by Bichromat on 2008-11-12
> **elbarto_87 said:**
> I am using Python 2.5 matplotlib-0.98.3. Is there an archive of older versions of matplotlib I can get my hands on. I couldn't find a link on sourceforge.

Elbarto

I found that:
[http://sourceforge.net/project/showfiles.php?group_id=80706&package_id=82474](http://sourceforge.net/project/showfiles.php?group_id=80706&package_id=82474)

---

### Post by Luggy on 2008-11-12
I've heard and briefly used [SciPy]("http://www.scipy.org/") and [NumPy]("http://numpy.scipy.org/"). They seem like have decent python libraries for doing matlab style array math and presentation.

---

### Post by elbarto_87 on 2008-11-12
@Bichromat:
Thanks for that link, I have just downloaded a few different versions and I will see how they compare with the current version I am using.

@Luggy:
I have primarily used Matlab in the past, so I have been trying to learn how to do similar tasks in python. Numpy is an excellent module for matrix and array operations. Once I learn more about the python language itself (ie classes etc) I will be able to test it out a bit more thoroughly. I have tried octave scilab etc, and in my opinion I think python with the appropriate modules would probably be the most powerful open source scientific computing package to replace my needs in matlab.

Also, a little off topic but worth a mention, are there many users on this forum that are familiar with Matlab? I am writing a thesis in Matlab and have found that it is far less community supported than languages like python etc.

Elbarto

---

