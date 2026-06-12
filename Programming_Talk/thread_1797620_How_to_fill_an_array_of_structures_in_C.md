---
title: "How to fill an array of structures in C"
date: 2011-07-05
forum: Programming Talk
---

### Post by stamatiou on 2011-07-05
Hey guys,
I have a structure and an array
```
struct identity
{
char name[10];
char secondname[10];
int age;
}humans[100];

```
Now, how can I fill all the contents of the array with a for loop?

---

### Post by Arndt on 2011-07-05
> **stamatiou said:**
> Hey guys,
I have a structure and an array
```
struct identity
{
char name[10];
char secondname[10];
int age;
}humans[100];

```
Now, how can I fill all the contents of the array with a for loop?

```
int i = 4;
humans[i].age = 33;

```

sets one part of one entry. Go from there.

---

### Post by stamatiou on 2011-07-05
> **Arndt said:**
> ```
int i = 4;
humans[i].age = 33;

```sets one part of one entry. Go from there.
```
for(i = 0;i<=10;i++)    {
human[i].name = "Name";
human[i].age = 30;
}
```
Would this work?

---

### Post by slavik on 2011-07-05
> **stamatiou said:**
> ```
for(i = 0;i<=10;i++)    {
human[i].name = "Name";
human[i].age = 30;
}
```
Would this work?
No, go read about strings in C.

---

### Post by Arndt on 2011-07-05
> **stamatiou said:**
> ```
for(i = 0;i<=10;i++)    {
human[i].name = "Name";
human[i].age = 30;
}
```
Would this work?

What values will i take in this loop? What indices of 'human' are valid?

---

### Post by JupiterV2 on 2011-07-05
> **Arndt said:**
> What values will i take in this loop? What indices of 'human' are valid?

I don't recommend using that code. As Slavik points out, you can't assign a string like that to a character array. You will need to use a C standard function like strncpy() to copy the string to your variable. You would decide how many elements are in your array of structures when you declare your variables. I recommend looking into how C strings work, how arrays work and how 'for' loops work before moving into structures. If you know how to populate an array with a for loop then you won't have to ask us how to populate a structure that way.

---

