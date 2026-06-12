---
title: "struct c"
date: 2013-02-11
forum: Programming Talk
---

### Post by cookie9 on 2013-02-11
hello everyone
can somebody tell how can i create multiple struct pointers and how to get their addresses using a for loop? acrually i want something like an array of structs but because i dont know how many structs i am going to need i tried something like a struct pointer
thank u

---

### Post by Bachstelze on 2013-02-11
A struct is an object like any other, so you can certainly make a pointer to it just like you make a pointer to any other object. Try it. :)

---

### Post by cookie9 on 2013-02-11
oh thank u! but how can i get two sequential addresses of two different structs? i tried everything but i really dont know how..

---

### Post by Bachstelze on 2013-02-11
You will have to explain more precisely what you mean by that because I have no idea...

---

### Post by cookie9 on 2013-02-11
ok i just need a struct pointer that i can move it to the next address using a for loop! i really dont know how to explain it better but anw thank u! :)

---

### Post by r-senior on 2013-02-11
It sounds to me as though you are looking for a linked list:

[http://www.cprogramming.com/tutorial/c/lesson15.html](http://www.cprogramming.com/tutorial/c/lesson15.html)

---

### Post by ofnuts on 2013-02-12
> **cookie9 said:**
> hello everyone
can somebody tell how can i create multiple struct pointers and how to get their addresses using a for loop? acrually i want something like an array of structs but because i dont know how many structs i am going to need i tried something like a struct pointer
thank u
```

#define SIZE 10

struct someStruct {
    long a;
    long b;
    long c;
};

struct someStruct *dynamicArray=malloc(sizeof (struct someStruct) * SIZE);

for (int i=0;i<SIZE;i++) {
    dynamicArray[i].a=i;
}

```

---

### Post by cookie9 on 2013-02-12
r-senior it seems that list is what i needed! thank u! ofnuts thank u to! :)

---

