---
title: "Java: equals method for comparing two integers"
date: 2009-07-09
forum: Programming Talk
---

### Post by Igniteflow on 2009-07-09
Hi,
I've run into a problem I don't really understand.  I've used the equals method before for comparing integers and it's worked fine.  Now I'm trying to compare two integer values from separate integer arrays as follows:

[PHP]
for ( int i = 0 ; i < x.length; i++ ) { 
    for ( int j = 0 ; j < y.length; j++ ) {
         if (x[i].equals(y[j])) {
             // stuff here
         }
    }
}
[/PHP]

But the compiler doesn't like it, saying "Cannot invoke equals(int) on the primitive type int".  Can anyone help me to compare these two values, I've done the hard part of the algorithm so this should be simple, but just can't figure it out.

Thanks in advance

---

### Post by baizon on 2009-07-09
The equals method compare 2 objects, but you got an int (instance), so that's why he don't like it. Use equals only if you want to compare objects. In this case use:
```

for ( int i = 0 ; i < x.length; i++ ) { 
    for ( int j = 0 ; j < y.length; j++ ) {
         if (x[i] == y[j]) {
             // stuff here
         }
    }
}  
``` 
An example for comparing 2 Integer objects:
```

Integer[] x = {1, 2};
Integer[] y = {3, 4};
boolean b = x[1].equals(y[1]);
```

---

### Post by smartbei on 2009-07-09
Have you tried ==?
```

for ( int i = 0 ; i < x.length; i++ ) { 
    for ( int j = 0 ; j < y.length; j++ ) {
         if (x[i] == y[j])) {
             // stuff here
         }
    }
} 

```

---

### Post by Igniteflow on 2009-07-09
Ah hah!  I had previously tried the == operator and thought it wasn't working, but I can see now that I had actually made a mistake in the main algorithm and it was working correctly after all.  Thanks for drawing my attention to it!!!

---

