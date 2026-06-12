---
title: "Executing ruby compiled with jruby"
date: 2011-03-01
forum: Programming Talk
---

### Post by fizgig on 2011-03-01
I've made a simple ruby program:

```
puts "Hello World"
```

and compiled it with jruby:

```
jrubyc test.rb
```

That seems to work as I get no errors and I now have test.class in my directory.  I now try to run it:

```
java test
```

and I get this:

```
Exception in thread "main" java.lang.NoClassDefFoundError: test
Caused by: java.lang.ClassNotFoundException: test
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: test.  Program will exit.
```

I'm not sure why.  I tried running it using the built in openjdk version and the sun version and it doesn't make a difference.

Anyone have any tips?

---

### Post by fizgig on 2011-03-01
Well, I randomly solved it seconds later.  Had to have this:

```
export CLASSPATH=/usr/lib/jruby/lib/jruby.jar:/home/matt
```

where /home/matt was the location of my compiled program.  Think I'm good now.

---

