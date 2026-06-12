---
title: "I can't create an instance of File class in java"
date: 2013-07-01
forum: Packaging and Compiling Programs
---

### Post by pavelexpertov on 2013-07-01
Basically, I am trying to practice creating instances of classes in java and I started learning how to create files and its instance. I believe my compiler has a glitch, because I checked others' examples of code and it's literally the same as mine. Here is my code:
```


import java.io.*;
class File
{
    public static void main(String[] args)
    {
        File f; 
        f = new File("File.txt");
        
    }
}

```
and here is my error I got after compiling the file:

[CODE]
 
pavel@pavel-EasyNote-TJ67:~/myjava$ javac File.java
File.java:7: cannot find symbol
symbol  : constructor File(java.lang.String)
location: class File
		f = new File("File.txt");
		    ^
1 error



[CODE]
Is it wrong or my compiler decided to do funny things lolz.

---

### Post by mendhak on 2013-07-10
Your class is called File and in your Main, you are calling File (I assume the java.io.File).  However, since your class is called File, you are effectively calling yourself.  Rename your class from the generic 'File' to something like 'Test' or 'AnythingButFile'.

---

### Post by ubuntpetbe2 on 2013-08-06
You can also change the constructor File to java.io.File to get around it.

---

### Post by amy4 on 2014-06-14
Its seems some issue with java installation. If you are using IDE like eclipse then make sure JRE and JDK set correctly. The above code [[COLOR=#000000]to create file in java [/COLOR]]("http://tutorialswithexamples.com/java-io-tutorial/how-to-create-file-in-java/")seems correct also use createNewFile() method to actually create file.

---

