---
title: "Java as a scripting language"
date: 2009-10-07
forum: Programming Talk
---

### Post by cknight on 2009-10-07
I'm basically wondering what disadvantages there might be by using Java as a scripting language (via the execution of commands through ProcessBuilder).  When you think scripting, the likes of Perl, Ruby, Python and many more come to mind, but not Java.  Why is this?

I keep trying to pick up one of these scripting languages, but just can't seem to stick with it long enough and get frustrated thinking I could do it much quicker in Java.  However, I'm well versed in Java and would be happy if the only disadvantage was more verbose code.

Also, Groovy seems an interesting avenue to look at (which claims to have an almost zero learning curve for Java developers).

Your thoughts?

---

### Post by pbrockway2 on 2009-10-07
I don't know how much sense it makes to power up an entire JVM just to ls a directory, rename a bunch of files or do some other task for which the likes of bash might be better suited.

On the other hand if you mean "scripting" as in "interpreted", then there is also [BeanShell]("http://www.beanshell.org/intro.html") which interprets Java source.

---

### Post by wieman01 on 2009-10-07
The advantage of PHP is for example that it is less complex and rather light-weight compared with Java. I used to programm J2EE and loved it, but I came to realize that PHP is much better for web development as it less complex and there are tons of good open source projects out there (e.g. Wordpress) that make web development a breeze.

For application development I guess I would still prefer Java, but I don't do it anymore these days.

---

### Post by kavon89 on 2009-10-07
Straight Java not very effective at all for writing scripts, especially since one of the nice things about scripts is one could quickly edit it/view the source if needed, which wouldn't be the case if Java were used.

Use Groovy, it should be very familiar to anyone versed in Java and I hear good things about it although the name is unusual.

---

