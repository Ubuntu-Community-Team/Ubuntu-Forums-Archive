---
title: "malloc acting weird"
date: 2011-03-11
forum: Programming Talk
---

### Post by ubu@ on 2011-03-11
Hi,

*malloc(1) *and *malloc(4) *returns the same size of block, I checked it by decreasing pointers. for example:


```
int main(){
  char *str1 , *str2 , *str3, *str4;
  str1 = (char*) malloc(1);
  str2 = (char*) malloc(2);
  str3 = (char*) malloc(4);
  str4 = (char*) malloc(3);
  printf("str1 = %d\n", (int)str1); 
  printf("str2 = %d\n", (int)str2);
  printf("str3 = %d\n", (int)str3);
  printf("str4 = %d\n", (int)str4);
  printf("malloc(1) size = %d\n", (int)(str2-str1));
  printf("malloc(4) size = %d\n", (int)(str4-str3));
  return 0;
}
```output:

```
str1 = 165199880
str2 = 165199896
str3 = 165199912
str4 = 165199928
malloc(1) size = 16
malloc(4) size = 16

```WHY? *malloc(4)* should be a block with 4 time size as* malloc(1)* block. isn't?

thanks.

---

### Post by Arndt on 2011-03-11
> **ubu@ said:**
> Hi,

*malloc(1) *and *malloc(4) *returns the same size of block, I checked it by decreasing pointers. for example:


```
int main(){
  char *str1 , *str2 , *str3, *str4;
  str1 = (char*) malloc(1);
  str2 = (char*) malloc(2);
  str3 = (char*) malloc(4);
  str4 = (char*) malloc(3);
  printf("str1 = %d\n", (int)str1); 
  printf("str2 = %d\n", (int)str2);
  printf("str3 = %d\n", (int)str3);
  printf("str4 = %d\n", (int)str4);
  printf("malloc(1) size = %d\n", (int)(str2-str1));
  printf("malloc(4) size = %d\n", (int)(str4-str3));
  return 0;
}
```output:

```
str1 = 165199880
str2 = 165199896
str3 = 165199912
str4 = 165199928
malloc(1) size = 16
malloc(4) size = 16

```WHY? *malloc(4)* should be a block with 4 time size as* malloc(1)* block. isn't?

thanks.

What would you have wanted str2 to be?

---

### Post by ubu@ on 2011-03-11
> **Arndt said:**
> What would you have wanted str2 to be?

a block in memory in size two, where I can put a only small number.
(using it only for learning. not implementation of something)

---

### Post by Npl on 2011-03-11
malloc(n) only guarantees you that it allocates **atleast** n bytes.
for a couple reasons this usually will be bigger:
[LIST]
[*]allocated blocks need to be suitably aligned, not sure about the exact requirements but at the very least it should be aligned to sizeof(int) boundarys.
[*]the c runtime needs to keep track of all allocated blocks - the smaller the blocks the bigger the overhead (relatively). Just look at filesystems where the blocksize is a few kilobytes.
[/LIST]

---

### Post by ubu@ on 2011-03-11
> **Npl said:**
> 
[LIST]
[*]allocated blocks need to be suitably aligned, not sure about the exact requirements but at the very least it should be aligned to sizeof(int) boundarys.
[/LIST]

thanks, make sense. but I don't understand the second reason. what do you mean by "overhead"?

> **Npl said:**
> 
the c runtime needs to keep track of all allocated blocks - the smaller  the blocks the bigger the overhead (relatively). Just look at  filesystems where the blocksize is a few kilobytes.


---

### Post by Npl on 2011-03-11
you have 2^32 bytes that you need to need to mark either as free or as allocated, how would you implement malloc which has to find a block of atleast n free bytes?
you`d need some kind of tables or lists to manage that, and you will have atleast 1 entry per malloced block (1 entry if you use a list, multiple depending on the allocated size if you use a table). this entries take memory aswell - the overhead of managing the available memory.

The exact amount of overhead is specific to the implementation of malloc, but I can assure you that its way more than 1 byte :D

allocate a block of couple MB of memory and try implementing own mymalloc/myfree functions that manage this block. you will see the problems involved.

---

### Post by ubu@ on 2011-03-11
got it. thanks1!

---

