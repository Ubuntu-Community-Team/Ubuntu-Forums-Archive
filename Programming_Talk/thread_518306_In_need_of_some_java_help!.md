---
title: "In need of some java help!"
date: 2007-08-05
forum: Programming Talk
---

### Post by Fireblend on 2007-08-05
Hello. I'm currently working on a little Java assignment for University. It runs on console, so no GUI, but I'd like to make it as simple as possible. 

I'd like to see if there's any way to make a little method that would show the classic "Press enter to continue" text or something like that, because there's a lot of text appearing at the same time and it can be really bothering. 

It's ok as it is now, but as I said, I'd like to polish it as much as I can, and that exact method or something similar would really help.

Thanks in advance!

---

### Post by nitro_n2o on 2007-08-05
```
import java.util.Scanner; 

public class Hello {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in); 
        System.out.print("Press enter to continue: "); 
        s.next(); //or s.nextLine(); i forget ;$ 
       // you should also s.close() in real input output situations 
    }

}
```

---

### Post by Kent84 on 2007-08-05
java.sun.com is your friend, especially the APIs

---

### Post by Fireblend on 2007-08-05
> **nitro_n2o said:**
> ```
import java.util.Scanner; 

public class Hello {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in); 
        System.out.print("Press enter to continue: "); 
        s.next(); //or s.nextLine(); i forget ;$ 
       // you should also s.close() in real input output situations 
    }

}
```

Exactly what I was looking for. Thanks!

---

