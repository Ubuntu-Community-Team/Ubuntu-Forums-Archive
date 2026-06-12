---
title: "veryvery simply question about complieing c"
date: 2009-06-04
forum: Packaging and Compiling Programs
---

### Post by jjbin on 2009-06-04
I follow a info from a page in Ubuntu to 
first run my C

here is the expl

Now you need to open first.c file

sudo gedit first.c

add the following lines save and exit the file 


```
#include <stdio.h>

int main()
{
printf("hello world\n");
return 0;
}

```

Firstly compile the code using the following command

cc -c first.c

that would produce an object file you may need to add to the library.

then create an executable using the following command

cc -o first first.c

Now run this executable using the following command

./first

Output should show as follows

Hello, world

I am vervvery beginner 
who can explain to me
why at last should type ./first

what about this command
"cc -o first first.c"

or somebody could give me a more
suitable place to ask for the newie

---

### Post by x33a on 2009-06-04
1) ./first

here, first is the executable, like an exe file in windows.

./ specifies to look for the exec in the current directory, otherwise you'll have to add it to the system PATH.

2) cc -o first first.c

means to place the output of the compiled file into first, the executable file.

look into
```
man gcc
```

for all the switches and other compiler specific options.

---

