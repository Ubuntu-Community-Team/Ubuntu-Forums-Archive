---
title: "Java: access a folder shared with Windows on both Linux and Windows"
date: 2013-08-17
forum: Programming Talk
---

### Post by Erik1984 on 2013-08-17
In my Java project I want to store data in a folder shared between Windows and Linux called "Web" (or a subfolder of that folder). The folder resides on a shared NTFS data partition. The point is that I want to be able to run the application in both systems and work on the same data. I have the same editor on both systems (Netbeans) but I don't want to store the data in the project folder or working directory of the program.

In Windows the path to that folder is:
```
I:\Web
```

In Ubuntu it's mounted as
```
/media/win8data/Web
```

Those paths are different so when I run the code with the Windows path it obviously does not work. The Linux mount path would not make sense on Windows. Is it possible in Java to check which operating system is being used and define the proper root for the path?

---

### Post by Azdour on 2013-08-17
You should be able to use System.getProperty("os.name") to retrieve the operating system it is running on and then decide how to construct the path to your shared folder

---

### Post by DarkAmbient on 2013-08-17
Another solution could be to make use of "org.apache.commons.lang.SystemUtils" contant "IS_OS_UNIX"

```
if (SystemUtils.IS_OS_UNIX) {
    // TADA
} else {
    // BOO
}
```

[SIZE=1]Don't mind my mild humor[/SIZE]

---

### Post by r-senior on 2013-08-17
What about an environment variable, defined with the appropriate path on each OS, then accessed via System.getenv() in your program?

Or, similar idea, pass in a property (java -D...) or command line argument when you invoke the program?

---

### Post by ofnuts on 2013-08-18
> **Azdour said:**
> You should be able to use System.getProperty"os.name") to retrieve the operating system it is running on and then decide how to construct the path to your shared folder
+1 to that, this is the standard way.

Also use System.getProperty("file.separator") at the proper places(*),  and the java.io.File methods to handle file names.


(*) In practice Windows system calls handle forward slashes just as well as back slashes so the only place where "/" v.s. "\" is important is when handling file paths in user input or config files.

---

### Post by Erik1984 on 2013-08-18
Thanks all! I'll think I go with the System.getPropery"os.name".

---

