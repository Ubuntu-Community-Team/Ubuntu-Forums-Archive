---
title: "begining c"
date: 2012-07-23
forum: Programming Talk
---

### Post by scorpious on 2012-07-23
why does the following programme make the value of "stop" 1 no matter what input I provide?

function() does not return anything.

```
#include <stdio.h>

int main() {
    int stop = 0;
    do {
        function();
        printf("type 1 to end");
        stop = scanf("%d", &stop);
        printf("%d", stop);
    }while (stop != 1);
        
    return 0;
}
```

---

### Post by Bachstelze on 2012-07-23
There are many things wrong with this code. For starters, check the man page for scanf(). Its return value is not what you think it is.

---

### Post by scorpious on 2012-07-23
Oh silly me. I put "stop =" unnecessarily. 

You said there were many things wrong? what else did I do wrong? I seems to work fine now.

---

### Post by Bachstelze on 2012-07-23
What happens if you enter 'a'?

---

### Post by scorpious on 2012-07-23
hmmmm......

---

