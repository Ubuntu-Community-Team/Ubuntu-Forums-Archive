---
title: "Application runs fine from the IDE but when run from the exe, the app crashes"
date: 2013-06-11
forum: Packaging and Compiling Programs
---

### Post by nasdaqtr on 2013-06-11
Hi, I have an app that picks up data from txt files through a GTK interface. The app runs fine from netbeans but when the compiled App is run, the GTK interface comes up, and then the app crashes.

Any help will be highly appreciated.

Thanks.

---

### Post by QIII on 2013-06-11
Hello!

What language?

Are you running this from the terminal?

Do you get any messages?


Thanks

---

### Post by nasdaqtr on 2013-06-11
Hi,

Its developed in C++ using Netbeans I am running it from a GTK+ interface. I do not get any messages, the GTK GUI just disappears.

---

### Post by QIII on 2013-06-11
Are you starting it from the terminal?

---

### Post by nasdaqtr on 2013-06-11
No, I double click on the GTK to run it from.

---

### Post by QIII on 2013-06-11
You might try to run it from the terminal to see if you get any messages.

---

### Post by nasdaqtr on 2013-06-11
Interesting thing is that on some machines the exe runs, but on other machines the exe does not run, all those machine are running Ubuntu 12.04. When I tried to run it from the terminal, the GTK interface came up and again when I load a certain text file containing some initialization variables the app crashes. The interface always comes up, it only crashes on some machines when you load up those configuration files. Thanks for your help and insight.

---

### Post by nasdaqtr on 2013-06-11
I get the following on one machine when i loaded the configuration file, " " terminate called after throwing an instance of "std::out of range" what () vector::M_range_check""

---

### Post by QIII on 2013-06-11
Are you reading anything into an array, like from your config file?

Is the array appropriately sized?

Are you traversing the array in such a manner that you go beyond the subscript range, such as searching for substrings?

32/64 bit issues?

---

### Post by nasdaqtr on 2013-06-11
Yes I am reading from an array. But I have checked through that code several times and find that it is water tight. I have gotten it audited by a senior colleague as well. And the code runs well on the same machine from the IDE in Netbeans. It is only when I run on exe, the GTK window comes up, and then while loading up the same files that were fine when being loaded from the IDE cause a crash. Do you suggest slecting the 64-bit option when compiling from Netbeans since I currently have it on default.

---

### Post by lisati on 2013-06-11
Sometimes errors are subtle. Are you using absolute file names to locate the config file(s) or are you doing something trying to figure out the proper location from argv[0]?

---

### Post by QIII on 2013-06-11
Depends on what it will be running on.

It still really sounds to me that something is causing the code to run out of bounds of an array.  Do you have a test harness built so that you can vary inputs and test boundary conditions and such?

What was your testing methodology?  Did you "see if it works" or "try to break it"?

Edit -- lisati caught something I missed and I had to read back through the thread.  Depending on where and how to are catching exceptions, that error may be a red herring.  Make sure you have the path right.  If it is not running on ANY other machine, that may be it.

---

### Post by nasdaqtr on 2013-06-11
I have absolute file names but here is an interesting part..on some machines I have to have the complete filename with extension such as MyParameters.txt. The Window pops up from the exe. on other machines, I have had to cut out the extension .txt to have the exe pop up window, otherwise there is no response.

---

### Post by nasdaqtr on 2013-06-11
Apologies for a duplicate reply. My path is the folder I am running the exe from.

---

### Post by QIII on 2013-06-11
So, is that behavior consistent between OSes?

I.e.: On Ubuntu you have to have it one way and Fedora the other?


(BTW:  Are you checking for the existence of the file before you try to read from it and handling a "file not found" exception gracefully?)

---

### Post by nasdaqtr on 2013-06-11
I have only used Ubuntu..that is the target OS.

---

### Post by QIII on 2013-06-11
In general, C++ doesn't give a hoot about file extensions.  It should be able to find foo as easily as bar.txt.  Of course foo is not the same ast foo.txt.

I don't believe I have ever run across something like this.

---

