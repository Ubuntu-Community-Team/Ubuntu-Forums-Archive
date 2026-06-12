---
title: "How to implement this logic"
date: 2009-08-27
forum: Programming Talk
---

### Post by codingfreak on 2009-08-27
In the below function I am trying to read only "STRING_SIZE" number of characters given in "STDIN"(Standard Input). Here STRING_SIZE is 4. So if I enter a string of size more than 4 for str1 then the remaining characters are getting automatically allocated to str2.

So is there a way where I can give strings to both str1, str2 even after giving string > STRING_SIZE.
```

STRING_SIZE=4
getString(char *str)
{
   printf("\nEnter a string of length < %d: ", STRING_SIZE);
   fgets(str, STRING_SIZE, stdin);
   printf("\n\n %s",str);
   fflush(stdin);
}

int main()
{
   getString(str1);
   getString(str2);
}


```

This is in "C" not in other languages

---

### Post by Arndt on 2009-08-27
> **codingfreak said:**
> In the below function I am trying to read only "STRING_SIZE" number of characters given in "STDIN"(Standard Input). Here STRING_SIZE is 4. So if I enter a string of size more than 4 for str1 then the remaining characters are getting automatically allocated to str2.

So is there a way where I can give strings to both str1, str2 even after giving string > STRING_SIZE.
```

STRING_SIZE=4
getString(char *str)
{
   printf("\nEnter a string of length < %d: ", STRING_SIZE);
   fgets(str, STRING_SIZE, stdin);
   printf("\n\n %s",str);
   fflush(stdin);
}

int main()
{
   getString(str1);
   getString(str2);
}


```

This is in "C" not in other languages

Why not read the line into a bigger buffer (80 characters or so), and then just extract the first four ones?

---

### Post by Krupski on 2009-08-27
> **codingfreak said:**
> In the below function I am trying to read only "STRING_SIZE" number of characters given in "STDIN"(Standard Input). Here STRING_SIZE is 4. So if I enter a string of size more than 4 for str1 then the remaining characters are getting automatically allocated to str2.

So is there a way where I can give strings to both str1, str2 even after giving string > STRING_SIZE.
<snip>
This is in "C" not in other languages

It only LOOKS like it doesn't work because you have no newline after printing the value of "str" in the function.

This code (yours, with a few additions), seems to do what you want:


```

#include <stdio.h>

int STRING_SIZE=4;
int getString(char *);

int getString(char *str)
{
   printf("\nEnter a string of length < %d: ", STRING_SIZE);
   fgets(str, STRING_SIZE, stdin);
   fflush(stdin);
   printf("\n\n%s\n\n",str);
   return 0;
}


int main(void)
{

   char str1[1024];
   char str2[1024];

   getString(str1);
   getString(str2);

   fprintf(stdout, "%s\n", str1);
   fprintf(stdout, "%s\n", str2);

   return 0;
}

```


And here is the resulting output from running the code above:

```

Enter a string of length < 4: 123456789


123


Enter a string of length < 4: abcdefghi


abc

123
abc

```

Seems like it works to me...?

-- Roger

(edit to add): The reason you only see THREE characters is that the fourth one is the end of line (null).

---

### Post by codingfreak on 2009-08-27
> **Krupski said:**
> It only LOOKS like it doesn't work because you have no newline after printing the value of "str" in the function.

This code (yours, with a few additions), seems to do what you want:


```

#include <stdio.h>

int STRING_SIZE=4;
int getString(char *);

int getString(char *str)
{
   printf("\nEnter a string of length < %d: ", STRING_SIZE);
   fgets(str, STRING_SIZE, stdin);
   fflush(stdin);
   printf("\n\n%s\n\n",str);
   return 0;
}


int main(void)
{

   char str1[1024];
   char str2[1024];

   getString(str1);
   getString(str2);

   fprintf(stdout, "%s\n", str1);
   fprintf(stdout, "%s\n", str2);

   return 0;
}

```And here is the resulting output from running the code above:

```

Enter a string of length < 4: 123456789


123


Enter a string of length < 4: abcdefghi


abc

123
abc

```Seems like it works to me...?

-- Roger

(edit to add): The reason you only see THREE characters is that the fourth one is the end of line (null).

What is the compiler you are using ??

I am using GCC. And if I run your program I am still getting same problem.
```
$ gcc -v
Using built-in specs.
Target: i386-redhat-linux
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-bugurl=http://bugzilla.redhat.com/bugzilla --enable-bootstrap --enable-shared --enable-threads=posix --enable-checking=release --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-languages=c,c++,objc,obj-c++,java,fortran,ada --enable-java-awt=gtk --disable-dssi --enable-plugin --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-1.5.0.0/jre --enable-libgcj-multifile --enable-java-maintainer-mode --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --disable-libjava-multilib --with-cpu=generic --build=i386-redhat-linux
Thread model: posix
gcc version 4.3.0 20080428 (Red Hat 4.3.0-8) (GCC) 
``````
$ ./a.out 

Enter a string of length < 4: 12345678


123


Enter a string of length < 4: 

456

123
456
```

---

