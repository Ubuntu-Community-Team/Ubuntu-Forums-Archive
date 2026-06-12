---
title: "C Programming - VERY simple password entry program..."
date: 2011-03-02
forum: Programming Talk
---

### Post by squareff255 on 2011-03-02
Why won't this work!? Every time I run it, it prints out: Invalid, even if I put in the correct pin...
                                  
```

#include <stdio.h>

int main(void)
{
  float number = 042646;
  int pass;
  printf("Enter the PIN.\n");
  scanf("%d", &pass);

  if (pass == number)
    {
      printf("Correct\n");
    }
  else
    {
      printf("Invalid\n");
    }
  return 0;
}

```

---

### Post by Tony Flury on 2011-03-02
> **squareff255 said:**
> Why won't this work!? Every time I run it, it prints out: Invalid, even if I put in the correct pin...
                                  
```

#include <stdio.h>

int main(void)
{
  float number = 042646;
  int pass;
  printf("Enter the PIN.\n");
  scanf("%d", &pass);

  if (pass == number)
    {
      printf("Correct\n");
    }
  else
    {
      printf("Invalid\n");
    }
  return 0;
}

```


have you actually printed out the enetered "pass" and your stored "number" when you do the comparison ?

A few things spring to mind : 

1) comparing a float to an int - because of how floats are stored, there might be a chance that your "042646" is not actually stored accurately - it might be stored as 424645.9999999999 - which of course wont compare with the int (== means exactly equal and is rarely a good idea with floats) - consider storing both values as ints.

2) Does the leading zero on your stored number do something else to the number (is that the inidication that the number following is Octal - I might be wrong).

3) since the actual value is irrelevant, and you are actually interested that the user eneters the right set of characters - maybe you should be storing and fetching chars, and using character or string comparisons.

---

### Post by sanderj on 2011-03-02
First of all: is this your homework we're doing?

Comparing an int with a float? Does that work in C? I guess not.

And the leading 0 in an int will of course disappear. You can check yourself with 

```
printf("The number is: %d\n",number);

```

Solution: put both number and pass in string (char[20]), and use a string compare (strcmp?).


EDIT: after posting this, I saw you had already received about the same answer.

---

### Post by bapoumba on 2011-03-02
Moved to PT.

---

### Post by Queue29 on 2011-03-02
Tony Flury was on the right track about the leading zero:

```

#include <stdio.h>

int main() {
    float n = 042646;
    printf("n: %f\n", n);
    return 0;
}

```

```
$ ./a.out 
n: 17830.000000

```

---

### Post by Arndt on 2011-03-02
> **sanderj said:**
> 

Comparing an int with a float? Does that work in C? I guess not.


Of course it works, in some sense (otherwise there would be a compiler error), but to know exactly what happens, consult the language reference.

---

### Post by Tony Flury on 2011-03-02
> **Queue29 said:**
> Tony Flury was on the right track about the leading zero:

```

#include <stdio.h>

int main() {
    float n = 042646;
    printf("n: %f\n", n);
    return 0;
}

```

```
$ ./a.out 
n: 17830.000000

```

Uggh - obscure C knowledge dragged up from about 15 years ago - so why can't i remember my niece's birthdays :-(

Thanks for confirming though.

---

