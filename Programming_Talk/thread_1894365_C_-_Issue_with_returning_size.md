---
title: "C - Issue with returning size"
date: 2011-12-12
forum: Programming Talk
---

### Post by Anstice on 2011-12-12
Hi guys,

I'm creating a simple application in C that lists the size of everything in a directory. I searched around and started using stat to do so but whenever I run the code it returns the same file size for every file. 


```

#include <stdio.h>
#include <dirent.h>
#include <sys/types.h>
#include <sys/stat.h>

main ()
{
    DIR *dir;
    struct dirent *ent;
    struct stat fileStat;
    dir = opendir (".");

        if (dir != NULL) 
	{
	    while ((ent = readdir (dir)) != NULL) 
	    {
                printf ("%d\n", fileStat.st_size);
	    }
	    closedir (dir);
	} 	
	else 
	{
	    /* could not open directory */
	    perror ("");
	}
}
```

Here are the results of ls -l in that directory to show they should all be different sizes.

```

drwxr-xr-x 2 tom tom 4096 Dec 12 08:45 1
drwxr-xr-x 2 tom tom 4096 Dec 12 08:38 2
drwxr-xr-x 2 tom tom 4096 Dec  8 18:32 applet - circuit
drwxr-xr-x 2 tom tom 4096 Dec  9 07:55 applet - gas
drwxr-xr-x 2 tom tom 4096 Dec  7 19:11 applet - liquid
lrwxrwxrwx 1 tom tom   45 Dec  8 18:30 circuit.html
-rwxr-xr-x 1 tom tom 4645 Dec 12 08:47 cwTest2
-rw-r--r-- 1 tom tom  356 Dec 12 08:47 cwTest2.c
-rwxr-xr-x 1 tom tom 4645 Dec 12 08:47 cwTest2.exe
-rw-r--r-- 1 tom tom  322 Dec 12 07:55 cwTest.c
-rwxr-xr-x 1 tom tom 5070 Dec 12 15:58 ffffuuuuuu
-rw-r--r-- 1 tom tom  533 Dec 12 15:58 ffffuuuuuu.c
lrwxrwxrwx 1 tom tom   41 Dec  9 07:55 gas.html
lrwxrwxrwx 1 tom tom   44 Dec  7 19:11 liquid.html

```

Results of running the program.

```

tom@x60deb:~/Desktop$ ./ffffuuuuuu 
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504
134513504

```
I'm guessing it's something really simple and I'll end up kicking myself but I'm pretty new to C programming.

advTHANKSance,
Tom.

EDIT: Added results of running the program

---

### Post by ofnuts on 2011-12-12
Your code is expecting the stat fairy to fill the structure...

---

### Post by Anstice on 2011-12-12
I added an if in the while to stat based on an example I saw but now all I get is the same in a different format. Now it just shows 4069 instead of 134513504.

```

if (stat(".",&fileStat) == 0)
{
    printf ("%d\n", fileStat.st_size);
}

```

---

### Post by ofnuts on 2011-12-12
> **Anstice said:**
> I added an if in the while to stat based on an example I saw but now all I get is the same in a different format. Now it just shows 4069 instead of 134513504.

```

if (stat(".",&fileStat) == 0)
{
    printf ("%d\n", fileStat.st_size);
}

```This is the size of your directory file, which is what you asked. You have to iterate your directory entries as returned by readdir() and call stat() on each.

---

### Post by Anstice on 2011-12-12
Oh I see. It works now, thank you very much.

---

