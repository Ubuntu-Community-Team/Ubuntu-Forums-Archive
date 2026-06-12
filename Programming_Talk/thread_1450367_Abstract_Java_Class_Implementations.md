---
title: "Abstract Java Class Implementations"
date: 2010-04-09
forum: Programming Talk
---

### Post by vik_2010 on 2010-04-09
I was looking through the Java source files, and I cam across an abnormality I hope someone can clarify:

The class "FileSystem.java" is an abstract class - hence, one should not be able to instantiate it directly.

However, the very first variable in File (both FileSystem and File are in the java.io package) creates a FileSystem object via:

[PHP]
public class File implements Serializable, Comparable<File> {
          private static FileSystem fs = FileSystem.getFileSystem();
[...]
}
[/PHP]How is it doing this? getFileSystem() in the FileSystem class is just a stub: there is no definition. 

If someone could elucidate how this is happening, i would appreciate it. I'm assuming that FileSystem is being concretely defined somewhere, but I don't know what to make of it, nor can I create a mental picture of how this should happen.

---

### Post by falconindy on 2010-04-09
I believe the implementation of FileSystem is OS specific, and defined by the JVM for the platform.

---

### Post by Some Penguin on 2010-04-09
You don't need to instantiate an object to call a class (i.e. static) method.

---

### Post by vik_2010 on 2010-04-09
Hmm...yes, I understand what both of you are saying, but my impression was that a method needed to at least be defined before it could be called. all getFileSystem() is is a stub:

[PHP]
private static FileSystem getFileSystem();
//New method declarations following. Notice the semicolon following the method
[/PHP]

Essentially, my question is how does the JVM know what getFileSystem() is doing if no concrete functionality is provided. Say I wrote:
[PHP]
public int addOne(int x);
//Again, only a method signature provided, no actual implementation
[/PHP]

It might be obvious from the method name that this function is supposed to return x+1, but since I haven't provided any statements within the function, compiler/jvm wouldn't know what to do with it. It's not so much a question of static/instance methods as methods with and without actual functionality provided by the programmer.

I dunno. Maybe I'm just missing something really simple.

---

### Post by Some Penguin on 2010-04-09
getFileSystem() also has the 'native' keyword, at least in the version I'm seeing.

That stub is a placeholder; the invocation will use native code (i.e. dynamically loaded library).

---

### Post by vik_2010 on 2010-04-09
what - an .so file, or something built into the jvm?

I missed the native clause - but I wouldn't have known what it does anyway.

---

### Post by falconindy on 2010-04-09
[This](http://www.javaworld.com/javaworld/javatips/jw-javatip23.html) explains how a native method could be created.

---

