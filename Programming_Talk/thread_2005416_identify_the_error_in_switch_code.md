---
title: "identify the error in switch code"
date: 2012-06-17
forum: Programming Talk
---

### Post by Bachstelze on 2012-06-17
Fixed this code for you:

```
#include <stdio.h>

int main(void)
{
    int c, t;
    printf("Enter the number of subjects he has failed in: ");
    scanf("%d%d", &c, &t);

    switch(c)
    {
        case 1:
            switch(t>3)
            {
                case 1:
                    printf("\nNo grace");
                    break;
                case 0:
                    printf("\nGrace of 5 marks per subject");
                    break;
            }
            break;

        case 2:
            switch(t>2)
            {
                case 1:
                    printf("\nNo grace");
                    break;
                case 0:
                    printf("\nGrace of 5 marks per subject");
                    break;
            }
            break;

        case 3:
            switch(t>1)
            {
                case 1:
                    printf("\nNo grace");
                    break;
                case 0:
                    printf("\nGrace of 5 marks per subject");
                    break;
            }
            break;
    }
}

```

Now what exactly is the problem?

---

### Post by ofnuts on 2012-06-17
A rather unusual use of the switch statement.

```
switch(t>2) {
    case 1:
        printf("\nNo grace");
        break;
    case 0:
        printf("\nGrace of 5 marks per subject");
        break;
}

```is better written:
```

if (t>2) {
    printf("\nNo grace");
} else {
    printf("\nGrace of 5 marks per subject");
}

```

---

### Post by 3Miro on 2012-06-17
The code wouldn't even compile without replacing s with t. Then the only time one would use "switch" instead of "if" is for a homework.

- Is this a homework question?
- What is this code supposed to do?
- You should really use "if" instead of "switch" for things like (t>3).
- I would also add another "\n" in the end of all the printf statements as it will make the output look a bit better.

---

