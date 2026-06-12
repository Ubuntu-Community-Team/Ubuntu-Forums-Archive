---
title: "java Reflection in netbeans"
date: 2010-05-10
forum: Programming Talk
---

### Post by Xender1 on 2010-05-10
So I have a .class file in a folder on my computer. I want to write a program that uses Reflection to look at this .class and get its methods etc. Im just having some trouble starting out on how to do this. I am using 
```

Class c = Class.forName(name);

```
But, I am unsure what name should be. I tried doing the directory like /home/name/Documents/myclass.class   but that did not work, I also tried putting it in the same folder as my main.java (the src folder) and still no luck. 

Thanks

---

### Post by Some Penguin on 2010-05-10
(1) The location of the file should match its place in the class hierarchy.
(2) The file hierarchy should be reflected in the classpath.
(3) The official name of a class is the same as how you might import it.

e.g. if you unpacked the Collections Framework, you might 

(1) have 
     some_dir/java/
     some_dir/java/util
     some_dir/java/util/LinkedList.{java,class}

(2)  some_dir would need to be in the classpath (ignoring the fact that it's a built-in)

(3) the class name would be java.util.LinkedList

---

### Post by Reiger on 2010-05-10
Although if you can import the class there's a much easier way:
```

Class cls = MyClassName.class;

```

---

### Post by Xender1 on 2010-05-10
trying to do the MyClassName.class way, I just keep getting undefined identifier.

I tried it a new way, I put it in the same folder as my Main.java so now I do not need to worry about my class path. Everytime I get the name though, I keep getting java.lang.String and I know for a fact that its name is not Sring.
```

        String MyClassName = "explorethis";
        Class c = MyClassName.getClass();
        String name = c.getName();
        System.out.println(name);

```
also, if MyClassName = "explorethis.class" its the same response, java.lang.String;

---

### Post by Xender1 on 2010-05-11
I feel kind of dumb, all along I was doing the write thing but its just Netbeans being silly! I wrote my own .java in a different folder and put myclass.class in that folder aswell.
```


import java.lang.Class;

public class Main {

    public static void main(String[] args) {
        try {
            Class myClass = Class.forName("myclass");
        } catch (ClassNotFoundException ex) {
            System.out.println("ClassNotFoundException");
        }

    }

}

```
I do not get the catch statement, meaning that it see's it! Very good! Now I am just confused as to why when I put myclass.class in the myproject/src/myproject folder it throws it...is there some special folder I have to put it in so it see's it?

---

