---
title: "Gcc Compiles Correctly But To Output"
date: 2007-11-01
forum: Programming Talk
---

### Post by tcooper4 on 2007-11-01
I have a very simple c program:
```
#include <stdio.h> 
void main(void)
{ 
  printf("sweet it worked");
}
```

I then compile it:
```
$ gcc test.c -o test
$ test
```
and I get nothing out  any ideas?

---

### Post by vambo on 2007-11-01
Not sure what you mean by nothing out. If the compiler didn't give you any error messages you should have a **test** file in the directory you compiled in then just

```
./test
```

---

### Post by nanotube on 2007-11-02
> **tcooper4 said:**
> I have a very simple c program:
```
#include <stdio.h> 
void main(void)
{ 
  printf("sweet it worked");
}
```

I then compile it:
```
$ gcc test.c -o test
$ test
```
and I get nothing out  any ideas?

you must run ```
./test
```
there's a built-in binary in /usr/bin/test, and that's what you are executing when you just run ```
test
```

that's your problem :)

---

