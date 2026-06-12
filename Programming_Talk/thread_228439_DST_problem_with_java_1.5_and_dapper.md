---
title: "DST problem with java 1.5 and dapper"
date: 2006-08-03
forum: Programming Talk
---

### Post by statuz on 2006-08-03
Hi all,
I've got 2 machine (updated daily) running dapper with java 1.5; I found that "strangeness":

Executing this simple code:

import java.util.*;

public class Test
{
   public static void main(String[] args)
   {
      GregorianCalendar gc = new GregorianCalendar();
      System.out.println("TIME: "+gc.get(Calendar.HOUR_OF_DAY)+":"+gc.get(Calendar.MINUTE));
      System.out.println("ZONE: "+gc.get(Calendar.ZONE_OFFSET)/(60*60*1000));
      System.out.println("DST: "+gc.get(Calendar.DST_OFFSET)/(60*60*1000));
   }
}

this is the output:

TIME: 9:5
ZONE: 1
DST: 0

but if I execute "date" from bash I've got (I'm in Italy):

gio ago  3 10:05:15 CEST 2006

What I want to say is that on ubuntu machines java doesn't recongnize DST and therefore every java date miss an hour; I executed the same code on windows, debian, suse and osx and the result is correct:

ZONE: 1
DST: 1

Someone can tell me something about this and if this happens only to me?
Thank you in advance

---

### Post by hod139 on 2006-08-03
Running your code I get the following output:
TIME: 12:49
ZONE: -5
DST: 1

Are you sure you're using Sun's java and not Gnu's?  I wrote up a little [howto]("http://ubuntuforums.org/showthread.php?t=201378") for installing Sun's java and Eclipse, you can ignore the parts of the post relating to eclipse.

Edit: I should add that I'm US eastern time, and the output from date is
```

Thu Aug  3 12:49:53 EDT 2006

```

---

### Post by statuz on 2006-08-03
Thank for your reply,
I'm sure I'm using Sun's java, let's look at my shell output:

statuz@linux:~$ sudo update-alternatives --config java
Password:
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      2        /usr/bin/gij-wrapper-4.1
 +    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:

And for being really sure:
statuz@linux:~$ which java
/usr/bin/java
statuz@linux:~$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2006-06-21 17:52 /usr/bin/java -> /etc/alternatives/ja va
statuz@linux:~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 40 2006-08-02 11:39 /etc/alternatives/java -> /usr/lib/jv m/java-1.5.0-sun/jre/bin/java

and

statuz@linux:~$ which javac
/usr/bin/javac
statuz@linux:~$ ls -l /usr/bin/javac
lrwxrwxrwx 1 root root 23 2006-06-21 19:10 /usr/bin/javac -> /etc/alternatives/javac
statuz@linux:~$ ls -l /etc/alternatives/javac
lrwxrwxrwx 1 root root 37 2006-06-21 19:10 /etc/alternatives/javac -> /usr/lib/jvm/java-1.5.0-sun/bin/javac

I compiled and ran this code both from shell and from eclipse.. with the same result..

Thank you again, hope to solve this problem..

---

### Post by anilwanted on 2008-08-15
I also face the same problem.
The sys time is correct but Java gets it wrong.
any solution?

---

### Post by Zugzwang on 2008-08-17
Ok, here is the solution. The problem is that the default constructor uses the "default timzone". However, the default is *not* the one you set in your GNOME/KDE profile. Java reads it from some different place. Read [here]("http://www.javaworld.com/javaworld/jw-10-2003/jw-1003-time.html") for more details.

---

