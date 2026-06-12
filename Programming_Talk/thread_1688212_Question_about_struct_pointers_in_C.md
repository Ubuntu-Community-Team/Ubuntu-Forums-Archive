---
title: "Question about struct pointers in C"
date: 2011-02-15
forum: Programming Talk
---

### Post by Peter76 on 2011-02-15
Hello, still studying my C book:p,

I have the following function:
```

void InitPerson( Person *person, char *name, char *address ) {
	int nameLength = strlen(name) + 1;
	person->name = malloc( sizeof( char ) * nameLength );
	strcpy( person->name, name ); }
```

What I understand from it is that person->name is the same as (*person).name, ie the pointer to the struct is dereferenced so you can access its value.
But why is this same construction used for allocating the memory?
I would use person.name =malloc(blabla) there, like in:
```

main() {

int* p;

p = malloc(sizeof(int));
*p = 10;
free(p);
}
```

It looks to me like the memory address is now given to the value of the pointer instead of the pointer itself.

Thanks in advance

---

### Post by Arndt on 2011-02-15
> **Peter76 said:**
> Hello, still studying my C book:p,

I have the following function:
```

void InitPerson( Person *person, char *name, char *address ) {
	int nameLength = strlen(name) + 1;
	person->name = malloc( sizeof( char ) * nameLength );
	strcpy( person->name, name ); }
```

What I understand from it is that person->name is the same as (*person).name, ie the pointer to the struct is dereferenced so you can access its value.
But why is this same construction used for allocating the memory?
I would use person.name =malloc(blabla) there, like in:
```

main() {

int* p;

p = malloc(sizeof(int));
*p = 10;
free(p);
}
```

It looks to me like the memory address is now given to the value of the pointer instead of the pointer itself.

Thanks in advance

Why should you use "person.name" for accessing the name field, when you just established that person->name or (*person).name is the way to do it? person.name implies that person is a struct, not a pointer to one.

I'm not sure what you mean when you write "like in". In the code, a pointer variable is assigned a pointer to memory, quite proper.

---

### Post by Peter76 on 2011-02-15
Ok, think I found the answer myself; "name" is actually of the type char*, so is that why this construction works?
And if "name" had been of type int, would malloc have then to be called with person.name instead of person->name?

---

### Post by Arndt on 2011-02-15
> **Peter76 said:**
> Ok, think I found the answer myself; "name" is actually of the type char*, so is that why this construction works?
And if "name" had been of type int, would malloc have then to be called with person.name instead of person->name?

If name had been of type int, no malloc would have been necessary. Then you just assign to it like this: person->name = 10.

---

### Post by nvteighen on 2011-02-15
> **Peter76 said:**
> Ok, think I found the answer myself; "name" is actually of the type char*, so is that why this construction works?
And if "name" had been of type int, would malloc have then to be called with person.name instead of person->name?

When in doubt, look for the type.

person's type is (Person *), so you access the name field by using person->name, no matter what you plan to do with it. It has nothing to do with the fact that you're using malloc.

---

### Post by slavik on 2011-02-15
no, it would not, because name would have to be int*

---

### Post by forrestcupp on 2011-02-15
> **Peter76 said:**
> 
What I understand from it is that person->name is the same as (*person).name, ie the pointer to the struct is dereferenced so you can access its value.
But why is this same construction used for allocating the memory?
I would use person.name =malloc(blabla) there, like in:


It looks to me like the memory address is now given to the value of the pointer instead of the pointer itself.

Thanks in advance

That's a good question, but you're misunderstanding something. The pointer is to the instance of the struct you named **person**. The **name** member is not a pointer. So you use the '->' because **person** is a pointer, not because **name** is a pointer.

If you want to confuse yourself, start making pointers to pointers. :)

---

### Post by cgroza on 2011-02-15
Well, malloc returns a pointer, so the left value needs to be a pointer too.
I am thinking C++ here and talking C. I say this because I believe that "malloc" is some sort of equivalent to the C++ "new"...

---

### Post by nvteighen on 2011-02-16
> **cgroza said:**
> Well, malloc returns a pointer, so the left value needs to be a pointer too.
I am thinking C++ here and talking C. I say this because I believe that "malloc" is some sort of equivalent to the C++ "new"...

Yes, name also has to be a pointer, but here it's irrelevant because he's not dereferencing it. If he wanted to dereference it, it would have been: *(person->name)

---

