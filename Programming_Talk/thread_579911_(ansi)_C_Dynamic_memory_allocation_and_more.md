---
title: "(ansi) C: Dynamic memory allocation and more?"
date: 2007-10-18
forum: Programming Talk
---

### Post by happogiri on 2007-10-18
```

struct ex1 {
     char *string1;
     char *string2;
     double n;
}; 

struct ex2 {
     char *string3;
     struct ex1 *structArray; /* I don't know how many ex1's yet? */
}

```

In ex1 there's two char pointers that are supposed to be strings of unknown length. If I wanted to make ( I do want!) a function to create struct ex1, how can I do it?
```

struct ex1 *createEx1(char *, char *, double) {
     struct ex1 *tmp;
     tmp = (struct ex1 *)malloc(sizeof(struct ex1));
     ....
     return tmp;
}

```
If I've understood right I can't allocate memory like that, since string1 and string2 are pointers (4 bytes). The reason why I'd like to do it like this is because:

I want to store structs like ex1 to ex2's structArray[] but I don't know how many. Maybe 3 maybe 1000. Something like this to create ex2: 
```

loop while something
     ex2.structArray[i] = createEx1(...); 
     i++;
end loop

```

Am I totally off the tracks?

---

### Post by smartbei on 2007-10-18
Well, if you can't be sure about the number of ex1 structs that you will want you may want to use a linked list or vector.
As for the rest of it, this might work:
```

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

struct ex1 {
	char *string1;
	char *string2;
	double n;
}; 

struct ex2 {
	char *string3;
	struct ex1 *structArray; /* I don't know how many ex1's yet? */
};

struct ex1 * createEx1(char *str1, char *str2, double dbl) {
	struct ex1 *tmp;
	tmp = (struct ex1 *)malloc(sizeof(struct ex1));
	
	tmp->string1=malloc(strlen(str1)+1);
	strcpy(tmp->string1,str1);
	
	tmp->string2=malloc(strlen(str2)+1);
	strcpy(tmp->string2,str2);
	
	tmp->n=dbl;
	return tmp;
}

int main ()
{
	struct ex2 container;
	
	container.structArray = createEx1("test1","test2",1234);
	
	printf(container.structArray->string1);
	printf(container.structArray->string2);
	printf("%lf",container.structArray->n);
		
	return 0;
}

```
NOTE: Add memory deallocation!

---

### Post by hod139 on 2007-10-18
> **smartbei said:**
> 
As for the rest of it, this might work:
<snip>

There are some problems with your code.  First, never use strcpy.  It is evil.  Second (and probably a small oversight since you were writing up this example code quickly), you never check the return status of malloc.  Third, I wouldn't have createEx1 return a pointer to a ex1 struct, ownership gets a little confusing.  Instead, pass a pointer to a ex1 struct pointer.  For example:
```

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

struct ex1 {
    char *string1;
    char *string2;
    double n;
};

struct ex2 {
    char *string3;
    struct ex1 *structArray; /* I don't know how many ex1's yet? */
};

// Attempt to allocate the stuct parameter and initialize 
// If allocation fails, return 0 else return 1
int createEx1(char *str1, char *str2, double dbl, struct ex1 ** tmp) {
    
    (*tmp) = (struct ex1 *)malloc(sizeof(struct ex1));
    if ((*tmp)==NULL) return 0; // failed to allocate the struct
    
    int strSize = strlen(str1);
    (*tmp)->string1 = malloc(strSize+1);
    if ((*tmp)->string1 == NULL) return 0; // failed to allocate the string

    strncpy((*tmp)->string1,str1, strSize); // only copy n bytes
    (*tmp)->string1[strSize] = '\0';        // always null terminate
    
    strSize = strlen(str2);
    (*tmp)->string2=malloc(strSize+1);
    if ((*tmp)->string1 == NULL) return 0; // failed to allocate the string

    strncpy((*tmp)->string2, str2, strSize); // only copy n bytes
    (*tmp)->string2[strSize] = '\0';         // always null terminate
    
    (*tmp)->n=dbl;
    
    return 1;
}

int main ()
{
    struct ex2 container;
    
    if( !createEx1("test1","test2",1234, &(container.structArray)) ){
        printf("Something failed");
        exit(1);
    }
    
    printf("%s \n", container.structArray->string1);
    printf("%s \n", container.structArray->string2);
    printf("%lf \n",container.structArray->n);


   // Write destructor!!!!!!!
        
    return 0;
}

```Here I pass in a pointer to the struct pointer, so ownership is more clear.  I use strncpy and null terminate the string (never ever use strcpy).  I check that the malloc was successful.

**Edit:** I also did not write a destructor, make sure you write one!

---

### Post by Lux Perpetua on 2007-10-18
What exactly is wrong with using strcpy if it clearly doesn't overflow the destination?

---

### Post by jpkotta on 2007-10-18
What is wrong with strncpy if you know the (maximum) size of the destination?

---

### Post by Wybiral on 2007-10-18
> **Lux Perpetua said:**
> What exactly is wrong with using strcpy if it clearly doesn't overflow the destination?

Bad habit / practice.

---

### Post by hod139 on 2007-10-18
> **Lux Perpetua said:**
> What exactly is wrong with using strcpy if it clearly doesn't overflow the destination?
It's not wrong, but why not use strncpy instead of strcpy?  

Don't get me wrong, strncpy is not a perfect solution and opens a whole host of other problems (lack of null termination if source >= dest, padding the dest with zeros if src < dest), but it is the lesser of two evils.  Ideally, strlcpy would become standard, which behaves, imo, how strncpy should.

---

### Post by smartbei on 2007-10-19
Yes, the idea was to get the OP started, not to write perfect code, hence I did not add free()'ing the memory, etc. Point taken though.

---

### Post by happogiri on 2007-10-24
Thanks alot! These pointers are causing me headaches... :)

---

