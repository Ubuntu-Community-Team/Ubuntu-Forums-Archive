---
title: "Question for C"
date: 2010-10-07
forum: Programming Talk
---

### Post by Kareta on 2010-10-07
In C:

Code is from sample two, [here]("http://members.cox.net/midian/articles/ansic10.htm")
```

/* filecheck.c 1.0 (06.20.98) */
#include <stdio.h>

int main(int argc, char *argv[])
{
   FILE *file_p;
   char FileName[20] = "Testfile.txt";

   if(!(file_p = fopen(FileName, "r")))
   {
      file_p = fopen(FileName,"w");
   }
   fclose(file_p);
   return 0;
}

```When it's looking for the file:
1. Where is it searching for the file? Whatever folder the code is in at the time of execution? Or do I have to specify a file location?
2. Why is it FileName[20]? Why an array?

Sorry if the question is stupid, just a bit confused.

---

### Post by dwhitney67 on 2010-10-07
With the hard-coded constant you provided for the file name, the program will look in the current directory where the application is executed.

As for the hard-coded value of 20 for the array size, it is suitable for the size of the filename that is also hard-coded.  If you were taking input from the user for a filename, and said filename included a long directory path, then it probably would not fit in those 20 characters.

---

### Post by worksofcraft on 2010-10-07
> **Kareta said:**
> 
```

   char FileName[20] = "Testfile.txt";

```

2. Why is it FileName[20]? Why an array?


A text string is of course an array of characters, but actually you make a very valid point: Indeed you really don't have to tell the compiler the size of that text string, because it is quite capable of counting the characters itself:
[php]
#include <stdio.h>
int main() {
	char FileName[] = "Testfile.txt";
	return !printf("FileName array size is %lu\n", sizeof(FileName));
}
[/php]
Note: it's not really php, but I like colors in the listing.
Anyway that gives...
```

$> g++ t.c
$> ./a.out
FileName array size is 13

```
So telling it to allocate 20 was just wasting some space in memory and could cause problems if you wanted to make the file name longer :shock:

---

