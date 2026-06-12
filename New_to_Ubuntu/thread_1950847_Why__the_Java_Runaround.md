---
title: "Why  the Java Runaround?"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Andavane on 2012-04-01
I'm trying to seize the bull by the horns by understanding *some*thing about this Java Devil; I think I should remove the one here is Oneiric and update it.
But first I am opening Terminal and typing "which java" which returns:

> /usr/bin/java

and when I go and look at that file, it's a link to:
> /etc/alternatives/java

and when I go there I see THAT is a link to:

> /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz

So I'd like to understand a bit about why there is this runaround, if I am to try to understand Java even a little bit. Which I don't now.

Regards, John

---

### Post by santosh83 on 2012-04-01
> **Andavane said:**
> I'm trying to seize the bull by the horns by understanding *some*thing about this Java Devil; I think I should remove the one here is Oneiric and update it.
But first I am opening Terminal and typing "which java" which returns:



and when Ii go and look at that file, it's a link to:


and when I go there I see THAT is a link to:



So I'd like to understand a bit about why there is this runaround, if I am to try to understand Java even a little bit. Which I don't now.

Regards, John

The "Alternatives" system is something Debian first introduced to deal with several packages providing the same command. The default command is simply a link to the alternatives directory, which then redirects it to the appropriate binary. It's used by several 'generic' commands as well, like 'x-www-browser', 'editor' and so on.

In Java's case, this allows you to have multiple versions of the JVM installed, and use alternatives to set the default. You can use 'update-alternatives' to set the defaults for all commands registered with alternatives. See man update-alternatives.

As an aside, the command output you've indicated above seems abnormal. I'd expect /etc/alternatives/java to redirect to the java binary, not the man page for it.

---

