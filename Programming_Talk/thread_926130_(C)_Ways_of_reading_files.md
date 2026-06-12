---
title: "(C) Ways of reading files"
date: 2008-09-21
forum: Programming Talk
---

### Post by Sockerdrickan on 2008-09-21
Would there be a better way of writing the contents of the while(1) loop?
[php]#include <stdio.h>
#include <stdlib.h>
#include <malloc.h>

typedef struct {
    int id;
    float price;
    char name[40];
} item;

item *items;

void error(const char* msg) {
    puts(msg);
    exit(1);
}

int cmp_ints(const void *foo, const void *bar) {
    int *a=(int*)foo;
    int *b=(int*)bar;

    if(*a<*b) return -1;
    else if(*a==*b) return 0;

    return 1;
}

int main() {
    FILE *f=fopen("list.db","r");
    if(!f) error("list not found");

    unsigned int last_item=0;
    while(1) {
        item tmp;
        if(fscanf(f,"%i%*c%f%*c%40[^\n]",&tmp.id,&tmp.price,tmp.name)!=3) {
            break;
        }

        items=realloc(items,sizeof(item)*++last_item);
        items[last_item-1]=tmp;
    }
    fclose(f);

    qsort(items,last_item,sizeof(item),cmp_ints);

    for(unsigned int i=0; i<last_item; ++i)
        printf("%i\t%.2f\t%s\n",items[i].id,items[i].price,items[i].name);

    free(items);

    return 0;
}
[/php]sample list.db:
[php]635890 2.50 Bread
401282 9.45 foo
531203 20.00 DOOM 3[/php]

---

### Post by doorman on 2008-09-21
You could write the part
[php]if(fscanf(f,"%i %f ",&current.id,&current.price)!=2) break;
if(!fgets(current.name,40,f)) break;[/php]as
[php]if( fscanf( f, "%i%*c%f%*c%40[^\n]%*c", &current.id, &current.price, current.name ) <= 0 )
    break;[/php]the "%*c" means "read a character from the input and ignore it"
the "%40[^\n]" means "read at most 40 characters or read until \n is reached"

hope this helps.

P.S. It's been a while since i coded stuff like this so it's possible that you may need to swap "40" and "[^\n]". I.e., if you get an error or not the input you wanted, write "%[^\n]40" instead of "%40[^\n]"

---

### Post by Sockerdrickan on 2008-09-22
Thanks!! Any other thoughts and improvements on the code?

---

### Post by mike_g on 2008-09-22
If you dont want to use a while 1 loop you could use the fscanf return value to keep it going. IE:
```

item tmp;
while(fscanf( f, "%i%*c%f%*c%40[^\n]%*c", &current.id, &current.price, current.name ) > 0)
{
   ...
}
```  

I'm also not sure if I would use realloc here as its going to cause quite and overhead if you are dealing with a lot of items plus its also difficult to insert/remove items. Personally I'd use a very simple linked list instead.

---

### Post by doorman on 2008-09-22
> **mike_g said:**
> If you dont want to use a while 1 loop you could use the fscanf return value to keep it going. IE:
```

item tmp;
while(fscanf( f, "%i%*c%f%*c%40[^\n]%*c", &current.id, &current.price, current.name ) > 0)
{
   ...
}
```I'm also not sure if I would use realloc here as its going to cause quite and overhead if you are dealing with a lot of items plus its also difficult to insert/remove items. Personally I'd use a very simple linked list instead.

Same thoughts here.

If you don't want to use linked lists (yet), you should at least check whether the realloc function succeeded. It is possible for it to fail when the system runs out of memory (which is not likely to happen but represents a potential bug).

Also, instead of writing your own error function, you could use perror - it prints out a message based on the last error occured (the variable errno). For example, when opening the file, if the FILE *f is NULL, you print out "db not found" which might not be true. Maybe the user running the app has not got the permission to read the file, or the file is locked by another process (which in your case is not going to happen as you're only reading it, but...), etc., so if the user makes a "ls" and sees the file, but you say "db not found", I'm pretty sure (s)he'll get confused.

EDIT: ops, I forgot to make an example of perror:
[php]if( ( f = fopen( "list.db", "r" ) ) == NULL ) {
  perror( "your_app_name" );
  return 1;
}[/php]
The output would look something like this:
```
$ ./your_app_name
your_app_name: file not found
```

---

### Post by Sockerdrickan on 2008-09-22
I just didn't like the thought of doing the same thing all of the time but OK, that would work pretty well if all standard library functions makes use of errno (they do right?). [COLOR=#000000][COLOR=#0000bb]perror[/COLOR][COLOR=#007700](argv[0][/COLOR][COLOR=#007700]);[/COLOR][/COLOR]

---

### Post by dwhitney67 on 2008-09-22
> **doorman said:**
> ...

If you don't want to use linked lists (yet), you should at least check whether the realloc function succeeded. It is possible for it to fail when the system runs out of memory (which is not likely to happen but represents a potential bug).
...
If a system has no more memory available on the heap, then there are bigger problems on hand compared to worrying about whether realloc() fails.

---

### Post by doorman on 2008-09-22
> **Tux0r said:**
> I just didn't like the thought of doing the same thing all of the time but OK, that would work pretty well if all standard library functions makes use of errno (they do right?). [COLOR=#000000][COLOR=#0000bb]perror[/COLOR][COLOR=#007700](argv[0][/COLOR][COLOR=#007700]);[/COLOR][/COLOR]

Yeah, they do. Well, as far as I know, most of them do :)

perror( argv[0] ) - that's it. I wanted to write that but didn't want to confuse you further :P

Also, in order to use argv[0], you need to change your main signature to:
[php]int main( int argc, char **argv )[/php]
argc - the arguments count (including the app name)
argv - the arguments vector - each argument in its own field starting from 0 (the app name) to argc - 1 (the last arg)

As far as improvements go, you could enable users to give the db filename as an argument - that way you won't have permission issues

---

### Post by Sockerdrickan on 2008-09-22
Yeah I know how main() works, I'm just trying basic things to do with C, that I can with C++ :)

---

### Post by cmay on 2008-09-22
[PHP] for(unsigned int i=0; i<last_item; ++i)
        printf("%i\t%.2f\t%s\n",items[i].id,items[i].price,items[i].name);[/PHP]
actually more a of a question but when i compile this using gcc -Wall -std=c99 i get an error about  initial loop declared outside 99mode. as far as i know then if it is java the loop will be alright i seem to remember its ok for c++ but i did not think it is okay to use a for loop this way in c.
you would according to my believe based on my sligthly outdated books and tutorials be it wrong or right have to use for loops like 
[PHP]unsigned int i;
for (i =0; i < lat_item; ++i)[/PHP]
hope you dont mind me asking.
i was just wondering as i read this tread.

---

### Post by Sockerdrickan on 2008-09-22
C99 allows you to use C++ like for loops

---

### Post by cmay on 2008-09-22
[PHP]
    for(unsigned int i=0; i<last_item; ++i)
        printf("%i\t%.2f\t%s\n",items[i].id,items[i].price,items[i].name);

this part gcc complaints about .
    
compiled with using geany as ide however.
gcc -Wall -std=c99 
compiler log:

test.c: In function ‘main’:
Compilation failed.
test.c:46: error: ‘for’ loop initial declaration used outside C99 mode[/PHP]
i compiled the code exactly as it is in copy paste style and this error shows up. i had read something about it was possible to compile c code with this way but i was not sure if it was in the defined standards or not. so when i first got these errors i figured it must be gcc that was right and tutorial that was wrong. how do you you compile it so there is no errors then. if i may ask. i learn c myself over the past month  so i read all the c post in the forums and try to learn from them. i do not hijack treads that often but i figured i could ask if someone fresh and new  to c like me try to learn file handling from the reading this post and get stuck in the same error.
or maybe i am doing something wrong when compiling.

---

### Post by Sockerdrickan on 2008-09-22
-std=c99 should make it work, perhaps that flag is not being passed on to gcc the right way, try to compile from a terminal and not with geany.

---

### Post by cmay on 2008-09-22
actually your right. it did not complaint when compiling from the terminal.
no errors and it display the output file list.db to read in the terminal fine as well. thanks for the reply.

---

