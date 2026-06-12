---
title: "strncat and file read help"
date: 2008-06-23
forum: Programming Talk
---

### Post by crashovaride on 2008-06-23
Hello,

I'm writing an application to read a file, and below is the code. Unfortunately, i can't get the file read function to work. After replacing strcat with strncat for a more secure method, i still get "Segmentation Fault (core dumped)" errors. This error is stemming from the read function. Here below, is the exact code...

[PHP]
int read_xml()
{
	char * uname_user = NULL;				
	char * fullpath = NULL;				
	char * fullfolder_directory = NULL;
	char buffer[225];
	uname_user = getenv("HOME");
        fullfolder_directory = strncat(uname_user, "/filedata.log", 255-1);
	printf("Searching for data in: %s\n", getenv("HOME"), fullfolder_directory, 255-1);
        FILE *f;
        readfile = fopen(fullfolder_directory, 255-1), "r");
                while (!feof(readfile))
                {
                if (readfile != NULL)
                {
                }
                //OPEN TMP FILE
                f = fopen("/tmp/outdata.log", "a+");
                        fgets(buffer, 256, readfile);
			if (strstr(buffer, "<quote>"))
			{
				printf("Extracting Quote: %s", buffer);
                        	fprintf(f, "Quote: %s", buffer);
			}
			else if(strstr(buffer, "<author>"))
			{
				printf("Extracting Author: %s", buffer);
                        	fprintf(f, "Extracting Author: %s", buffer);
			}
		}
	fclose(f);
	fclose(readfile);
	printf("Quotations have been successfully extracted.\n");
     return 0;
[/PHP]

Any ideas why this section is bombing badly? Any help would be appreciated. 
Thank you.

Kindest Regards.

---

### Post by Hubi17 on 2008-06-23
I'm not entirely sure, but don't you need to allocate memory for the *char** before you can assign them a value?!?!

What i mean is that before a command like:
*uname_user = getenv("HOME");*
you need to do some sort of *alloc* or *malloc*.
Same goes for the other pointers, otherwise I think you just have one char space reserved from memory and not the entire block needed to hold ur string.

---

### Post by geirha on 2008-06-23
You are trying to append "/filedata.log" to uname_user, which is a pointer returned by getenv(). You shouldn't do that, and that's what you get segmentation fault for. Use a buffer variable, either malloced or sufficiently large. e.g.
[php]
char *fullpath; //or possibly: char fullpath[1024]; if you don't want to use malloc
//...
fullpath= malloc((strlen(uname_user)+strlen("/filedata.log")+1)*sizeof(char));
strcpy(fullpath, uname_user);
strcat(fullpath, "/filedata.log");
//...
free(fullpath);
[/php]

It's a good idea to use the safer strncpy and strncat functions instead. And sprintf() is probably easier to use.

---

### Post by WW on 2008-06-23
The call to getenv() is fine.  After that call, user_name points to memory holding the value of the environment variable if it is, in fact, defined.  The problem (assuming "HOME" is defined and getenv() succeeds) is the call to strncat.  You don't know how big the buffer is that holds the value of the environment value, so it is not safe to try to append more to it.  If this statement does not cause a segfault, it is only because you are lucky.

The C string functions do not do any memory management; *you* have to ensure that memory is correctly allocated for all your strings. *Edit:* geirha shows one way (actually two ways, if you count the alternative mentioned in the comment) to handle this.

---

### Post by dwhitney67 on 2008-06-23
I assign a 50% score to the usage of getenv().  A better usage would have been:
[PHP]const char *uname_user = getenv( "HOME" );[/PHP]
The rationale behind declaring uname_user as const is to prevent it from being assigned another value.

Or better yet, forgo the assignment, and get to the heart of the matter:
[PHP]char filename[1024] = {0};
snprintf( filename, sizeof(filename), "%s/%s", getenv("HOME"), "filedata.log" );[/PHP]

I always compile C programs with the following compiler options:
```
gcc -Wall -pedantic -std=c99
```


P.S.  The read_xml() function is "doing" too much.  Break it apart!  The filename, or better yet the FILE pointer (for the "filedata.log" file) should be passed to it as a parameter.

---

### Post by crashovaride on 2008-06-24
whoa that is a lot of information and i will do my research on malloc and additional memory management. I shall declare that i'm not taking a college or online class for this. I'm trying to learn this on my own. And, most of the resources im using are eh. I have something like 4 books on the matter, and i have to cross reference each one. I've even posted about resources which aren't that great; and searched for good books which only leads me back to either posting or further frustrations. 

Also, where did most of you learn to program in C? any suggestions? Or, any information in regard to the matter would be appreciated. I would hate to keep pestering people in the help section for help every 1.2 seconds. I would like to learn on my own. =) However, am also grateful for the help provided here.

I do appreciate all the posting replies, and i will take more information from this and dig DEEPER with the methods proposed. I do thank everyone.

Kindest Regards

---

### Post by crashovaride on 2008-06-24
> **dwhitney67 said:**
> I assign a 50% score to the usage of getenv().  A better usage would have been:
[PHP]const char *uname_user = getenv( "HOME" );[/PHP]
The rationale behind declaring uname_user as const is to prevent it from being assigned another value.

Or better yet, forgo the assignment, and get to the heart of the matter:
[PHP]char filename[1024] = {0};
snprintf( filename, sizeof(filename), "%s/%s", getenv("HOME"), "filedata.log" );[/PHP]

I always compile C programs with the following compiler options:
```
gcc -Wall -pedantic -std=c99
```


P.S.  The read_xml() function is "doing" to much.  Break it apart!  The filename, or better yet the FILE pointer (for the "filedata.log" file) should be passed to it as a parameter.


dwhitney67,

Your example ROCKED and helped me develop what i needed!!!!! I did however find a small error in the proposed syntax, in snprintf(filename, sizeof(filename), "%s/%s", getenv("HOME"), " there should only be one %s with no trailing forward slash for the next file name. If the error was intentional to make me work for solving the problem, thank you for putting my limited skills to the test, if it wasn't, i still appreciate the help. Thank you very much.

Kindest Regards.

---

### Post by dwhitney67 on 2008-06-24
You're welcome, however I do not understand your comment concerning the forward-slash and extra %s.

The following program:
[PHP]#include <stdio.h>
#include <stdlib.h>

int main()
{
  char filename[100] = {0};
  snprintf( filename, sizeof( filename ), "%s/%s", getenv( "HOME" ), "firefox.log" );
  printf( "filename = %s\n", filename );
  return 0;
}[/PHP]
yields the expected result of:
```
/home/dwhitney/firefox.log
```

---

### Post by lisati on 2008-06-24
> **dwhitney67 said:**
> p.s.  The Read_xml() Function Is "doing" Too Much.  Break It Apart!  The Filename, Or Better Yet The File Pointer (for The "filedata.log" File) Should Be Passed To It As A Parameter.

+1

---

### Post by crashovaride on 2008-06-25
Actually, you are correct. There was an error on my end. I rebuilt the section and noticed it was ripping data *i believe* from the strncat. Thank you for the quick reply.

---

