---
title: "Getting a string from ths user in C"
date: 2009-05-10
forum: Programming Talk
---

### Post by stfu05 on 2009-05-10
Hello guys!
 
I'm writing a C program that get from the user a string and then I need to make some changes with that string.
I don't have a clue, how to get a dynamic string from the user, because it can have any length.
I had an idea - I can allocate memory for a string with length 1 and go char by char till I get to the ENTER char and in every step with realloc() increment the memory allocated by 1.
I think the idea is pretty much fine, but I can't make the code work... I don't know what to do...
 
Any ideas how the code should look like?
 
TNX !!!! :guitar:

---

### Post by jimi_hendrix on 2009-05-10
i would just use your idea

this is the beauty of C, you have to do everything the hard way

---

### Post by stfu05 on 2009-05-10
ok, tnx...
but I don't know how to transfer my idea to actual code...
can you give me a hand with that?

---

### Post by Joeb454 on 2009-05-10
I think there's a BUFSIZ in C which is defined as 1024. I would just use that. It's unlikely to have a string THAT long inputted by the user :)

Of course, you could look into malloc/realloc

---

### Post by eye208 on 2009-05-10
> **stfu05 said:**
> I had an idea - I can allocate memory for a string with length 1 and go char by char till I get to the ENTER char and in every step with realloc() increment the memory allocated by 1.
The idea is good, but doing it in steps of 1 char is slightly inefficient. Use fgets() instead. This function allows you to read characters into a char array of arbitrary length. After the call to fgets() check the string in the array for a trailing newline character ('\n'). If there is none, extend the array with realloc() and call fgets() again, this time pointing at the end of the string that was previously read. Repeat this until a trailing newline character appears in the array or either of feof() or ferror() return TRUE. The newline indicates that an entire line has been read.

---

### Post by stfu05 on 2009-05-10
> **eye208 said:**
> The idea is good, but doing it in steps of 1 char is slightly inefficient. Use fgets() instead. This function allows you to read characters into a char array of arbitrary length. After the call to fgets() check the string in the array for a trailing newline character ('\n'). If there is none, extend the array with realloc() and call fgets() again, this time pointing at the end of the string that was previously read. Repeat this until a trailing newline character appears in the array or either of feof() or ferror() return TRUE. The newline indicates that an entire line has been read.
 
tnx, but my code wouldn't work...
can you write some of it so i could get the general idea?
 
here is my code:
 
[SIZE=2][/SIZE]```
 
int size = 6;
int position = 0;
char* str = (char*)malloc(size);
// if allocation failed
if(str==NULL)
{}
printf("please enter a string\n");
while(fgets((str + position), 5, stdin) != NULL)
{
if(str[size - 1] == '\n')
{
break;
}
else
{
position = size - 1;
size += 5;
str = (char*)realloc(str, size);
}
}
printf(str);

```

---

### Post by dwhitney67 on 2009-05-10
You were close to the proper solution.  See below for the one that works:
```

  ...

  printf("please enter a string\n");
  while(fgets((str + position), size, stdin) != NULL)
  {
    if(strchr(str, '\n'))
    {
      break;
    }
    else
    {
      position += size - 1;
      str       = realloc(str, position + size);
    }
  }
  printf("%s", str);

```

---

### Post by stfu05 on 2009-05-10
> **dwhitney67 said:**
> You were close to the proper solution. See below for the one that works:
```

  ...
 
  printf("please enter a string\n");
  while(fgets((str + position), size, stdin) != NULL)
  {
    if(strchr(str, '\n'))
    {
      break;
    }
    else
    {
      position += size - 1;
      str       = realloc(str, position + size);
    }
  }
  printf("%s", str);

```
 
Tnx a lot man !!! ;)

---

### Post by asm_Coty on 2009-05-10
Yes, that looks basic but is yet very functional.

---

### Post by stfu05 on 2009-05-11
A similar question - if i have a file, and i want to read it line by line, how can i do a similar thing to a string that will hold the whole line from the file? because i don't know what length every line will be...
 
TNX again ! :guitar:

---

### Post by dwhitney67 on 2009-05-11
> **stfu05 said:**
> A similar question - if i have a file, and i want to read it line by line, how can i do a similar thing to a string that will hold the whole line from the file? because i don't know what length every line will be...
 
TNX again ! :guitar:

Use the same while-loop, with the fgets() as described (and provided to you) earlier.  The only difference is the file-descriptor; instead of stdin, use the file-descriptor returned from fopen().

---

