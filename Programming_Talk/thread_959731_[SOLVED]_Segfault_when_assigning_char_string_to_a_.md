---
title: "[SOLVED] Segfault when assigning char string to a std::string"
date: 2008-10-26
forum: Programming Talk
---

### Post by tom66 on 2008-10-26
I'm getting a segmentation fault when I try to do this:

```

void new_game()
{
	char yn[1];
	char temp_name[20];
	
	_user = (user *)malloc(sizeof(user));
	
	clear_screen();
	
	while(1)
	{
		printf("\n");
		printf(" - Enter a new name for this user (20 characters max): ");
		scanf("%20s", temp_name);
		printf(" - You entered: %s\n", temp_name);
		printf(" - Is this OK? (y/n): ", yn);
		
		scanf("%1s", yn);
		
		if(strcmp(yn, "y") == 0 || strcmp(yn, "Y") == 0)
		{
			break;
		}
		else
		{
			clear_screen();
		}
	}
	
	// this line is causing the problem: 
	_user->screen_name = temp_name;
}

```

Here is the user struct:

```

typedef struct user {
	int id;
	string screen_name;
	double money;
	finances *finance_log;
	alerts *alert_log;
	building *buildings_ptr;
	land *land_ptr;
	animal *animals_ptr;
};

```

---

### Post by jimi_hendrix on 2008-10-26
isnt there a function to convert a string to a cstring (char array)

---

### Post by tom66 on 2008-10-26
I don't know. If there is one, how do I use it?

---

### Post by jimi_hendrix on 2008-10-26
there is stringname.c_str() or something like that...go to [www.cplusplus.com...they]("http://www.cplusplus.com...they") have a lot of good string documentation

also...why use a string in the struct and not a char array?

---

### Post by tom66 on 2008-10-26
I decided to use standard character arrays. Solved, thanks.

---

### Post by dwhitney67 on 2008-10-26
std::string is used in C++; it would appear from the code you posted that you are writing C code.

The giveaway hints:
[LIST]
[*]printf()
[*]malloc()
[*]scanf()
[*]char array[N]
[*]strcmp()
[/LIST]

---

### Post by WW on 2008-10-26
Your code is an unholy commingling of C and C++. :)

**user** contains a C++ object, so you can't rely on malloc to create an instance.  Use new; that is, change this
```

    _user = (user *)malloc(sizeof(user));

```
to this:
```

    _user = new user;

```
Then the string in the user struct is properly initialized, and the assignment works.

---

### Post by tom66 on 2008-10-26
I'm using 'malloc' over 'new' because apparently I can't easily realloc with C++'s allocation features while with C, I can by using 'realloc'.

---

### Post by dwhitney67 on 2008-10-26
> **tom66 said:**
> I'm using 'malloc' over 'new' because apparently I can't easily realloc with C++'s allocation features while with C, I can by using 'realloc'.

realloc() is a function that accepts two parameters:  a pointer to an existing chunk of memory and the size for the new chunk.  It then returns a new chunk of memory of the requested size, and with the contents of the previous chunk of memory copied into the new.  There is one final step wrt to the previous memory chunk; can you guess what that is?

Stop for a moment to think how realloc() is implemented, or better yet, how you could implement it in C++.  It is not rocket science.

---

### Post by tom66 on 2008-10-26
I'm not too bright when it comes to memory allocation. Does it copy old data over? Does it check to see if it has free space at the current position? If there's a C++ way, please tell me. I was confused how to do it without realloc.

---

### Post by dwhitney67 on 2008-10-26
Here's a overly simplistic was to remodel realloc() in C++.  Note that because I have no idea who to get the original size of the initial array that was allocated, I had to improvise a little.  Presumably is you were managing a C++ class object, you would have this size... and more importantly, you would not need to define realloc()... just create your own method.

[php]
#include <cstring>
#include <iostream>


template<typename T>
T* realloc(T* ptr, size_t origSize, size_t newSize)
{
  T* rtnptr = new T[newSize];

  for (register size_t i = 0; i < origSize; ++i)
  {
    *(rtnptr+i) = *(ptr+i);
  }

  delete [] ptr;

  return rtnptr;
}


int main()
{
  char* array = new char[6];

  strcpy(array, "hello");

  array = realloc(array, 6, 12);

  strcat(array, " world");

  std::cout << array << std::endl;

  delete [] array;

  return 0;
}
[/php]

P.S.  For strings, use the std::string, not char arrays[].  If you need to realloc your structure, then I would revisit your design.  It would seem something is amiss.

---

