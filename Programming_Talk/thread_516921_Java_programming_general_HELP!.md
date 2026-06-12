---
title: "Java programming general HELP!"
date: 2007-08-03
forum: Programming Talk
---

### Post by ICU2 on 2007-08-03
I've been programming java apps in windows, with sockets, GUIs, JNI, RMI, etc, etc, etc.
The point is that i'm recently beginning to do this in linux, I've been using Ubuntu since 5.10 an never tried to do java before in here, so my question is: is there a good tutorial , or comparison on the little deferences in java/windows and java/linux?

BTW i've already have everything running an programming in java, but every now and then i have little drawbacks an have to search for every specific problem.

So really my question is: Has someone already wrote about these little differences?

---

### Post by kknd on 2007-08-03
Is exactly the same thing. Just the print doesn't work good, and JMF (like in windows) sucks.

---

### Post by nitro_n2o on 2007-08-03
well.. java is a cross platform language for the most part.. there is no need to worry about these little glitches.. 
minor differences might happen in GUI's depending on your desktop manager.. but you shouldn't worry about them a lot even for commercial stuff

---

### Post by AlexThomson_NZ on 2007-08-03
We have a good mix of Apple, Windows, Solaris and Linux boxes at work (doing Java development), and other than file paths, we have not really found any changes we have to make between environments (even with GUI widgets)

---

### Post by slavik on 2007-08-04
Java = write once, debug everywhere :P

if you code runs on Sun's JVM in windows, it shouldn't have a problem with Sun's JVM in Linux ... as for file paths, Java is supposed to handle the slashes properly, and you should use relative paths anyway (unless you are trying to access some exact system file or such in which case this discussion is worthless).

---

### Post by Lux Perpetua on 2007-08-04
I agree with the above posters. However, make sure you install and use Sun's virtual machine. The default is the GNU Java platform, which will not perform as you expect.

---

### Post by apoth on 2007-08-04
> **slavik said:**
> Java is supposed to handle the slashes properly.

Sort of, calling System.getProperty("file.separator") will return the appropriate slash for the OS you're running on.

Things are broadly, if not totally, the same for core Java stuff as long as you use things like the file.separator property and don't hardcode it and you use the standard Java look and feel.

---

### Post by tenmillionmilesaway on 2007-08-04
I find its easier to use the static method on the file class File.separator()

---

### Post by steve.horsley on 2007-08-05
Another important area is that of character encoding. Always make sure you specify the encoding when reading/writing text to/from input/output streams. This goes for both files and for socket streams. Especially socket streams. InputStreamReader/OutputStreamWriter use the default platform encoding unless told otherwise, and this is different between Windows (proprietary windows encoding) and Linux (somethimes UTF8, sometimes 8059-1).

---

### Post by hesham87 on 2007-08-05
People the man is trying to get atutorial or somthing to java programming in linux any help ?
iam in asame like him and i even try to use eclipse in linux but i cant work well in it

---

### Post by Ramses de Norre on 2007-08-05
Looking for a [tutorial](http://java.sun.com/docs/books/tutorial/index.html)?

---

### Post by AlexThomson_NZ on 2007-08-05
> **hesham87 said:**
> People the man is trying to get atutorial or somthing to java programming in linux any help ?
iam in asame like him and i even try to use eclipse in linux but i cant work well in it

The point we were making is there is are no real differences at all, hence there probably isn't any online comparisons (not that I bothered checking).  I don't think he is looking help actually programming Java, as it looks like he has done quite a bit already.

If you are having problems with Eclipse, start a new tread and detail your specific problems

---

