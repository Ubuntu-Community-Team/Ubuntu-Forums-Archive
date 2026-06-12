---
title: "help with structs and pointers in C++"
date: 2011-05-24
forum: Programming Talk
---

### Post by c@sp3r on 2011-05-24
Ok this is my situation I have this header file:
```
struct dir
{
	char name[3];
	int root_dir;
	int has_children;
	int num_children;
	int offset_to_children[2];
	int offset_to_files[16];
};
struct files
{
	char name[5];
	int size;
	int offset_to_beginning;
	int has_fragment;
	int next_fragment;
};
struct fat
{
	int files; 
	int dirs; 
	struct dir *dir_array; 
	struct files *file_array; 
};
```
In my program if I want to access the struct fat member *dir_array or *file_array, given that this member are pointers to another struct how can I access this members from my main program? This is what I'm doing and it compiles:
```
fat *pfat;
	pfat->dir_array->root_dir=0;
```
My doubt is if I'm doing it right. Can anybody clarify my doubt and point my to the right direction. Thanks!!!

---

### Post by maddog39 on 2011-05-24
If this is C++ I wouldn't be using C struct's but instead wrap all that data into a classes and use [encapsulation]("http://en.wikipedia.org/wiki/Encapsulation_%28object-oriented_programming%29") to control access to the data.

---

### Post by c@sp3r on 2011-05-24
No I can't do that, one of the conditions is that it has to be done with structs.

---

### Post by NovaAesa on 2011-05-24
Your way of accessing the struct is correct. I have to agree strongly with maddog39, while it's possible to use structs in C++, I have been taught that it's usually better to use classes with public member variables instead.

---

### Post by cgroza on 2011-05-24
> **NovaAesa said:**
> Your way of accessing the struct is correct. I have to agree strongly with maddog39, while it's possible to use structs in C++, I have been taught that it's usually better to use classes with public member variables instead.
Aren't structures in C++ classes with public access by default?

---

### Post by zippaplick on 2011-05-24
In c++ a struct is equivalent to a class, but has public members by default. (what cgroza said)

Your header file is technically correct and it may compile, but there are some issues.

First off:
```

fat *pfat;

```

Here you create a fat pointer that doesn't point to anything. You need to assign something, ie. a real fat instance, to actually use it.

I'm kind of surprised this line compiles:
```

pfat->dir_array->root_dir=0;

```

I suspect that this is simply assigning 0 to some arbitrary/uninitalized place in memory.

If you're gonna make a pointer here, use "new" to create a new fat instance:
```

fat *pfat = new fat();

```

And when you're done with it, don't forget to delete it to prevent a memory leak:

```

delete pfat;

```

Now, since the fat object itself has dir and file pointers as members, you probably want to define a constructor that actually allocates/creates the file and dir instances (or arrays) that those point to. If so, also define the destructor to clean up anything you've allocated on the heap.

Hopefully that makes some sense and is helpful. ;) 
If not, google up on pointers, memory management, and classes/structs.

---

