---
title: "help with utimbuf struct in C"
date: 2007-10-19
forum: Programming Talk
---

### Post by DFord425 on 2007-10-19
I am doing a programming assignment for one of my classes and i have to write a version of the touch command.  I need some help with the utimbuf struct.  I am trying to change the access and modification times. Here is my code```
void update_file_info(char* filename, struct stat *info_p)
{
	struct utimbuf time;
	utime(filename, time);
	
}
```
The problem i have is that the compiler says
```
touch1.c:80: error: storage size of ‘time’ isn’t known

```
Any help is appreciated.

---

### Post by public_void on 2007-10-20
You are passing a structure to utime, when it requires a pointer to that structure. The definition is:

int utime (const char *FILENAME, const struct utimbuf *TIMES)

Therefore your code should be:
```

void update_file_info(char* filename, struct stat *info_p)
{
    struct utimbuf time;
    utime(filename, &time);
    
}

```

---

### Post by DFord425 on 2007-10-20
When i tried that i got the same error when compiling. But it worked when i did this
```
void update_file_info(char *filename, struct stat *info_p)
{
	struct utimbuf *time;
	utime(filename, time);
	
}
```
Thanks for you help

---

