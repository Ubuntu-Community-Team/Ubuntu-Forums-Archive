---
title: "Compiling and running a java program"
date: 2011-01-06
forum: Packaging and Compiling Programs
---

### Post by Smintitule on 2011-01-06
It's a pretty simple java program I just wrote, and I'm not seeing why it isn't compiling.  Here's what's going on in the terminal:

~$ javac /home/leeland/test.java
l:~$ java test
Exception in thread "main" java.lang.NoClassDefFoundError: test
   at gnu.java.lang.MainThread.run(libgcj.so.11)
Caused by: java.lang.ClassNotFoundException: test not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.11)
   at java.lang.ClassLoader.loadClass(libgcj.so.11)
   at java.lang.ClassLoader.loadClass(libgcj.so.11)
   at gnu.java.lang.MainThread.run(libgcj.so.11)



And here's the (purposefully simple) source code:

class TestClass
{
    public static void main(String[] args)
    {
	System.out.println("Test");
    }
}

Any ideas?

---

### Post by Lootbox on 2011-01-06
If you named the class TestClass, you'll also need to name the file TestClass.java and compile/run it as such.

```

$ cd /path/to/directory/
$ javac TestClass.java
$ java TestClass

```

---

### Post by Smintitule on 2011-01-06
Ah, I knew it had to be something simple.

Thanks so much!

---

