---
title: "[C] passing char pointers to functions (problem)"
date: 2009-03-01
forum: Programming Talk
---

### Post by hey_ram on 2009-03-01
hi all,

i am facing a problem in passing character pointers to a function. this is a simple program from k&r, ex 3-3, where the objective is to expand a user-entered string. 

eg.) if the user enters a string say, a-z, the output must be the entire lower-case alphabet. and so on...

the basic structure of my program goes as follows:

1. function declaration: void expand(char *dest, char *src)

2. function call from main(): 
expand(dest, src)
a few words about this call: space has been allocated to string "src" dynamically.
all the space to the destination string (dest) is allocated dynamically in the function definition, and not in main().

3. in the function definition, i allocate the required space to dest (dynamically, through realloc) as many times as necessary to accommodate the expanded string. 

the trouble arises when the function returns. though i am passing pointers, it seems the string dest does not get updated. 

i tried using gdb and also printed the string dest in the function expand just before the function returns to main(). it seems to be  working just fine inside the function.

i am having trouble figuring out where i am going wrong. should the string dest not get updated in main?

any help is welcome!

---

### Post by dwhitney67 on 2009-03-01
Well, from the look of things, if your expand() function is going to allocate memory for the 'dest', and return such memory, then the declaration for expand() should be:
```

void expand(char** dest, const char* src);

```
The purpose of the "pointer to a pointer" for 'dest' is so that the address of 'dest', which is established elsewhere, can be changed to point to the allocated memory.  The 'src' pointer definition is changed to const so that the contents at that location are not modified.  K&R are smart guys, but they cut lots of corners in their examples.

Here's some code (of which I have not compiled):
```

void expand(char** dest, const char* src)
{
  ...
}

int main()
{
  char  src[20] = {0};
  char* dest = 0;

  printf("Enter some text: ");
  fgets(src, sizeof(src), stdin);

  expand(&dest, src);

  ...
}

```

---

### Post by lloyd_b on 2009-03-01
Just a comment - it would make more sense to actually have the function return the char *, rather than rely on passing via pointers in the parameters:
```
char *expand(char *src)
{
    char *dest;

    ...

    return dest;
}

int main()
{
    char src[20];
    char *dest;

    ...
    dest = expand(src);
    ...
}
```

Lloyd B.

---

### Post by dwhitney67 on 2009-03-01
Yes, that would work too and IMO be better.  But the OP's example is derived from the K&R book which defines it differently.

---

### Post by lloyd_b on 2009-03-01
> **dwhitney67 said:**
> Yes, that would work too and IMO be better.  But the OP's example is derived from the K&R book which defines it differently.
Ok. I wasn't aware that the example *required* doing it the "hard way" :)

Lloyd B.

---

### Post by hey_ram on 2009-03-01
thanx!

that solved the problem. but i still am unclear about the working of this solution. pointers in itself is hard, pointers to pointers doubly so. 

any help/guidance/link would be most welcome. 

@lloyd_b: yes, that was my first thought as well, and the program would have workied like a charm, but the question demanded otherwise.

---

### Post by lloyd_b on 2009-03-02
> **hey_ram said:**
> thanx!

that solved the problem. but i still am unclear about the working of this solution. pointers in itself is hard, pointers to pointers doubly so. 

any help/guidance/link would be most welcome. 

@lloyd_b: yes, that was my first thought as well, and the program would have workied like a charm, but the question demanded otherwise.
The thing to remember is that parameters passed to a function are NOT returned to the caller.  In this case, you were passing a pointer, and then modifying its value, but that modified value was "thrown away" when the function returned.

By passing a pointer to the pointer, you never modify the value of the parameter that was passed - just the contents of the memory it is pointing to (which happens to be a another pointer).  

Don't let yourself get hung up on "a pointer to a pointer". A pointer is a pointer, regardless of whether it points to an int, a float, or another pointer.  The rules are the same - if you're passing a pointer, you can modify the memory that is pointed to, but not the pointer itself.

Lloyd B.

---

