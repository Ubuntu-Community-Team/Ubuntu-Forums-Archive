---
title: "C address in memory"
date: 2011-01-23
forum: Programming Talk
---

### Post by L3v3L on 2011-01-23
```

int sqr() {
  int *square = NULL;

  square = malloc(sizeof(int)*4);

  printf("%d \n",&square);

}

int main() {
  int i;
  
  for (i=0;i<100;i++){
  sqr();
 }
}

```

The address that is outputed is always the same.
Can some one tell me why the address is always the same, and how i could fix this?

---

### Post by Some Penguin on 2011-01-23
You're not actually printing out the address that's been malloc'd.  You're printing out the address *where you store that address* -- which in this case is in a particular position in the stack frame.

---

### Post by L3v3L on 2011-01-23
crap!!
Im trying to create various vectors which in later code i want to compare two specific vectors. 
So I thought, ok ill create my 10 vectors, store the beginning address of each vector in another vector, then Id go like, compare vector 1 with vector 3. So any advice how I would go about this?

P.S number of vectors is variable, and their sizes too.

---

### Post by ibuclaw on 2011-01-23
> **L3v3L said:**
> crap!!
Im trying to create various vectors which in later code i want to compare two specific vectors. 
So I thought, ok ill create my 10 vectors, store the beginning address of each vector in another vector, then Id go like, compare vector 1 with vector 3. So any advice how I would go about this?

P.S number of vectors is variable, and their sizes too.

&square is the address of the pointer, not the address of the beginning of the allocated memory.

```

int *square = NULL;
square = malloc(sizeof(int)*4);
printf("%x \n", square);

```

Regards.

---

### Post by fct on 2011-01-23
> **L3v3L said:**
> crap!!
Im trying to create various vectors which in later code i want to compare two specific vectors. 
So I thought, ok ill create my 10 vectors, store the beginning address of each vector in another vector, then Id go like, compare vector 1 with vector 3. So any advice how I would go about this?

P.S number of vectors is variable, and their sizes too.

Sounds like a double array using dynamic memory:

```

int **vectorsVector = (int **) malloc(sizeof(int *) * (number of vectors));

vectorsVector[0] = (int *)malloc(sizeof (int) * (numbers per vector));
vectorsVector[1] = (int *)malloc(sizeof (int) * (numbers per vector));
...

```
vectorsVector[0][0] -> first number in first vector.
vectorsVector[0][1] -> second number in first vector.
vectorsVector[1][0] -> first number in second vector.

And so on.

To free the memory:

```

for (i = 0; i < number of vectors; i++)
   free(vectorsVector[i]);
free(vectorsVector);

```

Save for allocation and deallocation, it's the equivalent of using:

int[number of vectors][numbers per vector] vectorsVector;

---

