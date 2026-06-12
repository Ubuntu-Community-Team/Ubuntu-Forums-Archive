---
title: "Compiling Java in the Terminal"
date: 2008-02-25
forum: Programming Talk
---

### Post by nbitting on 2008-02-25
Hello everyone...I installed sun's java6 jdk and everything works great inside Eclipse.  I can compile and run my apps just fine.  My only issue is that I keep getting errors when I try running a java file from the terminal.  I just did the HelloWorld example to test this out and here's my code:

```

public class HWClass {

	public static void main(String[] args) {
		System.out.println("Hello, World!");

	}

}


```

Here's my output in the terminal:
```

nbitting@nbitting-laptop:~$ javac HelloWorld.java
HelloWorld.java:1: class HWClass is public, should be declared in a file named HWClass.java
public class HWClass {
       ^
1 error
nbitting@nbitting-laptop:~$

```

OR

```

nbitting@nbitting-laptop:~$ java HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld
nbitting@nbitting-laptop:~$ 

```

Any help would be greatly appreciated!

Thanks.

---

### Post by ZylGadis on 2008-02-26
Public classes in Java should have the same name as the file they are located in. Either change the name of your source file to HWClass.java , or change the name of your class to HelloWorld, or remove the public modifier.

---

### Post by imdano on 2008-02-26
^ What he said.  Eclipse is letting you get away with breaking a rule you shouldn't be breaking.  It's java coding convention to name a .java file after the main public class contained in it.

---

### Post by bcl1713 on 2008-02-26
just to clarify ZylGadis' post though: you won't need to remove the public modifier if you rename the file or class.  It's **always** a good idea to follow code convention and every public class and java should be in its own file named for the class.  HWClass should be in HWClass.java or HelloWorld (class) should be in HelloWorld.java.

---

