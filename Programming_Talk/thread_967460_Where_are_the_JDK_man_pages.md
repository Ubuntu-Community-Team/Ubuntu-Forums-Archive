---
title: "Where are the JDK man pages?"
date: 2008-11-02
forum: Programming Talk
---

### Post by HuBaghdadi on 2008-11-02
Hi,
I installed Sun JDK 6 via Synaptic, thought it doesn't include JDK man pages.
Any ideas how to install it?
Thanks.

---

### Post by leg on 2008-11-02
I don't think there are man pages for the jdk. All the info you need is on the sun site try:
[API Docs]("http://java.sun.com/javase/6/docs/api/")
[Tutorials]("http://java.sun.com/docs/books/tutorial/index.html")

---

### Post by scragar on 2008-11-02
For some reason the JDK package doesn't include a man page, but it does contain some docmentation, which is better than nothing I guess:
```
**w3m** /usr/share/doc/sun-java6-jdk/README.html
```
replace w3m with whatever browser you want(just incase you don't like reading from a terminal)

---

### Post by HuBaghdadi on 2008-11-02
When I was using Ubuntu 7.10 , JDK 6 was including man pages for all JDK tools.
It seems to me that JDK6 in Ubuntu 8.04 repositry doesn't has man pages.

---

### Post by SeanHodges on 2008-11-03
Searching through packages.ubuntu.com I can't find any packages containing man pages for the Java API, in either Gutsy (7.10) or Intrepid.

However, there are still man pages for the JDK *tools*, they are bundled with the JDK package itself so you should be able to type "man javac" assuming you have installed the JDK package.

The API is available for off-line browsing by installing "openjdk-6-doc", but this is in HTML format, not man. Again, this is the same situation for Gutsy. If you had the API in man page format in the past, I can only imagine it must have been from a third-party repository, or that you ran a tool like html2man across the HTML docs.

---

### Post by snova on 2008-11-03
There are no man pages, and you should be thankful. Java has a *very* large library.

There is a package that, when installed, will download and extract the documentation from Sun's website. Alternatively, look around their website, you'll find it eventually. It's a ~50MB zip file.

---

### Post by SeanHodges on 2008-11-03
> **snova said:**
> There is a package that, when installed, will download and extract the documentation from Sun's website.

The off-line documentation from Sun is available in the Ubuntu repositories, see my previous post.

---

### Post by HuBaghdadi on 2008-11-05
Well, I don't have any man page for any JDK tool
-----
No manual entry for javac
See 'man 7 undocumented' for help when manual pages are not available.
-----
I noticed that when I installed JDK 6 on Hardy, Synaptic asked me to download JDK docs from java.sun.com , a step Gutsy didn't ask me to do.

---

### Post by SeanHodges on 2008-11-05
> **HuBaghdadi said:**
> Well, I don't have any man page for any JDK tool
-----
No manual entry for javac
See 'man 7 undocumented' for help when manual pages are not available.
-----
I noticed that when I installed JDK 6 on Hardy, Synaptic asked me to download JDK docs from java.sun.com , a step Gutsy didn't ask me to do.

I think there might be something wrong with your installation...

The man pages for the JDK tools are not pulled directly from java.sun.com (though the API documentation might be if you install openjdk-6-doc?). I have JDK6 installed in Ubuntu 8.04 and the man pages were installed from the "openjdk-6-jdk" package:

```
sean@SEAN-PC:~$ dlocate javac.1.gz
sun-java5-jdk: /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/man/man1/javac.1.gz
sun-java5-jdk: /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/man/ja/man1/javac.1.gz
java-gcj-compat-dev: /usr/lib/jvm/java-1.5.0-gcj-4.2-1.5.0.0/man/man1/javac.1.gz
openjdk-6-jdk: /usr/lib/jvm/java-6-openjdk/man/man1/javac.1.gz
openjdk-6-jdk: /usr/lib/jvm/java-6-openjdk/man/ja_JP.eucJP/man1/javac.1.gz
```

Please post the output of this:

```
locate javac | grep man
```

This should help determine if the man pages are actually on your system as they should be.

---

### Post by HuBaghdadi on 2008-11-05
/usr/lib/jvm/java-6-sun-1.6.0.07/man/ja/man1/javac.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.07/man/man1/javac.1.gz
/usr/share/doc/ant-doc/manual/javacprops.html
/usr/share/doc/ant-doc/manual/CoreTasks/javac.html
/usr/share/doc/ant-doc/manual/OptionalTasks/javacc.html

---

### Post by SeanHodges on 2008-11-05
Aha! My mistake, you're using sun-jdk and not openjdk... I missed that.

Well man will be searching /usr/share/man for the man pages, which is not where your JDK man pages are. You can test this theory by pointing man at your JDK man path:

```
man --manpath=/usr/lib/jvm/java-6-sun-1.6.0.07/man javac
```

I would suggest this is a bug in the package, both OpenJDK and GCJ use the alternatives system to point to the correct man pages, but this seems to be broken in java-6-sun...

You should raise a bug in Launchpad to fix it, but a suitable work-around might be to add this path to your MANPATH variable in your ~/.bashrc file:

```
export MANPATH="$MANPATH:/usr/lib/jvm/java-6-sun-1.6.0.07/man"
```

---

### Post by jamesstansell on 2008-11-05
I just looked at my 8.10 Intrepid box and the sun-java6 manpages are linked properly from /etc/alternatives.  Does this command fix it for you?

```

$ sudo update-java-alternatives -s java-6-sun

```

---

### Post by jamesstansell on 2008-11-05
BTW, the launchpad bug is #294116; offhand I think it should probably be marked as invalid. (see my previous comment here)

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/294116](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/294116)

(Perhaps instead of marking the bug invalid it should just be converted to a question.)

---

### Post by HuBaghdadi on 2008-11-05
I run this command the very first time I installed the JDK 6

---

### Post by jamesstansell on 2008-11-06
> **HuBaghdadi said:**
> I run this command the very first time I installed the JDK 6

You may possibly need to run it again.

I just tested on my Hardy (ubuntu 8.04) machine, and the man pages were fine.  Also  switching back and forth between sun-java6 and openjdk6 worked with no problem.

---

