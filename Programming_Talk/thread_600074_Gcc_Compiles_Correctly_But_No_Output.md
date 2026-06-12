---
title: "Gcc Compiles Correctly But No Output"
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

### Post by lucia_engel on 2007-11-01
Try this:
```
./test
```

It worked for me.

---

### Post by LaRoza on 2007-11-01
> **tcooper4 said:**
> 
I then compile it:
```
$ gcc test.c -o test
$ test
```
and I get nothing out  any ideas?

You have to add "./" before running it. You cwd is not usually in your PATH, and it shouldn't be. "." means your current directory.

---

