---
title: "Anyway to speed up Eclipse?"
date: 2006-02-21
forum: Programming Talk
---

### Post by darthsabbath on 2006-02-21
It seems like a great IDE, almost visual Studio level, but... meh, it's SLOW.  Any hints, or any other good Java IDEs?  I've tried BlueJ, which seems okay, NetBeans, and Sun's stuff, and Eclipse seems to be the best, except for its speed.

Phil

---

### Post by LordHunter317 on 2006-02-21
Add more physical RAM.  Run it in Sun's JAVA 5 JDK/JRE.  That's about all you can sanely do.

Certain things will still be dog slow.

---

### Post by gord on 2006-02-21
general rule of thumb, if it runs in java. its gonna run slow (unless you have enough ram)

---

### Post by hod139 on 2006-02-21
[quote=LordHunter317]Run it in Sun's JAVA 5 JDK/JRE. [/quote] 
This was kinda a pain to do for me, unless I am missing something. I wanted Eclipse (and all other Java apps) to use Sun's JRE by default, not GNU's version. This means I didn't want to do
```
 eclipse -vm /usr/lib/j2sdk1.5-sun 
``` and/or set up an alias.  I just wanted to to set a system wide setting and have Eclipse obey, but I couldn't.

I thought I would only have to do 
```

sudo update-alternatives --config java

``` and choose Sun's JRE, but that didn't work.  Eclipse would still use GNU's gcj.

To finally get it to work, I removed the gcj runtime from my machine
```

sudo apt-get remove --purge java-gcj-compat

``` 
This effectively fixed the problem. Now, when starting Eclipse it can't find GNU's JRE, and starts polling a set of default locations for another runtime, which the SUN JRE is in. This is not a good solution, since IMO eclipse should listen to the update-alternatives command.

If someone knows a better way I'd like to hear it.

---

### Post by darthsabbath on 2006-02-21
Just out of curiosity, I'm running this on a 2.8 Ghz w/768MB RAM on 1 box and an Athlon 2400+ w/1GB RAM on the other, so I guess it's either deal with it or find another IDE. :D Any suggestions? I've heard Kdevelop was good, so I may install that.

---

### Post by darthsabbath on 2006-02-21
BTW... I'm also using the Sun JDK/JRE to run Eclipse.

---

### Post by jerome bettis on 2006-02-21
i apt-getted eclipse the other day ... wow has it gone downhill

3.0 was useable, this has all kinds of new features i don't need that just slow it down.  plus i can't even get it to run hello world without throwing a bunch of weird exceptions that make no sense.

---

### Post by gord on 2006-02-21
that should really be 'enough' to run eclipse. if its still sluggish use som't else. if you want lots of customisation id go for kdevelop if i were you. i personally use anjuta because all im really after is syntax highlighting and a 'compile' and 'run' button ;) 

n i wouldn't recomend using the version of eclipse from the repo's, people have been seeming to be having problems with it.

---

### Post by JoshuaPDavis on 2006-02-21
[QUOTE=darthsabbath]Just out of curiosity, I'm running this on a 2.8 Ghz w/768MB RAM on 1 box and an Athlon 2400+ w/1GB RAM on the other, so I guess it's either deal with it or find another IDE. :D Any suggestions? I've heard Kdevelop was good, so I may install that.[/QUOTE]
I love Eclipse, but it is a pig.

First thing I would try is bumping up the min/max heap size, launching eclipse like so: 
```
eclipse -Xms=256m -Xmx=512m
```

However, the biggest problem with Eclipse on Linux is that the Gtk+ version of SWT is slow.  You could try using the motif widget set by launching eclipse like this:
```
eclipse -ws motif
```

If you don't like the looks of motif (I know I don't) you could try using [this plugin]("http://swtfox.sourceforge.net/"), a Fox-based implementation of SWT.  It is more performant than SWT/Gtk+, and it looks better than motif.  I just recently started using it, so I can't vouch for its stability yet.

You can find more tips on Eclipse performance [here]("http://www.jroller.com/page/rayhon/20050515").

Josh

---

### Post by LordHunter317 on 2006-02-21
[QUOTE=JoshuaPDavis]I love Eclipse, but it is a pig.

First thing I would try is bumping up the min/max heap size, launching eclipse like so: 
```
eclipse -Xms=256m -Xmx=512m
```[/quote]This, on Linux, won't speed it up any, mearly prevent it from crashing sooner.  Linux doesn't bother to do any page allocation until the page is actually faulted for.

Well, you could turn strict overcommitting on, and it does the accounting.  But it won't speed anything up.

---

### Post by JoshuaPDavis on 2006-02-22
[QUOTE=LordHunter317]This, on Linux, won't speed it up any, mearly prevent it from crashing sooner.  Linux doesn't bother to do any page allocation until the page is actually faulted for.[/QUOTE]
Are you certain of this?  Are you saying that Java on Linux ignores the -Xms parameter?

I don't know much about memory management on Linux, but I ran a simple test and it looks to me like the memory is being pre-allocated.  I realize that I could simply be misinterpreting the output.

I made this Java class: 
```
public class Test {
        public static void main(String[] args) {
                try {
                        Thread.sleep(Integer.MAX_VALUE);
                } catch (InterruptedException ex) { }
        }
}
```
Then compiled and ran the following test:
```
klops@ops01 ~ $ java -Xms256m -Xmx256m -cp . Test &
[1] 6891
klops@ops01 ~ $ ps -F
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
klops     6834  6833  0   650  1400   1 10:21 pts/7    00:00:00 -bash
klops     6891  6834  1 107140 8712   1 10:28 pts/7    00:00:00 java -Xms256m -Xmx256m -cp . Test
klops     6899  6834  0   620   868   1 10:28 pts/7    00:00:00 ps -F
klops@ops01 ~ $ kill 6891
klops@ops01 ~ $ java -Xms128m -Xmx128m -cp . Test &
[2] 6901
[1]   Exit 143                java -Xms256m -Xmx256m -cp . Test
klops@ops01 ~ $ ps -F
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
klops     6834  6833  0   650  1400   1 10:21 pts/7    00:00:00 -bash
klops     6901  6834  1 74249  8452   1 10:29 pts/7    00:00:00 java -Xms128m -Xmx128m -cp . Test
klops     6909  6834  0   619   864   1 10:29 pts/7    00:00:00 ps -F
klops@ops01 ~ $ kill 6901
[2]+  Exit 143                java -Xms128m -Xmx128m -cp . Test
klops@ops01 ~ $ java -Xms512m -Xmx512m -cp . Test &
[1] 6940
klops@ops01 ~ $ ps -F
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
klops     6834  6833  0   650  1400   1 10:21 pts/7    00:00:00 -bash
klops     6940  6834  2 172666 9220   1 10:33 pts/7    00:00:00 java -Xms512m -Xmx512m -cp . Test
klops     6948  6834  0   620   868   1 10:33 pts/7    00:00:00 ps -F
klops@ops01 ~ $ kill 6940
```

Josh

---

### Post by LordHunter317 on 2006-02-22
[QUOTE=JoshuaPDavis]Are you certain of this?  Are you saying that Java on Linux ignores the -Xms parameter?[/quote]No, what I'm saying is that Java mallocs() all the RAM, and Linux just says, "Yes, it's there".  Linux doesn't bother to check to see if it can actually make the allocation unless strict overcommit is turned on.  

In either case, it doesn't actually allocate the memory to the process at that point.  It doesn't do that until the pages are faulted for.

> I don't know much about memory management on Linux, but I ran a simple test and it looks to me like the memory is being pre-allocated.Virtual memory, yes.  Linux isn't forcing any more pages into physical memory for Eclipse.  Look at RSS, it's nearly constant.

Now, you will get a slight benefit due to the fact that the JVM won't be reallocating the heap as often, but the point is that on Linux, that benefit is really tiny.  That's not true on other operating systems.

---

### Post by JoshuaPDavis on 2006-02-22
That's good information, thanks.  Optimizing the heap size makes a noticeable difference on Windows, but I hadn't actually done any benchmarks to see if the same was true on Linux.

---

### Post by matemargo on 2007-07-24
I know this is an old post. But FYI, you can disable "Auto-Activation" from Content Assist. This will avoid the hungs when you press ".".

To disable it, go to "Window/Preferences/Java/Editor/Content Assist". Unmark the option "Enable auto activation" in the "Auto-Activation" section.

Hope this help somebody.

---

