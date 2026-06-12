---
title: "fscanf &amp; structs"
date: 2006-03-14
forum: Programming Talk
---

### Post by Das Oracle on 2006-03-14
Here is any relevant code:

typedef struct{
char* word;
int score;
}tword;

tword* dictionary=NULL;
fscanf(ifp,"%d",&size);
dictionary = malloc(size*sizeof(tword));
for(index=0;index<size;index++){
     fscanf(ifp,"%s",dictionary[index].word);
} 

the problem is that when i try to print the words out like this:

for(index=0;index<size;index++)
     printf("%s\n",dictionary[index].word);

the output is null any ideas why?

---

### Post by pharcyde on 2006-03-14
Does your stream actually have any input?  Try using sscanf with simple buffer and see if you still have a problem.

---

### Post by LordHunter317 on 2006-03-14
You never allocate any space for the string, that's why.

Your allocation for the tword structure is incorrect.  When you call:```
malloc(size * sizeof(tword))
```You allocate space for a char pointer and an integer size times.  You don't allocate space for the string, just a pointer to it.

You need to allocate space for each of the strings as well.

---

