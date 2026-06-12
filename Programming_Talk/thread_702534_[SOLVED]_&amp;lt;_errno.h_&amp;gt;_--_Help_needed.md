---
title: "[SOLVED] &amp;lt; errno.h &amp;gt; -- Help needed"
date: 2008-02-20
forum: Programming Talk
---

### Post by adityakavoor on 2008-02-20
Here is my simple C program that checks whether a file has write permission or not .

```

#include<stdio.h>
#include<errno.h>
#include<unistd.h>
#include<sys/types.h>
#include<fcntl.h>


int main(int argc,char *argv[])
{
	int fd;

	fd = open(argv[1],O_WRONLY,0);

	if(fd == -1)
	{
		if(errno == EACCESS)
			printf("No permission\n");

		else if(errno == ENOENT)
			printf("File doesnt exist\n");
	}

	else printf("File opened and is writable\n");
}		


```

There seems to be no problem with ENOENT .

But <errno.h> doesnt recognise EACCESS and I get the following error during compilation. :( :(

```


In function ‘main’:
error: ‘EACCESS’ undeclared (first use in this function)
error: (Each undeclared identifier is reported only once
error: for each function it appears in.)


```

What am I missing here ??? :confused:

---

### Post by lnostdal on 2008-02-20
```
EACCES
```

..see man 2 open .. also see man 2 perror .. you can take advantage of that when printing error messages

---

### Post by adityakavoor on 2008-02-20
changing to EACCES worked :popcorn:

---

### Post by ruy_lopez on 2008-02-20
see also:

```
man strerror
```

Just be careful errno doesn't change between catching the error and printing the associated string.

---

### Post by adityakavoor on 2008-02-20
> **ruy_lopez said:**
> see also:

```
man strerror
```

Just be careful errno doesn't change between catching the error and printing the associated string.

No manual entry for strerror

---

### Post by adityakavoor on 2008-02-20
> **ruy_lopez said:**
> see also:

```
man strerror
```

Just be careful errno doesn't change between catching the error and printing the associated string.


No manual entry for strerror

---

### Post by DoktorSeven on 2008-02-20
> **adityakavoor said:**
> No manual entry for strerror

**sudo apt-get install manpages-dev**

---

### Post by adityakavoor on 2008-02-21
> **DoktorSeven said:**
> **sudo apt-get install manpages-dev**

Thanks. It was useful.

---

