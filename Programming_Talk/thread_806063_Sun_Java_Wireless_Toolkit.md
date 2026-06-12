---
title: "Sun Java Wireless Toolkit"
date: 2008-05-24
forum: Programming Talk
---

### Post by petermp on 2008-05-24
Hi,

I have just switched from Vista to Ubuntu 8.04, and when I try to emulate a j2me application I get an exception.

The first time I start the application (with no ~/j2mewtk/ folder) the following exception is casted:

```
Running with storage root ~/j2mewtk/2.5.2/appdb/DefaultColorPhone

Running with locale: LC_CTYPE=nb_NO.UTF-8;LC_NUMERIC=nb_NO.UTF-8;LC_TIME=nb_NO.UTF-8;LC_COLLATE=nb_NO.UTF-8;LC_MONETARY=nb_NO.UTF-8;LC_MESSAGES=en_GB.UTF-8;LC_PAPER=nb_NO.UTF-8;LC_NAME=nb_NO.UTF-8;LC_ADDRESS=nb_NO.UTF-8;LC_TELEPHONE=nb_NO.UTF-8;LC_MEASUREMENT=nb_NO.UTF-
8;LC_IDENTIFICATION=nb_NO.UTF-8

Running in the manufacturer security domain

Uncaught exception java/lang/RuntimeException: IOException reading reader invalid first byte 11111000.

Execution completed.

22885068 bytecodes executed

3358 thread switches

1791 classes in the system (including system classes)

37695 dynamic objects allocated (2415020 bytes)

144 garbage collections (2133624 bytes collected)
```


If I try to run the application again (with a ~/j2mewtk/ folder), this exception is cast:

```
Running with storage root ~/j2mewtk/2.5.2/appdb/DefaultColorPhone

Running with locale: LC_CTYPE=nb_NO.UTF-8;LC_NUMERIC=nb_NO.UTF-8;LC_TIME=nb_NO.UTF-8;LC_COLLATE=nb_NO.UTF-8;LC_MONETARY=nb_NO.UTF-8;LC_MESSAGES=en_GB.UTF-8;LC_PAPER=nb_NO.UTF-8;LC_NAME=nb_NO.UTF-8;LC_ADDRESS=nb_NO.UTF-8;LC_TELEPHONE=nb_NO.UTF-8;LC_MEASUREMENT=nb_NO.UTF-
8;LC_IDENTIFICATION=nb_NO.UTF-8

Running in the manufacturer security domain

java.lang.RuntimeException: IOException reading reader invalid byte 11100110

	at com.sun.cldc.i18n.Helper.byteToCharArray(+228)

	at com.sun.cldc.i18n.Helper.byteToCharArray(+9)

	at java.lang.String.<init>(+7)

	(...)

	at java.lang.Class.runCustomCode(+0)

	at com.sun.midp.midlet.MIDletState.createMIDlet(+34)

	at com.sun.midp.midlet.Scheduler.schedule(+52)

	at com.sun.midp.main.Main.runLocalClass(+28)

	at com.sun.midp.main.Main.main(+80)

Execution completed.

3739336 bytecodes executed

51 thread switches

1774 classes in the system (including system classes)

27329 dynamic objects allocated (1267964 bytes)

91 garbage collections (1149916 bytes collected)
```

I use Sun Java Wireless Toolkit 2.5.2, MyEclipse 6.0.1 and jdk1.6.0_06. The source files are originally created in XP and Vista.

Any tips?

---

### Post by petermp on 2008-06-03
I found the error. Some of the source files or configuration files were Cp1252 encoded. When setting the jvm to use Cp1252 encoding both on server and client side, everything worked just fine.

---

### Post by simosx on 2008-07-25
> **petermp said:**
> I found the error. Some of the source files or configuration files were Cp1252 encoded. When setting the jvm to use Cp1252 encoding both on server and client side, everything worked just fine.

I have the same issue, and I have verified that all source files are ASCII (which implies they are UTF-8 as well).

What I believe is the source of the problem is the locale UTF-8. Java and Windows use as default the UTF-16 locale. There appears to be a mixup over there. Using a locale such as CP1252 constitutes a workaround rather than a fix. It is important to get JDK to run with a UTF-8 encoding.

In my specific case, the exception is raised on the processing of text that the user entered. The text is ASCII, but still an exception occurs.

---

### Post by petermp on 2008-07-25
What kind of processing do you do?

In my case, I got a Vista-using colleague of mine to check out his default jvm locale. When it turned out to be Cp1252, I just tested to set the same on my jvm's and it worked fine.

Do you have the same problem when you run your application on a physical device?

I do agree that changing the jvm locale is a workaround. However, I do not have the time to investigate this any further, so I have settled with it :)

---

### Post by www.rzr.online.fr on 2010-01-07
I have this issue while parsing http reply ...

is it a bug specific to wtk ?

Please ask for at :
[http://forums.java.net/jive/thread.jspa?messageID=353365&#353365](http://forums.java.net/jive/thread.jspa?messageID=353365&#353365)

---

### Post by petermp on 2010-01-08
No bug, just different encoding of the files :)

---

