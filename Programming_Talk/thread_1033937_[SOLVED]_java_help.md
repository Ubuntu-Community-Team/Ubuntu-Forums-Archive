---
title: "[SOLVED] java help"
date: 2009-01-07
forum: Programming Talk
---

### Post by aszxcv on 2009-01-07
my code
[PHP]

public class gohome {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        int x = Math.round (Math.PI * 20.0);
        System.out.println(x);

    }

}




[/PHP]

error messages
[PHP]

found   : long
required: int
        int x = Math.round (Math.PI * 20.0);
1 error
BUILD FAILED (total time: 0 seconds)




[/PHP]

---

### Post by badperson on 2009-01-07
Hi,

the expression you have is pi times 20.0, that's not an int value. 

change to 
```
long x = Math.round (Math.PI * 20.0);
```
that should work. (it also might be a double, not sure...)
bp

---

### Post by aszxcv on 2009-01-07
i solved it i was to use (int) typecast

---

