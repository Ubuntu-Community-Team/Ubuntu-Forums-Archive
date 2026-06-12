---
title: "Static array issue ."
date: 2012-07-06
forum: Programming Talk
---

### Post by spanlength1 on 2012-07-06
HI , 

I am implementing a function for my assignment based on the following information. As you see the main.c file has a function 
printWithoutDuplicates which prints the strings that are not printed previously. I can use static arrays for this.(Dont confuse with
arrays on stack.) 

```

#ifndef TKK_AS_C_PRINTERS_H
#define TKK_AS_C_PRINTERS_H
/* Prints strings without duplicates
 * This implies that the function must store all previously printed strings
 *  and not print a string it has already printed.
 * In case of duplicate, nothing is printed.
 * A NULL parameter resets the storage and should
 *  free any memory allocated for the storage. */
void printWithoutDuplicates(const char*);

#endif

```

```

#include "printers.h"
#include <stdio.h>

int main(void)
{
const char* strings[] = {"a string", "another string", "a string", "a better string", "a string", NULL};

 printf("Printing without duplicates\n");
  for (size_t i = 0;strings[i];i++)
    printWithoutDuplicates(strings[i]);

  
  printf("Resetting the duplicate storage\n");
  printWithoutDuplicates(NULL);

}

```

Can some one sujjest how to proceed with the array to store the previously printed strings. I cannot have a dynamic arrays because i need to pass the index of the string array in the main.

---

### Post by trent.josephsen on 2012-07-06
printWithoutDuplicates should be a fairly simple function to implement and the array for duplicate strings can be local to it. I wrote one version in 11 lines. Why don't you give it your best shot and post your code when you get stuck?

---

### Post by lisati on 2012-07-06
> **trent.josephsen said:**
> Why don't you give it your best shot and post your code when you get stuck?
+1 to the suggestion. Depending on the ultimate purpose and context of the routine, it might even be possible to avoid the need for a second array to store the printed strings, but I suspect that doing so might defeat the purpose of the exrecise.

---

### Post by spanlength1 on 2012-07-06
> **lisati said:**
> +1 to the suggestion. Depending on the ultimate purpose and context of the routine, it might even be possible to avoid the need for a second array to store the printed strings, but I suspect that doing so might defeat the purpose of the exrecise.
```

#include "printers.h"
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>

static char *arraylist;
static int count = 0;
void printWithoutDuplicates(const char* stringname) {
    bool flag = true;
    if (stringname) {
        if (count > 0) {
            for (int i = 0; i < count; i++) {
                char *compare = arraylist[i];
                if (!strcmp(stringname, compare)) {
                    flag = false;
                }
            }
        } else {
            arraylist = malloc(sizeof (char));
            count = 1;
            arraylist[0] = stringname;
            flag = true;
        }
        
        
        if (flag){
            printf("%s\n", stringname);
            arraylist = realloc(arraylist, (sizeof (char) *(count + 1)));
            arraylist[count] = stringname;
            count = count + 1;
        }
    } else
        free(arraylist);
}


```

Well i had done something like this , but i am getting seg error.

---

### Post by snip3r8 on 2012-07-06
I have little knowledge of c , heres the best i could come up with

[PHP]static const char* printed[] = {"","",""};
static int flag = 0;

void printWithoutDuplicates(const char* param){
    if (param == NULL){
        remove(*printed);
        flag = 0;
        return;
    }
    //printf("\n passed in ; %s\n",param);
if (flag == 0) {
        printf("%s\n",param);
      printed[flag] = param;
       ++flag;
       return;
    }
        
    for (int i = 0;i < flag;i++) {
        if (printed[i] == param) {
            return;
        }
        else {
            printf("%s\n",param);
            printed[flag] = param;
            ++flag;
            break;
        }
    }
    
}
[/PHP]

---

### Post by spanlength1 on 2012-07-06
> **snip3r8 said:**
> I have little knowledge of c , heres the best i could come up with

[PHP]static const char* printed[] = {"","",""};
static int flag = 0;

void printWithoutDuplicates(const char* param){
    if (param == NULL){
        remove(*printed);
        flag = 0;
        return;
    }
    //printf("\n passed in ; %s\n",param);
if (flag == 0) {
        printf("%s\n",param);
      printed[flag] = param;
       ++flag;
       return;
    }
        
    for (int i = 0;i < flag;i++) {
        if (printed[i] == param) {
            return;
        }
        else {
            printf("%s\n",param);
            printed[flag] = param;
            ++flag;
            break;
        }
    }
    
}
[/PHP]

It works fine with the current string input but if i change that then it crashes .

const char* strings[] = {"a string", "another string", "my string","a string", "a better string", "a string","a better string","my string","a better string", "no string", NULL};

---

### Post by snip3r8 on 2012-07-06
I looked at some of your logic and added it to mine , here is the result:


[PHP]

#include <stdio.h>
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>

static const char** printed;
static int flag = 0;

void printWithoutDuplicates(const char* param){
    if (param == NULL){
        free(printed);
        flag = 0;
        return;
    }
    //printf("\n passed in ; %s\n",param);
    if (flag == 0) {
        printf("%s\n",param);
        printed = malloc(sizeof (char));
        printed[flag] = param;
        ++flag;
        return;
    }
    
    for (int i = 0;i < flag;i++) {
        if (printed[i] == param) {
            return;
        }
        else {
            printf("%s\n",param);
            printed = realloc(printed, (sizeof (char) *(flag + 1)));
            printed[flag] = param;
            ++flag;
            break;
        }
    }
    
}  


[/PHP]

---

### Post by Barrucadu on 2012-07-06
> **snip3r8 said:**
> I looked at some of your logic and added it to mine , here is the result:

That will still print duplicates at it checks the pointer values rather than the string contents.

---

### Post by spanlength1 on 2012-07-06
> **snip3r8 said:**
> I looked at some of your logic and added it to mine , here is the result:


[PHP]

#include <stdio.h>
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>

static const char** printed;
static int flag = 0;

void printWithoutDuplicates(const char* param){
    if (param == NULL){
        free(printed);
        flag = 0;
        return;
    }
    //printf("\n passed in ; %s\n",param);
    if (flag == 0) {
        printf("%s\n",param);
        printed = malloc(sizeof (char));
        printed[flag] = param;
        ++flag;
        return;
    }
    
    for (int i = 0;i < flag;i++) {
        if (printed[i] == param) {
            return;
        }
        else {
            printf("%s\n",param);
            printed = realloc(printed, (sizeof (char) *(flag + 1)));
            printed[flag] = param;
            ++flag;
            break;
        }
    }
    
}  


[/PHP]
Well , you code seems to work , but i did some changes. 
Also **char is pointing to an array of *chars not chars .
I need to do a valgrind and see if there is still any error.

```

void printWithoutDuplicates(const char* param) {
    if (param == NULL) {
        free(printed);
        flag = 0;
        return;
    }
    //printf("\n passed in ; %s\n",param); 
    if (flag == 0) {
        printf("%s\n", param);
        printed = malloc(sizeof (char*));
        printed[flag] = param;
        ++flag;
        return;
    }

    for (int i = 0; i < flag; i++) {
        if (printed[i] == param) {
            return;
        }
    }
    printf("%s\n", param);
    printed = realloc(printed, sizeof (char*) *(flag + 1));
    printed[flag] = param;
    ++flag;
}
```

---

### Post by trent.josephsen on 2012-07-06
Okay, for starters, you're declaring arraylist as a simple pointer to char -- it needs to hold as many (unique) strings as you give it, so let's declare it as an array of pointer-to-const-char. Also, arraylist and count don't have meaning outside of printWithoutDuplicates(), so let's declare them inside the function (with "static" so they're persistent from one call to the next).

```
#define NUM_STRINGS 1000
void printWithoutDuplicates(char const *stringname)
{
	static char const *arraylist[NUM_STRINGS];
	static int count = 0;
```
(I'm going to suppose that 1000 is "big enough" to simplify writing this routine; leaving making it more robust as an exercise.)

My version didn't check stringname for being non-NULL; if you want to, the easy way is
```
if (!stringname) {
        return;
}
```

As for the rest, I'll give pseudocode so I don't just give the whole thing away, but it's really just one **for** loop and one **if** statement:

```
for each string in **arraylist**:
    if the string is the same as **stringname**:
        return immediately
(now we know **stringname** isn't in **arraylist**)
add **stringname** to **arraylist**
increment **count**
print **stringname**

```

Also, no offense snip3r8, but your code is needlessly complicated and incorrect in various ways. Your use of malloc() in particular is confusing to say the least (to say nothing of the fact that it's not even necessary, and you were correct to avoid it in your original version).

---

### Post by snip3r8 on 2012-07-06
> **trent.josephsen said:**
> Okay, for starters, you're declaring arraylist as a simple pointer to char -- it needs to hold as many (unique) strings as you give it, so let's declare it as an array of pointer-to-const-char. Also, arraylist and count don't have meaning outside of printWithoutDuplicates(), so let's declare them inside the function (with "static" so they're persistent from one call to the next).

```
#define NUM_STRINGS 1000
void printWithoutDuplicates(char const *stringname)
{
	static char const *arraylist[NUM_STRINGS];
	static int count = 0;
```
(I'm going to suppose that 1000 is "big enough" to simplify writing this routine; leaving making it more robust as an exercise.)

My version didn't check stringname for being non-NULL; if you want to, the easy way is
```
if (!stringname) {
        return;
}
```

As for the rest, I'll give pseudocode so I don't just give the whole thing away, but it's really just one **for** loop and one **if** statement:

```
for each string in **arraylist**:
    if the string is the same as **stringname**:
        return immediately
(now we know **stringname** isn't in **arraylist**)
add **stringname** to **arraylist**
increment **count**
print **stringname**

```

Also, no offense snip3r8, but your code is needlessly complicated and incorrect in various ways. Your use of malloc() in particular is confusing to say the least (to say nothing of the fact that it's not even necessary, and you were correct to avoid it in your original version).

Lol , i knew the code would be horrible , saying i had limited experience in c is an understatement , only time i ever used malloc was to purposefully cause a memory leak for giggles. I was just trying to solve the problem out of interest and expanding my knowledge.

That said here is another attempt by me using your pseudocode logic .

[PHP]void printWithoutDuplicates(const char* param){
  
    static const char  *arrayList[NUM_STRINGS];
    static int count = 0;
    
    for (size_t i=0; arrayList[i]; i++) 
        if (param == arrayList[i]) return;
    
    arrayList[count] = param;
    count++;
    printf("%s \n",param);
    
}


int main(int argc, const char * argv[])
{
    const char* strings[] = {"badger", "badger", "badger", "mushroom", "mushroom", NULL};
    
    printf("Printing without duplicates\n");
    for (size_t i = 0;strings[i];i++)
        printWithoutDuplicates(strings[i]);
    
    
    printf("Resetting the duplicate storage\n");
    printWithoutDuplicates(NULL);
   
    
    return 0;
}
[/PHP]

as a matter of interest , how would we delete the arraylist if a null is passed to printWithoutDuplicates ? im guessing its something simple that i just dont know about.

It would be a breeze in C++ , but i think thats just because its a language i am familiar with :

[PHP]void printWithoutDuplicates(const char* param){
  
    static vector<const char*>printed;
    
    if (!param){
        printed.clear();//clear the vector
    }
    
    for (vector<const char*>::const_iterator iter=printed.begin();iter != printed.end();++iter) 
        if (param == *iter) return;//dont print
    
    printed.push_back(param);//print the result
    printf("%s \n",param);
    
}
[/PHP]

---

### Post by Barrucadu on 2012-07-06
> **snip3r8 said:**
> as a matter of interest , how would we delete the arraylist if a null is passed to printWithoutDuplicates ? im guessing its something simple that i just dont know about.

As it's not dynamically allocated (ie: with malloc) you can't. Also, use strcmp for comparing strings, == will just check the equality of the pointers.

---

### Post by trent.josephsen on 2012-07-06
> **snip3r8 said:**
> as a matter of interest , how would we delete the arraylist if a null is passed to printWithoutDuplicates ?

Um. Why would you want to do that?

But all you have to do with my version is set `count` to 0. The array isn't "deleted", but the stuff that remains there doesn't matter because in that case I overwrite it with a new list.

Your version doesn't quite work that way because how you loop through the array depends on arrayList[count] being 0. This also means you can only tolerate (NUM_STRINGS - 1) unique strings before straying into undefined behavior -- likely to cause off-by-one errors, especially if you later insert error checking code.

Also, your if statement's condition probably doesn't do what you expect; you might want to compare your current version to spanlength1's first one.

---

### Post by snip3r8 on 2012-07-06
> **Barrucadu said:**
> As it's not dynamically allocated (ie: with malloc) you can't. Also, use strcmp for comparing strings, == will just check the equality of the pointers.
using strcmp caused me some bad access errors,thats why i didn't use it

---

### Post by snip3r8 on 2012-07-06
> **trent.josephsen said:**
> Um. Why would you want to do that?

But all you have to do with my version is set `count` to 0. The array isn't "deleted", but the stuff that remains there doesn't matter because in that case I overwrite it with a new list.

Your version doesn't quite work that way because how you loop through the array depends on arrayList[count] being 0. This also means you can only tolerate (NUM_STRINGS - 1) unique strings before straying into undefined behavior -- likely to cause off-by-one errors, especially if you later insert error checking code.

Also, your if statement's condition probably doesn't do what you expect; you might want to compare your current version to spanlength1's first one.

Ok thanks for pointing that thing out about the loop , that was what was breaking my strcmp

heres the result:

[PHP]
#include <stdio.h>
#include <string.h>

#define NUM_STRINGS 1000

void printWithoutDuplicates(const char* param){
  
    static const char  *arrayList[NUM_STRINGS]; 
    static int count = 0; 
    
    if (!param){
        count = 0;
        return;
    }
    
    for (int i = 0; i < count;i++)  
        if (!strcmp(arrayList[i], param))
            return;
               
    arrayList[count] = param; 
    count++; 
    printf("%s \n",param);     
}


int main(int argc, const char * argv[])
{
    const char* strings[] = {"badger", "badger", "badger", "mushroom", "mushroom", NULL};
    
    printf("Printing without duplicates\n");
    for (size_t i = 0;strings[i];i++)
        printWithoutDuplicates(strings[i]);
    
    
    printf("Resetting the duplicate storage\n");
    
    printWithoutDuplicates(NULL);
    
    printf("Printing without duplicates\n");
    for (size_t i = 0;strings[i];i++)
        printWithoutDuplicates(strings[i]);

    return 0;
}
[/PHP]

Output:

```

Printing without duplicates
badger 
mushroom 
Resetting the duplicate storage
Printing without duplicates
badger 
mushroom 


```

---

### Post by Barrucadu on 2012-07-06
Also, you shouldn't put strings in your array with `arrayList[count] = param;`, if the string is ever freed or otherwise goes out of scope (which admittedly doesn't happen in your simple program), that'll be a bad memory access. You should use `strcpy` or `strdup`, making sure you `free` when you're done.

---

### Post by snip3r8 on 2012-07-06
Random thought: now i see why people get so angry when people say C and C++ are the same thing ,C is way more dependent on manual memory management.

---

### Post by trent.josephsen on 2012-07-06
Hmm, I hadn't thought of that possibility... I was thinking in terms of pointers to read-only memory and it hadn't occurred to me that someone might pass it an automatic or malloc()ed string.

And there's a lot more to C vs. C++ than just memory management, but yes, that's definitely a big difference a lot of new C programmers don't seem to be prepared for.

---

### Post by trent.josephsen on 2012-07-06
FWIW, here's my 11 line version:

```
void printWithoutDuplicates(char const *s)
{
	static char const *printed[NUM_STRINGS];
	static size_t n = 0;
	for (size_t i = 0; i < n; i++) {
		if (!strcmp(printed[i], s)) {
			return;
		}
	}
	puts(printed[n++] = s);
}
```

---

### Post by Bachstelze on 2012-07-06
As an aside, this would be a good problem to start experimenting with [hash tables](http://en.wikipedia.org/wiki/Hash_table), especially if the input is very large.

---

### Post by snip3r8 on 2012-07-07
> **Bachstelze said:**
> As an aside, this would be a good problem to start experimenting with [hash tables](http://en.wikipedia.org/wiki/Hash_table), especially if the input is very large.
I think that would just be a ton of overhead for something simple.

---

### Post by Bachstelze on 2012-07-07
> **snip3r8 said:**
> I think that would just be a ton of overhead for something simple.

Yes, but writing a C program in the first place is a ton of overhead anyway. [font=monospace]sort | uniq[/font] will do the job [fast enough](http://ubuntuforums.org/showthread.php?t=2003553#6) and more easily. Remember this is an assignment, not a real program.

---

### Post by spanlength1 on 2012-07-09
Well i did implement a dynamic array . It works fine 
```

void printWithoutDuplicates(const char* param) {
    if (param == NULL) {
        for (int i = 0; i < flag; i++) {
            free(printed[i]);
        }
        free(printed);
        flag = 0;
        return;
    }
    //printf("\n passed in ; %s\n",param);
    if (flag == 0) {
        printf("%s\n", param);
        printed = malloc(sizeof (char*));
        size_t len = 1 + strlen(param);
        printed[0] = malloc(len);
        printed[0] ? memcpy(printed[0], param, len) : NULL;
        ++flag;
        return;
    }

    for (int i = 0; i < flag; i++) {
        if (!(strcmp(printed[i], param))) {
            return;
        }
    }
    printf("%s\n", param);
    printed = realloc(printed, sizeof (char*) *(flag + 1));
    size_t len = 1 + strlen(param);
    printed[flag] = malloc(len);
    printed[flag] ? memcpy(printed[flag], param, len) : NULL;
    ++flag;
}
```

---

### Post by trent.josephsen on 2012-07-09
Calling realloc() every time you add a new item to the list is unnecessary. Here's how I would do it (untested). The array starts at 50 elements and grows by a factor of 1.5 every time it gets filled up: when you put the 50th element in, it grows to size 75; when you put the 75th element in, it grows to 112; then to 168, 252, 378 and so forth. If you put a thousand strings in it, you have to call realloc() 8 times, but if you put a million strings in it you only have to call realloc() 25 times.

My version frees only the memory used for the strings, not that used for the array itself, so when you call printWithoutDuplicates(NULL) it doesn't shrink back down to 0 and it won't call realloc() again if the next set of data is around the same size as the last. This is usually what you want, but there are disadvantages both ways.

```
#define INIT_SIZE	50
#define SCALE		1.5
void printWithoutDuplicates(char const *s)
{
	static char const **printed;
	static size_t n = 0, size = 0;

	/* if the parameter is NULL, then empty the array and return */
	if (!s) {
		for (size_t i = 0; i < n; i++) {
			free(printed[i]);
		}
		n = 0;
		return;
	}
	
	/* return immediately if the string is a duplicate */
	for (size_t i = 0; i < n; i++) {
		if (!strcmp(printed[i], s)) {
			return;
		}
	}

	/* otherwise, (re)size the array if necessary, ... */
	if (size == 0) {
		size = INIT_SIZE;
		printed = malloc(size * sizeof *printed);
	} else if (n == size) {
		size *= SCALE;
		printed = realloc(printed, size * sizeof *printed);
	}

	/* ... add the new string to the end, and print it */
	puts(printed[n++] = strdup(s)); // strdup() is a POSIX extension
}
```

strdup() is a POSIX extension, not standard C, but it's basically just shorthand for strcpy(malloc(strlen(s) + 1), s). (Not sure why you used memcpy... I mean, it works just fine, but it's less clear than strcpy() and you don't have to give strcpy() a size argument that is susceptible to off-by-one errors.)

Finally, don't use the ternary operator ?: as a replacement for an if-statement unless you intend to use the value of the expression. Evaluated in a void context it probably compiles to the same machine code, but it could also plausibly be slower than just `if (expression) statement;`. It's also less readable.

---

