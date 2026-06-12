---
title: "struct in c"
date: 2013-05-23
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-23
i am writing a struct. but initialization not work correctly.
what is wrong!

```

typedef struct {
    int userIdNumber;
    char* userName;
    int isThere;

}client;
client clientList[MAX_USER];
int main(int argNum , char **args)
{
    int i;
    for(i=0;i<MAX_USER;i++)
    {
        clientList[i].userName=NULL;
        clientList[i].userIdNumber=-1;
        clientList[i].isThere=0;
    }
}

```

---

### Post by spjackson on 2013-05-23
There is nothing wrong. What makes you think that there is?

---

### Post by ferizhandi on 2013-05-23
because use it in condition, and works unexpectedly.

---

### Post by ofnuts on 2013-05-23
Then show us where/how you use it later.

---

### Post by ferizhandi on 2013-05-23
tanks, my problem is solved , i did a mistake.

---

