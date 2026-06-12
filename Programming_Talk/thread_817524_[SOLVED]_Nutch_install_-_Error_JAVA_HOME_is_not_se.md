---
title: "[SOLVED] Nutch install - Error: JAVA_HOME is not set"
date: 2008-06-03
forum: Programming Talk
---

### Post by ultraloveninja on 2008-06-03
I know why it's doing this.

It's because i don't have this:

JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.10
export JAVA_HOME

in my etc/profile.


Can anyone tell me where that exactly needs to go?

Do I just put it in the profile for root. Is that correct?  I am VERY n00b to this part of ubuntu.

Any help is greatly appreciated.

Thanks!

---

### Post by xlinuks on 2008-06-03
In your home directory there's a hidden file (among many other hidden files) called ".bashrc". It's a text file, add to the end a line correspondingly putting the path to where your JDK is installed, in my case it's:
```

export JAVA_HOME=/home/fox/apps/jdk1.6.0_06

```
In Nautilus to show/hide the hidden files press Ctrl+H
After you set the new variable, depending on what you're gonna do, you need to logout/login back.
The system reads each time the ".bashrc" file and creates that variable.

---

### Post by ultraloveninja on 2008-06-04
Awesome.

That got rid of that,but now whenI try to execute a crawl:


bin/nutch crawl urls/helppages -dir crawl -depth 3 -topN 50


it comes back with this:

bin/nutch: line 153: /usr/lib/jvm/java-1.5.0-sun-1.5.0.10/bin/java: No such file or directory
bin/nutch: line 246: /usr/lib/jvm/java-1.5.0-sun-1.5.0.10/bin/java: No such file or directory
bin/nutch: line 246: exec: /usr/lib/jvm/java-1.5.0-sun-1.5.0.10/bin/java: cannot execute: No such file or directory

Looks like I got some stuff pointed to the wrong directory.

I wish I knew where all of this stuff was at.
Time to start digging.

---

### Post by xlinuks on 2008-06-04
I don't know what the following code is:
```

bin/nutch crawl urls/helppages -dir crawl -depth 3 -topN 50

```
Perhaps it is an app that has a bug, I don't have it so I can't test it.
I hope you correctly set the path, I hope you set JAVA_HOME not to the "bin" directory, but to the directory where it's installed, thus, NOT to "/usr/lib/jvm/java-1.5.0-sun-1.5.0.10/bin", but to "/usr/lib/jvm/java-1.5.0-sun-1.5.0.10".

According to the error your app yields, check if there is a file by the path
> /usr/lib/jvm/java-1.5.0-sun-1.5.0.10/bin/java

---

### Post by ultraloveninja on 2008-06-04
ok...

i will check that.

I am basically trying to run an intranet crawl from this guide:

[http://lucene.apache.org/nutch/tutorial8.html](http://lucene.apache.org/nutch/tutorial8.html)

where it says this:

> Once things are configured, running the crawl is easy. Just use the crawl command. Its options include:

    * -dir dir names the directory to put the crawl in.
    * -threads threads determines the number of threads that will fetch in parallel.
    * -depth depth indicates the link depth from the root page that should be crawled.
    * -topN N determines the maximum number of pages that will be retrieved at each level up to the depth.

For example, a typical call might be:

bin/nutch crawl urls -dir crawl -depth 3 -topN 50


but i installed nutch from this guide:

[http://wiki.apache.org/nutch/GettingNutchRunningWithDebian](http://wiki.apache.org/nutch/GettingNutchRunningWithDebian)



I am going to check out that path.

---

### Post by ultraloveninja on 2008-06-04
HA!!!

I got it.


i don't have /java-1.5.0-sun-1.5.0.10

i have /java-1.5.0-sun-1.5.0.15


changed that in the bashrc file and all it good.

thanks!!!

---

### Post by xlinuks on 2008-06-04
You're welcome :)

---

