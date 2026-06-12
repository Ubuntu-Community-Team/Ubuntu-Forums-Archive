---
title: "The path to the Java directory"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by SteelCore on 2008-08-13
Hi,
I need to enable Java in my Opera browser but that requires choosing the path to the Java directory. Where/How would I find that??? I'm using 7.10

---

### Post by kpkeerthi on 2008-08-13
Look in /usr/lib/jvm

---

### Post by Dill on 2008-08-13
Try this:

```
/usr/lib/jvm/java-1.5.0-sun/jre/lib/i386
```

You should be able to validate the path. If that's not it, enter this code, and the output should be the directory you need:

```
find / -name libjava.so 2> /dev/null 
```

Cheers, 
Dylan

---

### Post by SteelCore on 2008-08-13
Thanks. But there are 2 folders there:
1- java-6-sun
2- java-6-sun-1.6.0.0.3
Which one should I use? or are they all the same?

---

### Post by Dill on 2008-08-13
Did you try typing this into a Terminal?

```
find / -name libjava.so 2> /dev/null
```

It should produce the directory you need

---

### Post by Nepherte on 2008-08-13
> **SteelCore said:**
> Thanks. But there are 2 folders there:
1- java-6-sun
2- java-6-sun-1.6.0.0.3
Which one should I use? or are they all the same?
java-6-sun is a symbolic link to java-6-sun-1.6.0.0.3. So it doesn't matter which one you choose. If you choose the first one, I believe it will always point to the most recent java you have installed, in case you have multiple java-6-sun versions installed.

---

### Post by SteelCore on 2008-08-13
> **Dill said:**
> Did you try typing this into a Terminal?

```
find / -name libjava.so 2> /dev/null
```

It should produce the directory you need

Yes, that gave me
/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjava.so

---

### Post by SteelCore on 2008-08-13
> **Nepherte said:**
> java-6-sun is a symbolic link to java-6-sun-1.6.0.0.3. So it doesn't matter which one you choose. If you choose the first one, I believe it will always point to the most recent java you have installed, in case you have multiple java-6-sun versions installed.

Very informative. Thanks

---

