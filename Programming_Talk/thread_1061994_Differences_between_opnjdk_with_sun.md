---
title: "Differences between opnjdk with sun"
date: 2009-02-06
forum: Programming Talk
---

### Post by pedroezsa on 2009-02-06
I used standard jdk from sun when i still used windos, but now i use openjdk since i read many reviews about it when i tried to install java in ubuntu, instead of the one from sun (sunjava~).
But, what are exactly the differences between these two??

ps : I'am askin this now because i'm trying to install applet plugin in my firefox, and seems like all the plugin used the sunjava, is it just okay if i'm installing this plugin??

Thanks before for the replay

---

### Post by cb951303 on 2009-02-06
I would like to add a question. Does OpenJDK has a firefox plugin? If so why people is so excited about the 64Bit sun plugin?

---

### Post by bruce89 on 2009-02-06
> **cb951303 said:**
> I would like to add a question. Does OpenJDK has a firefox plugin? If so why people is so excited about the 64Bit sun plugin?

Yes, and because people don't know about it.

---

### Post by drubin on 2009-02-06
I would stick with Sun's version of java for now.... They are going to release their implementation as opensource with version 7.

but the openjdk is just too bugy for GUI type apps.

Take a look at this post for further info [http://ubuntuforums.org/showpost.php?p=6031955&postcount=9](http://ubuntuforums.org/showpost.php?p=6031955&postcount=9)

---

### Post by pedroezsa on 2009-02-06
so i guess sunjava is better than openjdk?? cz i sometimes have my netbean closed suddenly too.. is it also because of the openjdk bug?

---

### Post by nebu on 2009-02-06
open jdk is actually developed by sun microsystems....

sun has some kind of initiative that they are going to make jdk an open source software.... in that endeavour.... they have launched openjdk....


in the future all releases of java will shift to the openjdk standard.....
today however.... the proprietary format of jdk is definitely less buggy....

---

### Post by jespdj on 2009-02-06
[OpenJDK](http://openjdk.java.net/) (hint: you would have found that website with a simple Google search) is about 95% the same as Sun Java 6.

Some time ago, Sun decided to open source their Java implementation. They couldn't do that easily, because they used some proprietary third-party parts that they don't have the rights to. So they started the OpenJDK project for developing the next version of open source Java (this is eventually going to become Java 7). In the OpenJDK project, Sun is replacing the proprietary parts by open source parts.

Because people wanted open source Java now, they decided to make a Java 6 version based on the OpenJDK code. That is the version of OpenJDK Java that's currently in the Ubuntu repository.

OpenJDK Java is the default Java on Ubuntu because it's fully open source. You can install the regular Sun Java 6, but that's the old, non-open source Java with the proprietary parts still included.

OpenJDK Java 6 works fine for almost everything, and NetBeans and Eclipse run fine on OpenJDK.

Up to Sun Java 6 update 11, there was no 64-bit browser plug-in included with Sun Java. A few days ago Sun released Java 6 update 12, which finally includes a 64-bit browser plug-in.

There's also a browser plug-in for 64-bit OpenJDK Java. But unfortunately it does not work correctly with all Java applets, notably the applets that some banks use for online banking don't work with OpenJDK. That's why some people had problems with OpenJDK Java on a 64-bit system.

---

### Post by pedroezsa on 2009-02-16
Thanx for the answers, so i guess i'll keep my openjdk till the sun version 7 released \\:D/

---

### Post by hthury on 2009-02-16
I also used sunjava, but didn't even knew about the OpenJDK until this morning when I got a look in the repositories.

I was just looking for that kind of information.

Thanks everyone.

I'll try OpenJDK and go back to sunjava if it too much buggy. I hope not.

---

### Post by eye208 on 2009-02-17
> **drubin said:**
> but the openjdk is just too bugy for GUI type apps.
No, it's not.

> Take a look at this post for further info [http://ubuntuforums.org/showpost.php?p=6031955&postcount=9](http://ubuntuforums.org/showpost.php?p=6031955&postcount=9)
That "bug" was caused by a missing fonts package.

---

