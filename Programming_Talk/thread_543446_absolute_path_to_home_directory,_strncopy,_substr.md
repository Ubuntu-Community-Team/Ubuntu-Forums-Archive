---
title: "absolute path to home directory, strncopy, substr"
date: 2007-09-05
forum: Programming Talk
---

### Post by nzadLithium on 2007-09-05
hey

I'm having problems with the stuff in the title.

I'm using c.

I want to store the path to the currently logged in users home directory in a string. Can someone give me an example of how to do?

Also i am taking a path to a program. Say mozilla

and i get the path /usr/local/mozilla or wherever it is

i then want to take off the /usr/local/ and only be left with mozilla in my variable.

I tried strncpy like its shown on this page [http://www.kalamazoolinux.org/pipermail/programming/2003-July/000177.html](http://www.kalamazoolinux.org/pipermail/programming/2003-July/000177.html)

i have this

void browserOK()
{
	if (browseSelect == 1)
	{
		browseReturn = 	gtk_file_selection_get_filename (GTK_FILE_SELECTION (browser));
		**strncpy(browseReturnCheck, browseReturn+9 , 9);**
		printf ("%s\n", browseReturnCheck);
	}
	browseSelect = 0;
}

gives me no errors on compile but when i run it i get segmentation fault.

I also tried
"browseReturnCheck = browseReturn.substr (position, length)".

I get this from using substr

main.c:53: warning: implicit declaration of function ‘substr’
main.c:53: warning: assignment makes pointer from integer without a cast
/tmp/ccAmRPk2.o: In function `browserOK':
main.c:53: undefined reference to `substr'
collect2: ld returned 1 exit status

hellllllllllllllllpppppppppppppppppppppppp

---

### Post by prospero527 on 2007-09-05
What is browseReturn is it a char *?  If so you can't do something like browseReturn.substr(), strings are not objects in C they are just character pointers.

---

### Post by prospero527 on 2007-09-05
another thing, the segmentation fault is likely due to no memory being allocated for browseReturnCheck.  Either malloc() memory for browseReturnCheck:
```

browseReturnCheck = (char *) malloc(sizeof(char)*strlen(browseReturn)+1);

strncpy(browseReturnCheck, browseReturn, strlen(browseReturn));

```
or use a function like strdup() or strndup():
```

browseReturnCheck = strndup(browseReturn, strlen(browseReturn));

```

hope that helps

---

### Post by lloyd_b on 2007-09-05
> **nzadLithium said:**
> hey

I'm having problems with the stuff in the title.

I'm using c.

I want to store the path to the currently logged in users home directory in a string. Can someone give me an example of how to do?

Also i am taking a path to a program. Say mozilla

and i get the path /usr/local/mozilla or wherever it is

i then want to take off the /usr/local/ and only be left with mozilla in my variable.

I tried strncpy like its shown on this page [http://www.kalamazoolinux.org/pipermail/programming/2003-July/000177.html](http://www.kalamazoolinux.org/pipermail/programming/2003-July/000177.html)

i have this

void browserOK()
{
	if (browseSelect == 1)
	{
		browseReturn = 	gtk_file_selection_get_filename (GTK_FILE_SELECTION (browser));
		**strncpy(browseReturnCheck, browseReturn+9 , 9);**
		printf ("%s\n", browseReturnCheck);
	}
	browseSelect = 0;
}

gives me no errors on compile but when i run it i get segmentation fault.

I also tried
"browseReturnCheck = browseReturn.substr (position, length)".

I get this from using substr

main.c:53: warning: implicit declaration of function &#8216;substr&#8217;
main.c:53: warning: assignment makes pointer from integer without a cast
/tmp/ccAmRPk2.o: In function `browserOK':
main.c:53: undefined reference to `substr'
collect2: ld returned 1 exit status

hellllllllllllllllpppppppppppppppppppppppp

The simplest way to get the user's home directory is by grabbing the environment variable HOME, using the "getenv()" function.

And as for stripping off the leading elements of a path, the "basename()" function handles that nicely.

```

#include <stdlib.h>
#include <libgen.h>
#include <stdio.h>
#include <string.h>

void main()
{
     char homedir[256];
     char dirname[256];

     strcpy(homedir, getenv("HOME"));

     printf("The contents of HOME are: %s\n", homedir);

     strcpy(dirname, basename(homedir));

     printf("The name of the user's home directory is: %s\n", dirname);
}
```

Note: Be sure to read the man pages for both functions.  "basename()" in particular has a few gotcha's that you need to be aware of.

Lloyd B.

---

### Post by nzadLithium on 2007-09-06
ah thx. i gots that going now.

and that basename command is awesome :)

---

### Post by Compyx on 2007-09-06
> **lloyd_b said:**
> The simplest way to get the user's home directory is by grabbing the environment variable HOME, using the "getenv()" function.

And as for stripping off the leading elements of a path, the "basename()" function handles that nicely.

```

#include <stdlib.h>
#include <libgen.h>
#include <stdio.h>
#include <string.h>

void main()
{
     char homedir[256];
     char dirname[256];

     strcpy(homedir, getenv("HOME"));

     printf("The contents of HOME are: %s\n", homedir);

     strcpy(dirname, basename(homedir));

     printf("The name of the user's home directory is: %s\n", dirname);
}
```

Note: Be sure to read the man pages for both functions.  "basename()" in particular has a few gotcha's that you need to be aware of.

Lloyd B.

Just a few pointers:

'main' returns int, even when invoking gcc without any warning switches it will warn about this.
When including libgen.h you also get a function called dirname, so change the name of the char array `dirname` to something else.
What if strlen(getenv("HOME")) > 256: buffer overflow.
What if strlen(basename(homedir)) > 256: buffer overflow.

---

