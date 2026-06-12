---
title: "Need help with IKVM (Java with Mono)"
date: 2006-04-15
forum: Programming Talk
---

### Post by solomarv on 2006-04-15
I am getting this problem:

```
$ javac Demo.java -classpath 'mscorelib.jar:gtk-sharp.jar'
Demo.java:5: cannot access cli.System.Object
file cli/System/Object.class not found
                Application.Init();
                           ^
1 error

```

Any ideas?

I checked mscorlib.jar, and found Object.class in java.lang, so I copied it to cli.System, and still getting the same problem.

For those of you who may not know, IKVM allows to use Mono libraries (GUI ones are of particular interest) inside of Java applications. Before using Mono, I had to run:

```
$  ikvmstub /usr/lib/mono/1.0/mscorlib.dll
$  ikvmstub /usr/lib/mono/gtk-sharp/gtk-sharp.dll
$  ikvmstub /usr/lib/mono/gtk-sharp/glib-sharp.dll
$  ikvmstub /usr/lib/mono/gtk-sharp/atk-sharp.dll
```

This is latest dapper, if it matters.

---

### Post by jrei on 2006-07-19
I have the same problem.

Its actually quit difficult to find helpfull information in the web, howto use ikvm propperly.

Greetings, Jörn

---

