---
title: "[SOLVED] [C] Strucutres/Threads"
date: 2008-10-10
forum: Programming Talk
---

### Post by carrie.peary on 2008-10-10
Having some trouble passing a structure with two values (a, b) to a thread function. The values are different and I can't figure out why. Here's the two important segments:

```

for (i=0;i<M;i++)
      for (j=0;j<N;j++)
          struct v *data = (struct v *)malloc(sizeof(struct v));
          data->a = 4;
          data->b = 2;
          printf("       A is: %d B is: %d\n",data->a,data->b);
          pthread_create(&tid[size],&attr,runner,(void *)&data);


```

```

void *runner(void *param)
{
int g,h;
struct v *my_data;
my_data = (struct v*) param;
g=my_data->a;
h=my_data->b;
printf("       G is: %d H is: %d\n",g,h);
pthread_exit(0);
}

```

Oh, my output is:

```

A is: 4 B is: 2
         I is: 134520840  J is: 0
A is: 4 B is: 2
         I is: 134520840  J is: 1
A is: 4 B is: 2
         I is: 134521920  J is: 2
A is: 4 B is: 2
         I is: 134522240  J is: 3
A is: 4 B is: 2
         I is: 134522560  J is: 4
A is: 4 B is: 2
         I is: 134522720  J is: 5
A is: 4 B is: 2
         I is: 134523040  J is: 6
A is: 4 B is: 2
         I is: 134520840  J is: 7
A is: 4 B is: 2
         I is: 134520840  J is: 8

```

Any help is greatly appreciated. Thanks!

---

### Post by dribeas on 2008-10-10
In case someone else reads this, and even you have it solved, I would guess that you are passing a pointer to a pointer to your struct, but you are casting it back to a pointer of the struct:

```

pthread_create(&tid[size],&attr,runner,(void *)&data);

```

should probably be:

```

pthread_create(&tid[size],&attr,runner,(void *)data);

```

as data is already of type 'struct v *'. Anyway, it would be interesting having the real solution if you could post it.

---

