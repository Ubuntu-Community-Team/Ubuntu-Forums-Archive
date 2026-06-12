---
title: "Maximum memory available to Java Virtual Machine"
date: 2008-02-05
forum: Programming Talk
---

### Post by barrybevel on 2008-02-05
Hi,
  I'm running a WebSphere Portal Server on Ubuntu 7.10.

The fact I'm running Portal is not reallyt important it''s just a JVM,
but must be 32-bit JVM.

What is the maximum amount of memory a JVM can access on Linux?

i.e. How much memory can a single 32-bit process can access?

I only have access to machines with 1GB ram.


If anyone out there has a Ubuntu machine with a lot of ram

will the following work with the SUN (Must be SUN)  java command:

java -Xms1024m -Xmx1024m hello.HelloWorldApp

java -Xms2048m -Xmx2048m hello.HelloWorldApp

java -Xms3072m -Xmx3072m hello.HelloWorldApp

java -Xms4096m -Xmx4096m hello.HelloWorldApp


I don't expect 4096 to work as the JVM itself and the OS will take
a nice chunk of ram.

Thanks in advance to anyone who knows or is willing to help.

Cheers,
  Barry.


```

package hello;

public class HelloWorldApp
{
  public static void main(String arg[])
  {
    System.out.println("Hello World!");
  }
} 

```

---

### Post by Zugzwang on 2008-02-05
This can easily be found using your favourite search engine:

[http://weka.sourceforge.net/wiki/index.php/Java_Virtual_Machine]("http://weka.sourceforge.net/wiki/index.php/Java_Virtual_Machine")

---

### Post by barrybevel on 2008-02-05
Thanks Zugzwang, that is a good link.
The answer is 1.7GB  Not at all what I expected.

---

### Post by barrybevel on 2008-02-07
Hi,
  When I said that Linux can only have a Max JVM Heap of 1.7GB and suggested we look at Solaris, a guy at work got bothered.

He told me that in a near future, a version of Linux will have Memory defrag and it will make it possible to have a larger chuck of continious memory for the JVM.

Has anyone heard of this or is it just silly talk for sake of agrument?

I can't find anything about memory defrag 
(maybe defrag is the wrong word but you know what I mean...)

Thanks in advance

---

### Post by RIchard James13 on 2008-02-07
Just a thought but that article mentions the 3/1 split in the Linux Kernel. There is a patch to give more options in the split. I don't know if that would solve the problem though.
[http://kerneltrap.org/node/2450]("http://kerneltrap.org/node/2450")

Memory Fragmentation in the Linux Kernel, scroll down the page a bit
[http://lwn.net/Articles/120960/]("http://lwn.net/Articles/120960/")

---

### Post by barrybevel on 2008-02-08
Hi RIchard James13,
  That artical on 3/1 split and solutions is execllent.
Thanks a million.

---

