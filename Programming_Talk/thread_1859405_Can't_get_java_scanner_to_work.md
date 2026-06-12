---
title: "Can't get java scanner to work"
date: 2011-10-13
forum: Programming Talk
---

### Post by backslyder on 2011-10-13
Hi,

I just made the switch from windows to ubuntu. My java programs were working fine in windows. However, now when I run my programs i get this error (I'm using SciTe Text Editor):

```
>java -cp . Test
Type a number: Exception in thread "main" java.util.NoSuchElementException
    at java.util.Scanner.throwFor(Scanner.java:855)
    at java.util.Scanner.next(Scanner.java:1478)
    at java.util.Scanner.nextInt(Scanner.java:2108)
    at java.util.Scanner.nextInt(Scanner.java:2067)
    at Test.main(Test.java:11)
>Exit code: 1
```here's what my code looks like:

>  import java.util.*;

public class Test {
    
    public static void main(String[] args) {
        
        Scanner console = new Scanner(System.in);
        
        System.out.print("Type a number: ");
        
        int a = console.nextInt();
        
        System.out.println("you typed: " + a);
        
    }
    
}  This is just a sample program...it compiles fine, but then this happens when i run it. I've even installed sun's jdk 6 and jre...I'd appreciate any help.

---

### Post by HotCupOfJava on 2011-10-14
Hmmm.... no problem here - but I'm using the OpenJDK instead. It shouldn't have anything to do with your problem, but you don't need to use the "-cp" argument in this case. Simply typing "java Test" will execute the class file if it is in the current directory.

---

### Post by satsujinka on 2011-10-14
it's probably something wrong with your install.
just to test nextLine() doesn't work either right?

---

