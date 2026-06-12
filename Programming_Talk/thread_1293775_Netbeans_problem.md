---
title: "Netbeans problem"
date: 2009-10-17
forum: Programming Talk
---

### Post by hyperAura on 2009-10-17
hello there, i've downloaded Netbeans IDE to write a program in java. the following is just to try out how to pass arguments in netbeans but something seems to go wrong in netbeans. working environment is windows and i've also installed jdk1.6.

public class ArgsExmpl {
    public static void main(String [] args)
   {
        System.out.println(args[0]);
     }
}

the error i'm getting is the following:

Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 0
        at ArgsExmpl.main(ArgsExmpl.java:12)
Java Result: 1

---

### Post by OpenGuard on 2009-10-17
```
public class ArgsExmpl {
    public static void main(String args[]) {
        System.out.println(args[0]);
    }
}

```

How about this ?

---

### Post by hyperAura on 2009-10-18
thats how i typed it in netbeans.. i just re-typed here but not correctly..

my code in linux works fine but in netbeans in windows it just wont pass the arguments..
i've tried printing out args.length just to see if it gets anything but the output is 0..

---

### Post by OpenGuard on 2009-10-18
Does it work if you compile it via command-line ( by manually typing in javac and specifying your source file ) ? Oh, and .. which version of Java JRE/JDK you are using ( both platforms ) ?

---

### Post by hyperAura on 2009-10-18
it works fine through the command line.. ive attached a picture of what versions are installed and platform

---

### Post by OpenGuard on 2009-10-18
> **hyperAura said:**
> it works fine through the command line.. ive attached a picture of what versions are installed and platform

Replace javaw with java and it should work just fine.

---

### Post by hyperAura on 2009-10-18
ive tried by changing only the first one but it just keep adding javaw at the end on its own

---

### Post by jespdj on 2009-10-19
You get an ArrayIndexOutOfBoundsException because when you run the program from NetBeans, you're not passing any command line arguments to the program. So args is an array with zero elements. If you try to access the first element, args[0], then you get an exception, because that element doesn't exist.

---

### Post by hyperAura on 2009-10-19
i pass arguments into the project properties but the problem is that Netbeans seems to not picking them up..

---

