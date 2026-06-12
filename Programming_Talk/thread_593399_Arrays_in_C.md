---
title: "Arrays in C"
date: 2007-10-27
forum: Programming Talk
---

### Post by daniel of sarnia on 2007-10-27
Hey I'm learning C, and I was hoping someone could help me out trying to make an array that stores then prints doubles. I thought it would be easy, but I guess I've messed up somewhere. It's odd to because I can make it work with and int. 

```


#include <stdio.h>

#define SIZE 10

int main(void)
{

    double val[SIZE], ans;
    int i;
    

    
    for( i=0 ; i<SIZE ; i++)
    {   
        printf("\nEnter a double number: ");
        scanf("%f \n", &val[i]);
    }
    

    for( i=0 ; i<SIZE ; i++)
        printf("%f \n", val[i]);

    return 0;
}

```

Thanks in advance, I think it's something really simple to. But I can get it to work :confused:

---

### Post by WakkiTabakki on 2007-10-27
Since your using double your formatting string should be %lf (as in **L**ong **F**loat), e.g
```
scanf("%lf", &val[i]);
```

Same goes for the printf-line, ofcourse...

/N

---

### Post by daniel of sarnia on 2007-10-27
Thank so much, ahhh I've read the before too. Little things I for get make me crazy hahaha

---

