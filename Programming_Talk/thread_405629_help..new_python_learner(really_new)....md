---
title: "help..new python learner(really new)..."
date: 2007-04-10
forum: Programming Talk
---

### Post by AlexenderReez on 2007-04-10
hello all gurus and language master over there.....


i use to learn c for a while...so i decide to learn python as my second language...

in C i never use specific program as i just use gedit editor to do all compile thing...
which i save file in name end with '.c'....let say i choose file name is sad..so sad.c

then compile with 

cc -o sad2 sad.c
 
when i want to run it...i just paste sad2 to terminal...then enter....

how to make python like this??

let say i make simple python like

#!/bin/python
print "Hello, world!"


then save as [www.sh..execute](www.sh..execute)..

chmod +x [www.sh](www.sh)

how to run it?

---

### Post by chakkaradeep on 2007-04-10
> **reez0105 said:**
> 
#!/bin/python
print "Hello, world!"


save the file as **example.py** and execute in terminal as **python example.py** or you can also do this, save the file as **example**, do **chmod +x example** and from the terminal in the directory where *example* file is, execute as **./example**

---

### Post by cisforcojo on 2007-04-10
I recommend you mess around with running:

python at a terminal and do your learning there to get a handle of lists and def variables, loops, etc

After that, I recommend using SPI. It's a Python IDE and is pretty good! Highly recommended by lots. You just type your program and hit Cntrl-R to run it. Simple.

---

### Post by chakkaradeep on 2007-04-10
> **cisforcojo said:**
> 
After that, I recommend using SPI. It's a Python IDE and is pretty good! Highly recommended by lots. You just type your program and hit Cntrl-R to run it. Simple.

Is it available in ubuntu repos ? (errr...in fiesty :) )

---

### Post by AlexenderReez on 2007-04-10
thanks.....:)

---

### Post by pmasiar on 2007-04-10
SPI has a typo - it is SPE :-) Or use IDLE - even simpler IDE.

I maintain wiki with links for Python learners: [http://learnPython.pbwiki.com/](http://learnPython.pbwiki.com/) HTH

---

### Post by chakkaradeep on 2007-04-10
> **pmasiar said:**
> SPI has a typo - it is SPE :-) Or use IDLE - even simpler IDE.

I maintain wiki with links for Python learners: [http://learnPython.pbwiki.com/](http://learnPython.pbwiki.com/) HTH

Thanks :) , You link is very useful. Bookmarked it already :)

---

### Post by cisforcojo on 2007-04-10
Ooh.... thanks for the correction. SPE it is. I'll check out IDLE as well!
Not sure about the Feisty repos but it's definitely in the Edgy repos.

sudo apt-get install spe

EDIT:  Your wiki is FANTASTIC. Also bookmarked it.

---

### Post by AlexenderReez on 2007-04-12
```
SPI has a typo - it is SPE  Or use IDLE - even simpler IDE.

I maintain wiki with links for Python learners: http://learnPython.pbwiki.com/ HTH
Reply With Quote 
```



i also bookmark it.....

and maybe this is stupid question from newbie.....i see the difference in python and c language....as i'm using beryl....i checked its structure and realize that contain python and c...so i guess it is combination of 2 language....is it mean we can combine any programming language to create software.....??

---

### Post by bashologist on 2007-04-12
> **reez0105 said:**
> #!/bin/python
print "Hello, world!"

I'm not sure about this but I think a more portable way of doing this hash line would be:
```
#!/usr/bin/env python
```

---

### Post by pmasiar on 2007-04-12
> **reez0105 said:**
> python and c...so i guess it is combination of 2 language....is it mean we can combine any programming language to create software.....??

Surely yes, combining languages you can get result which combines strengths of both, avoiding weakness of both: developing whole solution  in Python, and when solution is stable (API, data structures etc), time profiling it and reimplementing as C library 5% of the code which takes 80% of execution time, you have flexibility of Python with speed of C.

It depends how easy is link those languages and how complementary they are. C is very good complement to Python.

---

### Post by Wybiral on 2007-04-12
> **pmasiar said:**
> C is very good complement to Python.

Python is a very good compliment to C :)

They are REALLY easy to use together whether you're writing a module for python or embedding python IN C, really really easy.

---

### Post by AlexenderReez on 2007-04-13
dear all gurus and masters...thanks for help to this newbie...i just realized that python has many differences c...hope any gurus/master here can help me to change this c structure to python....

i don't really understand about variable in python...so i hope anybody could give example and few explanation so that i can get better understanding....can this simple program be written in python?if yes hope can teach me(change to python)..-->

enter number 1-->9 and display in multiplication table....

example of running...

Quote:

reez@AleXenDeRrEeZ:~$ /home/reez/kl
enter your genius value(1->9 only)
-->9


**MuLtipLiCaTiOn TabLe for 9**
X : 1 2 3 4 5 6 7 8 9
-------------------------------
1 : 1 2 3 4 5 6 7 8 9
2 : 2 4 6 8 10 12 14 16 18
3 : 3 6 9 12 15 18 21 24 27
4 : 4 8 12 16 20 24 28 32 36
5 : 5 10 15 20 25 30 35 40 45
6 : 6 12 18 24 30 36 42 48 54
7 : 7 14 21 28 35 42 49 56 63
8 : 8 16 24 32 40 48 56 64 72
9 : 9 18 27 36 45 54 63 72 81

written in c-->

Quote:
#include<stdio.h>

int main(void)
{
int num,
row,
col1,
col2;

printf("enter your genius value(1->9 only)\n\t-->");
scanf("%d", &num );

if (num > 0 && num < 10) {

printf("\n**MuLtipLiCaTiOn TabLe for %d**\n", num);

if (col1 < 1 ) {
printf(" X : ");

}
for (row =num;row<=num ; row++) {
for (col1=1;col1<=num;col1++) {
printf(" %d ", col1);


}
printf("\n");
for (col1=1;col1<=3*num ;col1++) {
printf("-"); }
printf("----");
col1--;

printf("\n");
}

for (row =num;row<=num ; row++) {
for (col1=1;col1<=num;col1++){
printf(" %d :", col1);
for (row =num;row<=num ; row++) {
for (row=1;row<=num;row++) {
col2 = col1 * row;
printf("%3d", col2);

}
}
printf("\n");}
col1--;

}


}

else
{

printf("\n**********************\n");
printf("\n**Invalid UsEr InPut**\n");
printf("\n**********************\n");

}

return(0);
}

---

### Post by pmasiar on 2007-04-13
> **reez0105 said:**
> i don't really understand about variable in python.......can this simple program be written in python?


Surely it *can* be written in Python (and in less lines) but how - it is exercise for you :-)

Start reading any online book from [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart) hint: loops

Another hint: when posting code, use code tags: [ code ] [ / code ]

---

### Post by AlexenderReez on 2007-04-13
i will try....:KS

---

### Post by nihilocrat on 2007-04-13
hint :
It took me awhile to figure out how to do for loops correctly, and I thought it was dumb at first. The equivalent of:
```
for(i=0; i<foobar; i++)
```
is:
```
for i in range(0, foobar):
```
But it really gets cool when you loop through lists (basically arrays), because you can do this:
```
for item in my_array:
    item = baz + 1
```
instead of the C way, which would be this:
```
for(i=0; i<foobar, i++){
    array[i] = baz + 1;
}

```

---

### Post by AlexenderReez on 2007-04-13
[SIZE="6"]thank a lot for hint[/SIZE]

this popcorn for you..:popcorn:

---

### Post by Wybiral on 2007-04-13
> **nihilocrat said:**
> hint :
It took me awhile to figure out how to do for loops correctly, and I thought it was dumb at first. The equivalent of:
```
for(i=0; i<foobar; i++)
```
is:
```
for i in range(0, foobar):
```
But it really gets cool when you loop through lists (basically arrays), because you can do this:
```
for item in my_array:
    item = baz + 1
```
instead of the C way, which would be this:
```
for(i=0; i<foobar, i++){
    array[i] = baz + 1;
}

```


You could use a pointer as an iterator in C...

```

#include <stdlib.h>
#include <stdio.h>

int main()
{
   long *i;
   long my_array[5];

   // Fill array
   for(i = &my_array[0]; i < &my_array[5]; ++i)
   {
      *i = rand() % 10;
   }

   // Print array
   for(i = &my_array[0]; i < &my_array[5]; ++i)
   {
      printf("%i\n", *i);
   }

}

```


Or, you could use a linked list...

```

#include <stdlib.h>
#include <stdio.h>

struct list_t
{
   long data;
   struct list_t *next;
};
typedef struct list_t list;

void prepend(list** link, long data)
{
   list* temp = *link;
   *link = (list*)malloc(sizeof(list));
   (*link)->next = temp;
   (*link)->data = data;
}

void cleanup(list* link)
{
   list* temp;
   while(link)
   {
      temp = link->next;
      free(link);
      link = temp;
   }
}

int main()
{
   list* i;
   list* my_list = NULL;
   prepend(&my_list, 10);
   prepend(&my_list, 20);
   prepend(&my_list, 50);
   prepend(&my_list, 30);
   prepend(&my_list, 40);

   for(i = my_list; i != NULL; i = i->next)
   {
      printf("%i\n", i->data);
   }

   cleanup(my_list);
}

```

In fact, python's list's are a lot more similar to linked list's then arrays, so the second one probably is closer to pythons. (my point was that array index isn't the only way to iterate over data in C)

---

### Post by AlexenderReez on 2007-04-14
> **Wybiral said:**
> You could use a pointer as an iterator in C...

```

#include <stdlib.h>
#include <stdio.h>

int main()
{
   long *i;
   long my_array[5];

   // Fill array
   for(i = &my_array[0]; i < &my_array[5]; ++i)
   {
      *i = rand() % 10;
   }

   // Print array
   for(i = &my_array[0]; i < &my_array[5]; ++i)
   {
      printf("%i\n", *i);
   }

}

```


Or, you could use a linked list...

```

#include <stdlib.h>
#include <stdio.h>

struct list_t
{
   long data;
   struct list_t *next;
};
typedef struct list_t list;

void prepend(list** link, long data)
{
   list* temp = *link;
   *link = (list*)malloc(sizeof(list));
   (*link)->next = temp;
   (*link)->data = data;
}

void cleanup(list* link)
{
   list* temp;
   while(link)
   {
      temp = link->next;
      free(link);
      link = temp;
   }
}

int main()
{
   list* i;
   list* my_list = NULL;
   prepend(&my_list, 10);
   prepend(&my_list, 20);
   prepend(&my_list, 50);
   prepend(&my_list, 30);
   prepend(&my_list, 40);

   for(i = my_list; i != NULL; i = i->next)
   {
      printf("%i\n", i->data);
   }

   cleanup(my_list);
}

```

In fact, python's list's are a lot more similar to linked list's then arrays, so the second one probably is closer to pythons. (my point was that array index isn't the only way to iterate over data in C)

i don't really understand...(i'm also new to c programming...)..but i will try to understand...:)

---

### Post by AlexenderReez on 2007-04-15
any gurus want  explain about above?i don't understand(in fact i don't learn yet) about linked....?

hope any gurus will explain....

---

### Post by AlexenderReez on 2007-04-16
> #include<stdio.h>


int main(void)
{
int num,
	row,
	col1,
	col2=1,
	space;
	
printf("enter your best value\n--->");
scanf("%d", &num);
if( num > 0)
{
for (row =1;row<=num ; row++){
for (space =1;space<=(num-row);space++){
printf(" ");}
for (col1=1;col1<=row;col1++){
printf("%d", col1);}
col1--;
while (col2 < row && col1 > 1){
col1--;
printf("%d", col1);

}
printf("\n");
}
for (row =1;row<=num ; row++){
for (col1=1;col1<=num;col1++){
printf("%d", col1);}
**col1--;**
**while (col2 < num && col1 > 1)**{
**col1--;**
printf("%d", col1);

}
printf("\n");
}
}
else
printf("**inValiD user InPut**");

return(0);
}




i try to change this program to python but i only cloud do till this..
i have already highlight that things that i don't sure....gurus....please help me...:( 
> 
#!usr/bin/python

print"enter your best value\n-->"


num = (" > ")
if num > 0 :

for row in range(1, num):
for space in range(1, num-row):
print" "
for col1 in range(1,row):
print col1
while col2 < num && col1 > 1 :
print col1
print"\n"
else :
print "**InvaLid UsEr InPuT**"

---

