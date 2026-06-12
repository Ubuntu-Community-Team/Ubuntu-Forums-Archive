---
title: "Undefined Const behaviour"
date: 2012-03-16
forum: Programming Talk
---

### Post by c2tarun on 2012-03-16
```
#include <stdio.h>

main(){
        const int i=123;
        const int *p;
        p=&i;
        int *np;
        np = (int*)p;
        *np = 98273987;
        printf("%d\n",i);
}

```



According to my understanding the value of a const variable is constant and cannot be changed. But on executing the above program I am getting the output as 98273987 which is impossible, I should get an error. Can anyone please explain me this behavior.

---

### Post by muteXe on 2012-03-16
what happens if you declare *np as const?

---

### Post by muteXe on 2012-03-16
edit:  I am not getting the same output as you report, i'm getting 123...

---

### Post by c2tarun on 2012-03-16
Which compiler are you using? I am using gcc4.6.1

---

### Post by Zugzwang on 2012-03-16
"const" means that the value *is supposed to be* constant, not that the compiler will actually enforce it to be constant. In the line " np = (int*)p;" you explicitly cast the "const" away, telling the compiler that you don't want it to care about constness in this case. Overwriting a const variable is a bad idea as optimizations by the compiler might or might not affect the value of the constant variable (I might be mistaken here, but it is in any case a bad idea).

---

### Post by muteXe on 2012-03-16
visual studio 2010.
incidently, if you do my suggestion in post #2 the compiler *does* complain.

---

### Post by c2tarun on 2012-03-16
> **Zugzwang said:**
> "const" means that the value *is supposed to be* constant,
Sorry I am not able to understand the above line :( can you please explain a bit.

> 
 not that the compiler will actually enforce it to be constant. In the line " np = (int*)p;" you explicitly **cast the "const" away**, telling the compiler that you don't want it to care about constness in this case.What do you mean by casting the const away? 

> **Overwriting a const variable** is a bad idea as optimizations by the compiler might or might not affect the value of the constant variable (I might be mistaken here, but it is in any case a bad idea).
What do you mean by Overwriting a const variable?

---

### Post by codemaniac on 2012-03-16
const variable is constant , as long as you are not manipulating its value via its base address .
see the code below .
```

#include <stdio.h>

main(){
        const int i=123;

        int *p;
        p=&i;
        *p=789;
        printf("%d\n",i);
}
```

---

### Post by muteXe on 2012-03-16
When you declare something as const, you are actually only making a suggestion to the compiler to do it.

On casting: [http://www.cprogramming.com/tutorial/const_correctness.html](http://www.cprogramming.com/tutorial/const_correctness.html)

---

### Post by Arndt on 2012-03-16
> **c2tarun said:**
> 
What do you mean by casting the const away? 



(int *)p is a cast, and since it doesn't use the keyword 'const', you're telling the compiler that it is allowed to modify things pointed to by p. That is a lie, since you declared i const. In C you're allowed to lie to the compiler like this, but you are responsible for the consequences. A proper cast would be (const int *)p.

---

### Post by c2tarun on 2012-03-16
> **Arndt said:**
> (int *)p is a cast, and since it doesn't use the keyword 'const', you're telling the compiler that it is allowed to modify things pointed to by p. That is a lie, since you declared i const. In C you're allowed to lie to the compiler like this, but you are responsible for the consequences. A proper cast would be (const int *)p.

Thanks for the explanation guys :) I got it now.
I am marking this thread as solved.

---

