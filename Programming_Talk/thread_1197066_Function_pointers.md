---
title: "Function pointers"
date: 2009-06-25
forum: Programming Talk
---

### Post by Rij on 2009-06-25
Hello all,

I am hoping to get some help from you regarding function pointers. I have no idea how to do this. This is a basic question so I hope you will not be offended by my post! :)

I have N functions, all having similar signature:
```

void func_i() {
/* do something */
}

```

In my main, I want to declare an array (of size N) of function pointers. Each element in the array will point to the function as declared above. Then I want to declare a loop in main from where I want to call ith function by calling the ith array element.

This is the lame attempt I made in coding. I am so out of depth that I dont even know where to go from here.

```

typedef void (*ptr2fn) ();

void func_1() {
}

void func_2() {
}

ptr2fn array[2] = {NULL};

int main() {
   array[0] = &func_1;
   *array[0] ();
}


```

When I compile this, I get the error:
```

error: void value not ignored as it ought to be

```

---

### Post by kjohansen on 2009-06-25
Try getting rid of the * in "*array[0]()"


```

typedef void (*ptr2fn) ();

void func_1() {
}

void func_2() {
}

ptr2fn array[2] = {NULL};

int main() {
   array[0] = &func_1;
   array[0] ();
}

```

---

### Post by Can+~ on 2009-06-25
```
*array[0]();
```

Should be
```
(*array[0])();
```

Anyway, I remember learning all about function pointers from:
[http://www.newty.de/fpt/fpt.html](http://www.newty.de/fpt/fpt.html)

---

### Post by Rij on 2009-06-25
Thanks folks for the suggestions. For now, I have been able to make it work. Even extended it to 2D array. But my foundation remains shaky at best. 

Need to revisit this concept later.

---

