---
title: "Java giving wrong time"
date: 2007-09-16
forum: Programming Talk
---

### Post by CptPicard on 2007-09-16
Ok, this is on Debian Etch so not really Ubuntu but I think I'll ask anyway as it's likely someone is able to give me a good answer...

I am setting up a Java web application on my new Debian server, and running into an oddity with Java's time. System time and timezone are correct as far as I know:

```

Your default time zone is set to 'Europe/Helsinki'.
Local time is now:      Sun Sep 16 07:25:02 EEST 2007.
Universal Time is now:  Sun Sep 16 04:25:02 UTC 2007.

```

However, with Java code that essentially does System.out.println(new Date()) we get:

```

voitto:~# java Testi
Sun Sep 16 06:30:45 GMT+02:00 2007

```

So Java is an hour behind :confused: -- This is going to be a total showstopper for this deployment until it is resolved :(

Nothing like this on my Ubuntu development box! It probably has something to do with summer time, but no idea how to fix this...

---

### Post by dwhitney67 on 2007-09-16
Maybe this [article]("http://www.javaworld.com/javaworld/jw-10-2003/jw-1003-time.html") will help you.

---

### Post by CptPicard on 2007-09-16
Thanks lots for the pointer, looks like the problem I'm having... reading it now.

Quite unforgivable of Java really to have such a fundamental behaviour difference even between two Linuxes, both running Java 1.5.. :( "Write once run anywhere", my *** :(

EDIT: Ok, so it's a matter of setting TZ or -Duser.timezone=Europe/Helsinki. *Phew*. Interesting though that Debian's Sun Java can deduce the GMT+2 bit of timezone information but not the DST adjusted one, while Ubuntu doesn't have TZ set and the Java timezone information is correct....

EDIT2: Heh, weirdness. Just for posterity, let it be recorded that [this solved it]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/49068/comments/13"). Java doesn't like /etc/localtime unless it's a symlink (which it isn't even on my Ubuntu box), and making it a symlink makes Java like the timezone data :p

---

