---
title: "Structure data and string don't pass condition statement"
date: 2008-12-13
forum: Programming Talk
---

### Post by subdee on 2008-12-13
Hello all. I have a function where I'm comparing a field from a structure to a string, and although when I output them they show the exact same string, they don't pass the condition as true. Can you help me out?  Here's the function:

```

void check_stud(stud *p, char sname[]) {
     
     int check;
     if (p == NULL)  {
   	   printf("\n NO DATA to print!!!  ");
   	   return;
    }
    printf(sname);
    printf(p->name);
    if (sname == p->name)
    {
             printf("  The student's NAME is: %s . His studentID is: %d\n", p->name, p->id);
             printf("  The student's AGE is: %d, his GPA is: %f, and his SEX is: %c\n\n", p->age, p->gpa, p->sex);
             return;
    }
    else
    {
             printf("   The student does not exist. \n");
             return;
    }
}

```

and the structure:
```

typedef struct {
		int	id;
		char name[50];
		int age;
		float gpa;
		char sex;
} stud;

```

---

### Post by subdee on 2008-12-13
Never mind, I used strcmp to compare.  :)  :)  :cheers:

---

### Post by pp. on 2008-12-13
Please mark your thread as solved, then.

---

