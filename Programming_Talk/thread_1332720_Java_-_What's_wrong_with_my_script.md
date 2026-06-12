---
title: "Java - What's wrong with my script?"
date: 2009-11-20
forum: Programming Talk
---

### Post by KaleXD on 2009-11-20
```
class Loop {
    public static void main (String[] args) {
        int num = 0;
        for(int i = 1; i < 4; i++) {
            System.out.printIn("Outer Loop i=" + i);
            
            for(int j = 1;j < 4; j++) {
                System.out.printIn("\tInner Loop j=" +j);
                System.out.printIn("\t\tTotal num="+ (++num));
            }
        }
    }
}
```i get this error:
[IMG]http://i499.photobucket.com/albums/rr352/KaleXD/Compilererror-1.jpg[/IMG]




and now whenever i try to run a compiled .java i get this error:
[IMG]http://i499.photobucket.com/albums/rr352/KaleXD/recurringerror.jpg[/IMG]


System Specs: 

Manufacturer: Acer 
    Model: Aspire 7720     
Total amount of system  memory: 4.00 GB RAM    
OS: Windows Vista Ultimate 64-bit 
   Processor: Intel Core 2 Duo @ 1.67GHz



i'm completely at a loss towards what wrong.

---

### Post by doas777 on 2009-11-20
I think it shoudl be 
System.out.println where the last two chars are 'l' (L) and 'n' (N) for line, not IN.

---

### Post by KaleXD on 2009-11-20
oh my god.

thank you so much, this had me frustrated out of my mind. :D:D:D:D:D:D:D:D

---

