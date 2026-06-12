---
title: "Why does Eclipse package depend on GNU Java?"
date: 2007-04-22
forum: Programming Talk
---

### Post by jespdj on 2007-04-22
Hello everybody.

I just installed Feisty Fawn from scratch. I'd like to do Java development and Eclipse is my favourite IDE.

I also want to use Sun's JDK 6. I hate the GNU Java junk, which is unfortunately the default Java in Ubuntu. So I used Synaptic to download and install Sun JDK 6 and to remove the GNU Java junk.

After that I wanted to install Eclipse 3.2.2 with Synaptic. Now if I select Eclipse in Synaptic, it insists on installing the GNU Java junk again! :mad: So instead of using the Ubuntu package I downloaded Eclipse from [www.eclipse.org](www.eclipse.org) and installed it by hand (just unzip/tarring the package in /usr/share).

Why does the Eclipse Ubuntu package depend on the GNU Java junk? Eclipse doesn't need that.

Where can I file a request to have this dependency removed in a future Ubuntu Eclipse installation package?

---

### Post by jespdj on 2007-04-22
I looked at the dependencies in Synaptic. I think the error is here:

1. eclipse depends on: eclipse-jdt
2. eclipse-jdt depends on: eclipse-platform
3. eclipse-platform depends on: java-gcj-compat | java1-runtime | java2-runtime

That last line is the bug. I don't have java1-runtime or java2-runtime (these packages are not listed in the package list). So Synaptic insists on using the GNU Java stuff, even though I have sun-jdk-6 and other Sun Java packages installed.

Where can I report this so that the Eclipse package can be fixed?

---

### Post by nanotube on 2007-04-22
probably on here:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by jespdj on 2007-04-22
Thanks, I asked the question on Launchpad (#5383).

---

### Post by nanotube on 2007-04-22
> **jespdj said:**
> Thanks, I asked the question on Launchpad (#5383).

cool. feel free to post back here when you get some results. :)

---

