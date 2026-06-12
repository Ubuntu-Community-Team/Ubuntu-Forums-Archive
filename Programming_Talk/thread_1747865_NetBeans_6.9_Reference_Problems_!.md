---
title: "NetBeans 6.9 Reference Problems !"
date: 2011-05-03
forum: Programming Talk
---

### Post by etdsbastar on 2011-05-03
Hello there,

I had updated netbeans plugins and modules today through the inbuild update option. Now I am getting the following error:

Reference Problems for JUnit.

Please see the attached images. 

Help me.

---

### Post by Flaxis on 2011-05-03
Not entirely sure, but try downloading the libraries manually, and place them as a JAR in '/usr/lib/jvm/java-6-sun/jre/lib/ext' (or openJDK, depends on what you use). You'll probably need root rights to do this.
Let me know if this worked.

---

### Post by etdsbastar on 2011-05-03
no such folder dear. 

Where to download the junit libraries, can they be found in synaptic?

---

### Post by Flaxis on 2011-05-03
An apt-cache search leads me to a package called junit4. You could try installing it through dpkg, though, I would download the latest release from [https://github.com/KentBeck/junit/downloads](https://github.com/KentBeck/junit/downloads) (the JAR, of course)

"no such folder dear."
Have you tried looking in openJDK equivalents? Explore /usr/lib/jvm and directories underneath on own insight. Since I switched to JRE from sun, my directory structure will probably be slightly different from yours.

---

### Post by etdsbastar on 2011-05-03
> **Flaxis said:**
> An apt-cache search leads me to a package called junit4. You could try installing it through dpkg, though, I would download the latest release from [https://github.com/KentBeck/junit/downloads](https://github.com/KentBeck/junit/downloads) (the JAR, of course)


junit is already installed.
see the attachment.

---

### Post by Flaxis on 2011-05-03
Remove these packages and download the libraries without using syntapic. Sometimes software sources aren't up-to-date.
If even that doesn't work, follow this tutorial:
[http://www.chromedocs.net/2010/06/or-how-i-learned-to-stop-reading-bug.html](http://www.chromedocs.net/2010/06/or-how-i-learned-to-stop-reading-bug.html)
It says IcedTea, but IcedTea is the browser plugin used by OpenJDK, so you will change your entire JRE to sun.
(Select the text if it is not readable, the writer of the blog changed the text color to black)

---

### Post by etdsbastar on 2011-05-03
i had downloaded junit-4.5.jar and kept under /<user folder>/.netbeans/6.9/modules/ext and my problem has been solved.

Thanks for all your support.

---

