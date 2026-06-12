---
title: "[SOLVED] Need Help:C programming: The return values of S_ISREG, S_ISDIR via stat"
date: 2007-12-29
forum: Programming Talk
---

### Post by fyplinux on 2007-12-29
I write a simple program that scan all the children of a directory, and try to get some properties of each file.

here is the code:
```

int en(char *arg)
{
	printf("arg:\n%s\n",arg);
	
	struct dirent **namelist;
	struct stat *file_info;
    int n;
    
    n = scandir(arg, &namelist, 0, alphasort);
    if (n < 0)
        perror("scandir");
    else {
		file_info =  malloc(sizeof(stat));
		printf("name\t\t\t\ttype\t\length\n");
        while(n--) {
			
			properties(namelist[n]);
			stat(namelist[n]->d_name,file_info);//need to check whether it succeed
			
			//to determine whether it is a directory
			printf("\nis_directory %d\n",S_ISDIR(file_info->st_mode));
			printf("is regular file %d\n",S_ISREG(file_info->st_mode));
            printf("is socket %d\n",     S_ISSOCK(file_info->st_mode)); 
			free(namelist[n]);
			
        }
        free(namelist);
    }

	
	return 0;
}

void properties(struct dirent *dirent)
{

	printf("\n%s\t",dirent->d_name);
	printf("%d\t",dirent->d_type);
	printf("%d\t",dirent->d_reclen);
}

```

the output of scanning a directory:
```

/home/src/filelist/src/files
name                            type    length

xlib-manual.tar.gz      8       32
is_directory 0
is regular file 0
is socket 0

note    8       16
is_directory 0
is regular file 0
is socket 0

b       4       16
is_directory 0
is regular file 0
is socket 0

a.jpg   8       20
is_directory 0
is regular file 0
is socket 0

a       4       16
is_directory 0
is regular file 0
is socket 0

S5958v2.pdf     8       24
is_directory 0
is regular file 0
is socket 0

Link to Link to Documentation   10      44
is_directory 0
is regular file 0
is socket 0

Link to Advanced Unix programming-zh    10      48
is_directory 0
is regular file 0
is socket 0

Changeofaddressform_website1.doc        8       44
is_directory 0
is regular file 0
is socket 0

..      4       16
is_directory 1
is regular file 0
is socket 0

.       4       16
is_directory 1
is regular file 0
is socket 0


```

my question is:
1. it seems that only . and .. are recognized as directory, although both a and b are directories.why?
2. . and .. is considered as socket, which is indicated by the return value of S_ISSOCK

These behaviors are strange, it might be the problem of my code.

---

### Post by fyplinux on 2007-12-29
I modified the code: a name_buf is used to store the path, which could be used in stat(name_buf,file_info);

Then, it could determine which one is a directory, which one is a regular file.

```

int en(char *arg)
{
	printf("arg:\n%s\n",arg);
	
	struct dirent **namelist;
	
	char name_buf[111] = "";
    int n;
    
    n = scandir(arg, &namelist, 0, alphasort);
    if (n < 0)
        perror("scandir");
    else {
			struct stat *file_info;
		file_info =  malloc(sizeof(stat));
		printf("name\t\t\t\ttype\t\length\n");
        while(n--) {
		
			
			properties(namelist[n]);
			strcat(name_buf,arg);
			strcat(name_buf,namelist[n]->d_name);
			printf("%s\n",name_buf);
			stat(name_buf,file_info);//need to check whether it succeed
			
			//to determine whether it is a directory
			printf("\nis_directory %d\n",S_ISDIR(file_info->st_mode));
			printf("is regular file %d\n",S_ISREG(file_info->st_mode));
            printf("is socket %d\n",     S_ISSOCK(file_info->st_mode)); 
			printf("is link %d\n",     S_ISLNK(file_info->st_mode));
			free(namelist[n]);
			
			strcpy(name_buf,"");
			
			
        }
        free(namelist);
    }

	
	return 0;
}


```

**other problems appeared:**

First,If I allocate the memory space of file_info inside the while loop, there is *** glibc detected *** malloc(): memory corruption (fast ...
 
```

while(n--) {
		     file_info =  malloc(sizeof(stat));/*---allocate---*/
			
			properties(namelist[n]);
			strcat(name_buf,arg);
			strcat(name_buf,namelist[n]->d_name);
			printf("%s\n",name_buf);
			stat(name_buf,file_info);//need to check whether it succeed
			
			//to determine whether it is a directory
			printf("\nis_directory %d\n",S_ISDIR(file_info->st_mode));
			printf("is regular file %d\n",S_ISREG(file_info->st_mode));
            printf("is socket %d\n",     S_ISSOCK(file_info->st_mode)); 
			printf("is link %d\n",     S_ISLNK(file_info->st_mode));
			free(namelist[n]);
			
			strcpy(name_buf,"");
			
			
        }
```
this problem remains even if I free the space before the allocation.

Second,  A link to a directory got the result like:


Link to b       10      24      /home/jing/Desktop/project_sync/src/filelist/src/files/Link to b

is_directory 1
is regular file 0
is socket 0
is link 0

A link to a regular file got the result:

Link to note    10      24      /home/jing/Desktop/project_sync/src/filelist/src/files/Link to note

is_directory 0
is regular file 1
is socket 0
is link 0

---

### Post by Compyx on 2007-12-30
I haven't looked at your code in depth, but one problem caught my eye:
```

file_info = malloc(sizeof(stat));

```
Here, you're allocating memory for a function-pointer, not for the struct 'stat'.
```

file_info = malloc(sizeof(struct stat));

```
Should do the trick, or my personal way of doing it:
```

file_info = malloc(sizeof *file_info);

```

C doesn't magically create tags for structs, so you always need to prepend 'struct'.

BTW: you should always check the return value of malloc(), something like:
```

if (file_info == NULL) {
    fprintf(stderr, "%s:%d: crap! I couldn't allocate %ld bytes!\n",
            __FILE__, __LINE__, (unsigned long)sizeof(*file_info));
    /* clean up and exit */
}

```

---

### Post by fyplinux on 2007-12-30
> **Compyx said:**
> I haven't looked at your code in depth, but one problem caught my eye:
```

file_info = malloc(sizeof(stat));

```
Here, you're allocating memory for a function-pointer, not for the struct 'stat'.
```

file_info = malloc(sizeof(struct stat));

```
Should do the trick, or my personal way of doing it:
```

file_info = malloc(sizeof *file_info);

```

Or, could I do it in this way?
			```
file_info = malloc(sizeof(struct stat));
```

---

### Post by stroyan on 2007-12-30
You can use```
file_info = malloc(sizeof(struct stat));
```, which Compyx already said.  It is not clear from the code fragment that you need to use malloc for file_info.  If you are just keeping one value at a time then you can just declare file_info as a struct and pass its address```
struct stat file_info;
stat(name_buf,&file_info);
printf("\nis_directory %d\n",S_ISDIR(file_info.st_mode));
```
You should reexamine your use of name_buf.  Paths can be much larger than 111 characters.  You can get the limit on paths under a mount point by calling pathconf().  Using strncat instead of strcat would allow you to protect from buffer overruns when assembling name_buf values.  (Or you could just use strlen to check for length limits.)

---

### Post by fyplinux on 2007-12-30
thank you all.I think now I got my answer. and stroyan has given me a good point of memory management.

the second problem could be solved by using lstat(),rather than stat().

---

### Post by fyplinux on 2007-12-30
> **stroyan said:**
> 
You should reexamine your use of name_buf.  Paths can be much larger than 111 characters.  You can get the limit on paths under a mount point by calling pathconf().  Using strncat instead of strcat would allow you to protect from buffer overruns when assembling name_buf values.  (Or you could just use strlen to check for length limits.)

It is a good point, but it seems pathconf() is not good enough to deal with this problem.

The relevant macros to the length could be: 
```

_PC_NAME_MAX
    returns the maximum length of a filename in the directory path or filedes. the process is allowed to create. The corresponding macro is _POSIX_NAME_MAX. 

_PC_PATH_MAX
    returns the maximum length of a relative pathname when path or filedes is the current working directory. The corresponding macro is _POSIX_PATH_MAX.

```
The maximum valid path name length could be calculated by:
```
_PC_PATH_MAX*_PC_NAME_MAX
```
as each relative pathname could be as long as _PC_NAME_MAX

my current ubuntu 7.10 system has the properites:
      max length of file name: 255
     max length of relative path: 4096
while 255*4096 is a huge number, the calculation is not reasonably useful to get the limitation of the length of the pathname.

But we do need to limit the length of the buff_name, which could be specified by the programmer.

Any idea?

---

### Post by stroyan on 2007-12-30
The maximum length of a path to a file is simply _PC_PATH_MAX characters.
You don't need to multiply that by _PC_NAME_MAX.
_PC_NAME_MAX is the maximum length of one file (or directory) name.
Both limits apply.  You don't need to allocate more then _PC_PATH_MAX characters for a path buffer.  But you may need to deal with an overflow of that limit.  You should check that the path fits in that limit and error out if it is exceeded.

---

