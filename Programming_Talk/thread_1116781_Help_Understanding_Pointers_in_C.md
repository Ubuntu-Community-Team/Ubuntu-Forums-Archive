---
title: "Help Understanding Pointers in C"
date: 2009-04-05
forum: Programming Talk
---

### Post by nite owl on 2009-04-05
Ive come across this tutorial found here: 
[http://home.netcom.com/~tjensen/ptr/ch1x.htm](http://home.netcom.com/~tjensen/ptr/ch1x.htm)

It gives a coding example:

```

#include <stdio.h>

int j, k;
int *ptr;

int main(void)
{
    j = 1;
    k = 2;
    ptr = &k;
    printf("\n");
    printf("j has the value %d and is stored at %p\n", j, (void *)&j);
    printf("k has the value %d and is stored at %p\n", k, (void *)&k);
    printf("ptr has the value %p and is stored at %p\n", ptr, (void *)&ptr);
    printf("The value of the integer pointed to by ptr is %d\n", *ptr);

    return 0;
}

```

My question is to do with the printf statements:
```
printf("k has the value %d and is stored at %p\n", k, (void *)&k);

```

When I run the program it says for this line of code, "k has the value of 2 and is stored at 00404014". How are they getting 2? I don't mean why is it 2, but how is it actually getting input there, I don't understand the coding?

I know its replacing %d with 2 and %d just means a decimal variable will go there, but wheres the program telling it which variable to put there?

---

### Post by wicky_ts on 2009-04-05
here the statemant printf is going to print is what between inverted commas.
"k has the value %d and is stored at %p\n"

next you are passing two variables to this statemant
 k, (void *)&k

printf know the first varable should be printed as a decimal value and the next one as address. it can identify %d and %p. and put the variables in the same order

---

### Post by rba1988 on 2009-04-05
> **nite owl said:**
> Ive come across this tutorial found here: 
[http://home.netcom.com/~tjensen/ptr/ch1x.htm](http://home.netcom.com/~tjensen/ptr/ch1x.htm)

It gives a coding example:

```

#include <stdio.h>

int j, k;
int *ptr;

int main(void)
{
    j = 1;
    k = 2;
    ptr = &k;
    printf("\n");
    printf("j has the value %d and is stored at %p\n", j, (void *)&j);
    printf("k has the value %d and is stored at %p\n", k, (void *)&k);
    printf("ptr has the value %p and is stored at %p\n", ptr, (void *)&ptr);
    printf("The value of the integer pointed to by ptr is %d\n", *ptr);

    return 0;
}

```

My question is to do with the printf statements:
```
printf("k has the value %d and is stored at %p\n", k, (void *)&k);

```

When I run the program it says for this line of code, "k has the value of 2 and is stored at 00404014". How are they getting 2? I don't mean why is it 2, but how is it actually getting input there, I don't understand the coding?

I know its replacing %d with 2 and %d just means a decimal variable will go there, but wheres the program telling it which variable to put there?

it's part of the printf function. If you're already studying functions, you can see here that the printf function accepts certain arguments. First is the string it will print (the one in the " " ) and the corresponding variables/values in which it will replace the %d with. It's arranged in a sequential order in such a way that "k" will be passed to the first %d and (void *)&k will be passed to %p. I hope I said it right.O_o

---

### Post by nite owl on 2009-04-05
thanks a lot guys for the prompt replies, has really helped me, I just have one more question. What is with the (void *) &k, why couldn't it just be &k, why is (void *) there?

---

### Post by PmDematagoda on 2009-04-05
> **nite owl said:**
> thanks a lot guys for the prompt replies, has really helped me, I just have one more question. What is with the (void *) &k, why couldn't it just be &k, why is (void *) there?

I don't think there is any difference if you use &k or cast the memory address of k to void due to the fact that %p is used to display pointer values regardless of it's type, and also since a memory address is just a memory address, regardless of what type it has. Now if you wanted to display something that required a pointer/data of type void, you would try and cast the pointer/data to void, although it may produce some undesired results based on the function and what it does.

---

### Post by Krupski on 2009-04-05
> **nite owl said:**
> I know its replacing %d with 2 and %d just means a decimal variable will go there, but wheres the program telling it which variable to put there?

Look at the line of your code:

```

     printf("k has the value [COLOR="Red"]**%d**[/COLOR] and is stored at [COLOR="SeaGreen"]**%p**[/COLOR]\n", [COLOR="Red"]**k**[/COLOR], [COLOR="SeaGreen"]**(void *)&k**[/COLOR]);

```

Note the color hilight: The colored format specifier for printf matches the variable being printed at that spot.

For example, the red one (%d) is the "integer" specifier and it's being replaced by the contents of the integer VARIABLE "k".

If "k" instead contained "5", then the program would print "k has the value 5...."

Make sense?

-- Roger

p.s. you don't need the "void*"... this line is equally OK:

```

     printf("k has the value [COLOR="Red"]**%d**[/COLOR] and is stored at [COLOR="SeaGreen"]**%p**[/COLOR]\n", [COLOR="Red"]**k**[/COLOR], [COLOR="SeaGreen"]**&k**[/COLOR]);

```

---

### Post by scg on 2009-04-06
Hello, here is a great tutorial specifically for c pointers.

[http://boredzo.org/pointers/](http://boredzo.org/pointers/)

I would try to explain things, but this does a much better job.

---

