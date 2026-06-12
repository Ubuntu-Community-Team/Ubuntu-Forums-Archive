---
title: "Simple ANSI C program: strange behaviour on 64-bit, works on 32-bit"
date: 2012-07-12
forum: Programming Talk
---

### Post by R33D3M33R on 2012-07-12
I have an unusual problem that I'm struggling to solve for a while now. I have written a simple ANSI C program that takes a string from a file, parses it and returns values. Everything works as expected on 32-bit systems, but it behaves strange on 64-bit system. 

I have tracked down the bug to the **attached** source code (input file is also attached). It should compile with no warnings and work on both architectures, but the difference is the output. 

The output of 32-bit is (as expected):

```

-91480.000000
3.000000
4.000000

```

but on 64-bit is:

```

-9.140000
0.000000
0.000000

```

What is wrong? Thanks in advance!

---

### Post by Tony Flury on 2012-07-12
To me, 

```

while(result != NULL) {
    val=strtok(buf,"=");
    val=strtok(NULL,"=");
    val[strlen(val)-1]=0;
    result[0]=val;
    break;
}

```
is confusing - not saying this is the souce of the problem, but it does not make sense to me. You seem to be tryig to find the 2nd equals sign in val (i.e. the two strtok).

I think this line is superfluous : 

```

val[strlen(val)-1]=0;

```
As the definition of strlen means that there is already a NUL character at position strlen(val)-1.

also the test in the loop seems wrong to me.
Note : Good idea to use code tags in future for small programs.

---

### Post by R33D3M33R on 2012-07-12
Let me explain:

If i read the reference correctly

```
val=strtok(buf,"="); //this should return the first part (a1)
val=strtok(NULL,"="); //this should return the second part (-9.148e+04 3.0 4.0)
val[strlen(val)-1]=0; //this should remove the newline from second part, but as you say it might be unneeded
```

I know the coding might be horrible, but what else can you expect from a guy that started programming in PHP :D

---

### Post by spjackson on 2012-07-12
> **R33D3M33R said:**
> Let me explain:

If i read the reference correctly

```
val=strtok(buf,"="); //this should return the first part (a1)
val=strtok(NULL,"="); //this should return the second part (-9.148e+04 3.0 4.0)
val[strlen(val)-1]=0; //this should remove the newline from second part, but as you say it might be unneeded
```I know the coding might be horrible, but what else can you expect from a guy that started programming in PHP :D
A few printfs would verify those assertions (or debugging in gdb).

There are some issues of detail, however, the fundamental flaw is this. After get_config has been called, what does temp_p point to? It's get_config's val which is an offset into get_config's buf, i.e. an array that has been popped off the stack.

You need to either pass a buffer into get_config to hold the result, or you need to use malloc.

---

### Post by R33D3M33R on 2012-07-12
That seems to be it. After setting char *temp_p to temp_p[256], changing the appropriate values in the get_config function and using strcpy(result,val); it works.
I'm not sure why this wasn't a problem on 32-bit, but it's solved! Thanks!

---

### Post by Tony Flury on 2012-07-12
> **R33D3M33R said:**
> Let me explain:

If i read the reference correctly

```
val=strtok(buf,"="); //this should return the first part (a1)
val=strtok(NULL,"="); //this should return the second part (-9.148e+04 3.0 4.0)
val[strlen(val)-1]=0; //this should remove the newline from second part, but as you say it might be unneeded
```

I know the coding might be horrible, but what else can you expect from a guy that started programming in PHP :D

Strlen does not count to the new line, it counts to the null terminator in the string. Since you ae reading 1024 chars from the file with fgets - if your file is more than 1024 chars long, then you wont get a null terminator (I think) and then strtok and srtlen will fail. 

I thinnk you will find your code fragment will only work in this case since you have one "=" in your input file - try it with two lines (say the 2nd line is "a2=1.6E-9 4.0 0.0" for example), and  I think it will fail - as the 2nd strtok will return the string from the first "=" to the 2nd "=", including line breaks.
The point is that the part you actually want is delimited by a '\n', so it would make more sense to use that as your delimiter in the 2nd strtok call. I might be wrong - been a while since i have used it.

---

### Post by Bachstelze on 2012-07-12
> **Tony Flury said:**
> Strlen does not count to the new line, it counts to the null terminator in the string. Since you ae reading 1024 chars from the file with fgets - if your file is more than 1024 chars long, then you wont get a null terminator (I think) and then strtok and srtlen will fail.

Nope, fgets always null-terminates.

@OP: If you run your program in Valgrind, you will see that you have a lot of memory management problems, *even in 32 bits*. Just because the program appears to work fine does not mean everything is OK. So look into those.

Also strtok() is an abomination and you should really not use it. A good rule of thumb is that if you need strtok() to do your task, it's probably not something you should do in C in the first place.

*EDIT:* That said, here it doesn't look like you really need strtok(). fscanf() or sscanf() should do what you want.

---

### Post by Odexios on 2012-07-12
> **Tony Flury said:**
> To me, 

```

while(result != NULL) {
    val=strtok(buf,"=");
    val=strtok(NULL,"=");
    val[strlen(val)-1]=0;
    result[0]=val;
    break;
}

```
is confusing - not saying this is the souce of the problem, but it does not make sense to me. You seem to be tryig to find the 2nd equals sign in val (i.e. the two strtok).

I think this line is superfluous : 

```

val[strlen(val)-1]=0;

```
As the definition of strlen means that there is already a NUL character at position strlen(val)-1.

also the test in the loop seems wrong to me.
Doesn't the definition of strlen mean that there is a NULL character at position strlen(val), and a valid character at strlen(val) -1 (if and only if, of course, strlen(val) > 0)?

[php]#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[]) {
  
  char *string = "test";

  printf("%d\n%d - %d\n", strlen(string), string[strlen(string)], string[strlen(string)-1]);

  return 0;

}
[/php]

Output:
```
4
0 - 116
```

So, effectively, writing

[php]val[strlen(val)-1] = 0;[/php] means deleting the last non-null character from the string, doesn't it?

---

### Post by Bachstelze on 2012-07-12
> **Odexios said:**
> 
So, effectively, writing

[php]val[strlen(val)-1] = 0;[/php] means deleting the last non-null character from the string, doesn't it?

Yes.

---

### Post by R33D3M33R on 2012-07-15
@Tony Flury: My code also works with multiple =
@Bachstelze: I lack skills for debugging these things, but is it, because I don't free memory after use/clear variables?
@Odexios: I also use this code to load filenames by calling get_config directly. If I omit val[strlen(val)-1] = 0;  from the code, the files won't load. If I use it, everything works

---

