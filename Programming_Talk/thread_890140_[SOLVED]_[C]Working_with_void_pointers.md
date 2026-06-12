---
title: "[SOLVED] [C]Working with void pointers"
date: 2008-08-14
forum: Programming Talk
---

### Post by Can+~ on 2008-08-14
I'll admit it, this is part of a homework, but I have doubts on my own implementation of the "storing" part. The thing is, it's supposed to mimic a database which stored different kinds of data in different files and retrieves them.

So this are the two methods I thought on how to do it, either:
-Create a function per structure (example: clients, products...)
-Create a main function that can hold every data type.

Let's say that I have a structure (invented right now):

[PHP]typedef struct
{
    unsigned int id;
    char name[40];
}t_person;[/PHP]

And my implementation so far is something like:

[PHP]bool db_store(void *data, char datatype)
{
     // Do stuff here.
}[/PHP]

char datatype : So if I want to store a person, it would be a "p". Example:

[PHP]// Declaration
t_person a_person;
a_person.id = 5;
strcpy(a_person.name, "Peter");

// Function call
db_store(&a_person, 'p');[/PHP]

Now here's the thing I don't get, if I got a person type, plus the letter "p" as the char, how can I access it's "id" or "name"?

My first idea was to declare a temporary data type with a switch-case for each letter, but it didn't work out, as I can't declare variables inside a switch case.

If I use if () { }, those variables are created in the scope of the if (If I'm right).

So, I don't get how to work with this void pointer. Everyone else doing the homework are doing it the easy-but-long way of functions per data type. Should I do it too? Is there something I'm missing?

repeat: Yes, it's part of a homework, but no, it's not the whole homework, there's a lot more behind it, I'm just confused about void pointers.

---

### Post by lisati on 2008-08-14
Huh? What's a "void pointer"?

EDIT: (OK I just looked it up on Wikipedkia). I'll give the OP a hint, based on what little I understand the question (my programming experience doesn't include much C): there are two examples of accessing the individual elements in the Declaration.

---

### Post by Can+~ on 2008-08-14
> **lisati said:**
> Huh? What's a "void pointer"?

It's a pointer that just stores the address and not the type of information contained on it, so it can work as a "wildcard".

[http://www.cplusplus.com/doc/tutorial/pointers.html](http://www.cplusplus.com/doc/tutorial/pointers.html)

---

### Post by mike_g on 2008-08-14
IIRC you should be able to cast the void pointer to a pointer of your struct type. You could start your function defining a null pointer to each struct type then assign the pointer to one of them in your switch statement.

Edit:
I knocked up a simple test program to show what I mean:
```
#include <stdio.h>
#include <string.h>

typedef struct
{
	int id;
	char data[40];
}Thing;

void foo(void *vp)
{
	Thing *tp = (Thing*)vp;
	printf("%d %s", tp->id, tp->data);
}

int main()
{
	Thing t;
	t.id = 10; 
	strcpy(t.data, "blah blah blergh");
	foo(&t);
	return 0;
}
```

---

### Post by cszikszoy on 2008-08-14
Seeing as how this is homework and all, I don't want to give away the answer.

But, you might find this webpage helpful: [http://www.cplusplus.com/doc/tutorial/structures.html](http://www.cplusplus.com/doc/tutorial/structures.html)

Perhaps around the bottom  where it talks about the arrow operator? :)

---

### Post by Can+~ on 2008-08-14
> **mike_g said:**
> IIRC you should be able to cast the void pointer to a pointer of your struct type. You could start your function defining a null pointer to each struct type then assign the pointer to one of them in your switch statement.

Edit:
I knocked up a simple test program to show what I mean:


That's very close to what I need. But now, let's say I've got 10 different things:

```
#include <stdio.h>
#include <string.h>

typedef struct
{
	int id;
	char data[40];
}Thing;

typedef
....
}Thing2;
...

... ThingN

void foo(void *vp, char type)
{
	switch type
	{
		case '1' : Thing *tp = (Thing*)vp;
		case '2' : Thing2 *tp = (Thing2*)vp;
		...
	}

	// do stuff with thing
}

int main()
{
	Thing t;
	t.id = 10; 
	strcpy(t.data, "blah blah blergh");
	foo(&t);
	return 0;
}
```

The section of the switch-case won't work.

---

### Post by mike_g on 2008-08-14
Youre right it wont. You will have to handle the different data stuctures seperately within the switch statement, or in seperate functions. Theres no real way round that.

Edit: out of cuiriosity, what are you trying to do with this data?

---

### Post by lisati on 2008-08-14
> **Can+~ said:**
> It's a pointer that just stores the address and not the type of information contained on it, so it can work as a "wildcard".

[http://www.cplusplus.com/doc/tutorial/pointers.html](http://www.cplusplus.com/doc/tutorial/pointers.html)

Thanks. I found that explanation easier to understand than the one I found at Wikipedia.

---

### Post by Can+~ on 2008-08-14
> **mike_g said:**
> Youre right it wont. You will have to handle the different data stuctures seperately within the switch statement, or in seperate functions. Theres no real way round that.

Edit: out of cuiriosity, what are you trying to do with this data?

Store it on a binary file, where blocks are sorted according their respective ID. Later retrieve it. It's a full simulation of a database, this problem I have is just a tiny subset of the real deal.

Anyway, I hoped someone to come up with "oh use awesome_function(x)", but nothing. So I guess I'll have to find a workaround.

Thank you anyway.

---

### Post by mike_g on 2008-08-14
> Store it on a binary file, where blocks are sorted according their respective ID. Later retrieve it. It's a full simulation of a database, this problem I have is just a tiny subset of the real deal.
Well you could write a generic write function. Say:
```
WriteFile(tablename, datapointer, datasize)
```
Opens the relevant table file, moves to a suitable index free block and writes the data out. THat function could then be called from your switch statement, or it could even replace your existing function.

> Anyway, I hoped someone to come up with "oh use awesome_function(x)", but nothing. So I guess I'll have to find a workaround.
Well you could always use sqlite ;)

Edit: I dont know if you are already doing this but databases are usually pre written with filler (empty blocks); that way you dont have to shuffle content around when you insert items. Makes it much faster to insert items, but the filesize is larger.

---

### Post by Bachstelze on 2008-08-14
What's the "stuff" you need to do with your things? From your last example, it seems the same stuff is done regardless of the type of thing that is being handled, that would mean all the types must have the same structure, right?

---

### Post by SledgeHammer_999 on 2008-08-14
@Can+~
Well, why don't you use "if"s instead of "switch"? (and "return" instead of "break")--> this solution is very C-ish hahahahahah

---

### Post by mike_g on 2008-08-14
Personally I dont see a need for a switch/if statement at all. If you want to write to a file you can just use a generic function. Something like should append but if you want to insert you will need to do a little extra tweaking:
```

write("thing1_table.dat" &t, sizeof(Thing1));

...

int write(const char *table, void *vp, int size)
{
	FILE* out = fopen(table, "ab");
        if(! out) return -1;
	fwrite(vp, size, 1, out);
	fclose(out);
        return 0;
}
```

---

### Post by Can+~ on 2008-08-14
But still I need to access it's ID to know where it fits. And the ID is not auto-incremental, it's might be a number like 12345678-K. It's not that easy, trust me.

> @Can+~
Well, why don't you use "if"s instead of "switch"? (and "return" instead of "break")--> this solution is very C-ish hahahahahah

Scope of variables. Variables are born and killed on the {}. Try this example:

[PHP]int main(int argc, char** argv)
{
	if (1)
	{
		int x = 2;
		
		printf("x inside:%d", x);
	}
	
	printf("x outside:%d", x);
	
	return 0;
}
[/PHP]

Not very C-ish at all.

> **HymnToLife said:**
> What's the "stuff" you need to do with your things? From your last example, it seems the same stuff is done regardless of the type of thing that is being handled, that would mean all the types must have the same structure, right?

Data types on this application are not homogeneous, one could be 200 bytes, another 20 bytes. Some pseudo-tables are sorted on ID, other on other fields (corrected).

---

### Post by mike_g on 2008-08-14
> But still I need to access it's ID to know where it fits. And the ID is not auto-incremental, it's might be a number like 12345678-K. It's not that easy, trust me.
But I would assume that the ID is always going to be the first four bytes of data?

As for finding where in the table to insert the data thats a different matter; I'll leave that to you to figure out. I'm confident that it could all be done with a generic function tho ;)

edit:
> Some pseudo-tables are sorted on ID, other on other fields (corrected).
 
Oh; if thats the case then you might want to go back to using a switch. Or, you could pass in the id size and the id offset from the start of the data, and possibly the id type (string or int). But that would be complicating things.

---

### Post by SledgeHammer_999 on 2008-08-14
Ok. Looking again back at your first post I assume that you request this as well--> You don't know how to access the struct's members(when using a pointer), right? If that's the case then the answer is simple.(I use your example struct)
[php]t_person * person;
int a;
char b[40];
a = person->id;
b = person->name;
[/php]

read here about dynamic memory and pointer(I know its C++)-->[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by cszikszoy on 2008-08-14
> **SledgeHammer_999 said:**
> Ok. Looking again back at your first post I assume that you request this as well--> You don't how to access the struct's members(when using a pointer), right? If that's the case then the answer is simple.(I use your example struct)
[php]t_person * person;
int a;
char b[40];
a = person->id;
b = person->name;
[/php]read here about dynamic memory and pointer(I know its C++)-->[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Please refer to post #5: [http://ubuntuforums.org/showpost.php?p=5590822&postcount=5](http://ubuntuforums.org/showpost.php?p=5590822&postcount=5)

:)

---

### Post by Can+~ on 2008-08-14
> **SledgeHammer_999 said:**
> Ok. Looking again back at your first post I assume that you request this as well--> You don't know how to access the struct's members(when using a pointer), right? If that's the case then the answer is simple.(I use your example struct)
[php]t_person * person;
int a;
char b[40];
a = person->id;
b = person->name;
[/php]

read here about dynamic memory and pointer(I know its C++)-->[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Are you any of you two reading? Following an element of a pointer of a struct is easy as pie. The problem appears when you have **void pointers** (read: title). Can you access elements of an struct passed as void? No, because compiler doesn't know what structure to expect. It needs to be specifically casted, which can't be done for a wide selection of types on plain C, apparently.

[PHP]typedef struct
{
	int a;
	char b;
}mystruct;

void readvoid(void *anything)
{
	printf("number: %d\nchar: %c", anything->a, anything->b);
}

int main(int argc, char** argv)
{
	mystruct sth;
	sth.z = 'x';
	sth.x = 134;
	
	readvoid(&sth);
	
	
	return 0;
}[/PHP]

```
[COLOR="Red"]warning: dereferencing &#8216;void *&#8217; pointer
error: request for member &#8216;x&#8217; in something not a structure or union
warning: dereferencing &#8216;void *&#8217; pointer
error: request for member &#8216;z&#8217; in something not a structure or union[/COLOR]
```

---

### Post by Can+~ on 2008-08-14
> **mike_g said:**
> But I would assume that the ID is always going to be the first four bytes of data?

As for finding where in the table to insert the data thats a different matter; I'll leave that to you to figure out. I'm confident that it could all be done with a generic function tho ;)

edit:
 
Oh; if thats the case then you might want to go back to using a switch. Or, you could pass in the id size and the id offset from the start of the data, and possibly the id type (string or int). But that would be complicating things.

I finally decided to do multiple functions but with mixed use of the void pointer. So know, you can call just 1 function, that will delegate for each type. This has the added benefit that I can work different files in different formats, e.g a Hash.

I appreciate your help. You gave me more ideas :)

---

### Post by SledgeHammer_999 on 2008-08-14
> **Can+~ said:**
> Are you any of you two reading? Following an element of a pointer of a struct is easy as pie. The problem appears when you have **void pointers** (read: title). Can you access elements of an struct passed as void? No, because compiler doesn't know what structure to expect.

[PHP]typedef struct
{
	int a;
	char b;
}mystruct;

void readvoid(void *anything)
{
	printf("number: %d\nchar: %c", anything->a, anything->b);
}

int main(int argc, char** argv)
{
	mystruct sth;
	sth.z = 'x';
	sth.x = 134;
	
	readvoid(&sth);
	
	
	return 0;
}[/PHP]

```
[COLOR="Red"]warning: dereferencing ‘void *’ pointer
error: request for member ‘x’ in something not a structure or union
warning: dereferencing ‘void *’ pointer
error: request for member ‘z’ in something not a structure or union[/COLOR]
```

hahahaahah that's why you need to cast your void pointer first into the correct type. I corrected your code and it builds:
[php]typedef struct
{
	int a;
	char b;
}mystruct;

void readvoid(void *anything)
{
        mystruct * cast_into_me;
        cast_into_me = (mystruct*) anything;
	printf("number: %d\nchar: %c", cast_into_me->a, cast_into_me->b);
}

int main(int argc, char** argv)
{
	mystruct sth;
	sth.a = 134;
	sth.b = 'x';

	readvoid(&sth);


	return 0;
}[/php]

---

### Post by Can+~ on 2008-08-14
> **SledgeHammer_999 said:**
> hahahaahah that's why you need to cast your void pointer first into the correct type. I corrected your code and it builds:

Stop answering the first thing you see. You're not reading:
"It needs to be specifically casted, which can't be done for a wide selection of types on plain C, apparently."

The thing is that there are multiple structures, a letter identifies the type of structure, can you cast having a single character?

Example:
[PHP]f(void * ptr, char type)
{
    if (type == 'i') // 'i' for int.
    {
         int *aux = (int*)ptr
    }else if (type == 'f')
    {
         float *aux = (float*)ptr;
    }
    
    // use aux
}[/PHP]

That won't work, aux will become local to the scope of the if.
Switch/case neither (unless it has a case 'i' {} which makes the, again, local).

Don't bother on replying anyway, I'm opting for other solution (marked as solved).
[SIZE=1](and why he laughs?)[/SIZE]

---

### Post by DavidBell on 2008-08-15
You're not getting it, you need to redo your general function along the lines

[PHP]f(void * ptr, char type)
{
    if (type == 'i') // 'i' for int.
    {
         int *aux = (int*)ptr
         // use aux
    }else if (type == 'f')
    {
         float *aux = (float*)ptr;
         // use aux
    }
    
}[/PHP]

or

[PHP]f(void * ptr, char type)
{
    switch (type)
        {case 'i':
             {// 'i' for int.
                 int *aux = (int*)ptr;
                 // use aux
             }
             break;
         case 'f':
             {// 'f' for float.
                 float *aux = (float*)ptr;
                 // use aux
             }
             break;
         };
}[/PHP]

If you have common data in the same order at the start of each struct definition /I think/ you can cast to a simple struct with only the common data ( a bit like a base class) for common functions. But I'm not sure if this will always work with optimisations these days, it would be safer to include common data in a contained sub-struct.

DB

---

