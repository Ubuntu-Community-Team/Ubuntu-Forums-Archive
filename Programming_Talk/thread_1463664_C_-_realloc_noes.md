---
title: "C - realloc noes?"
date: 2010-04-27
forum: Programming Talk
---

### Post by ApEkV2 on 2010-04-27
I can't seem to get this function to work with realloc. It segfaults either in fputs or in realloc itself.
Is it because I used memset?  I have a fix, although I would rather use realloc.

I have the output from gdb, but I'm not home right now to get that.
It says something about strlen in stdlib.h idk.

```
[color=green]// with realloc that doesn't work[/color]
void KO_file(char *path)
{
	FILE* fdes = fopen(path,"r+");
	if (fdes == NULL) return;
	struct stat buf;
	stat(path,&buf);
	
	unsigned int temp = _7MEG < buf.st_size ? _7MEG : buf.st_size;
	unsigned int x = 0, re_size;
	char *buffer = malloc(temp);
	buffer = memset(buffer, 0x01, temp);
	
	while (x < buf.st_size) {
		if (x+temp <= buf.st_size) {
			fputs(buffer, fdes);
			fflush(fdes);
			x += temp;
		} else {
			re_size = buf.st_size-x;
			[color=red]buffer = realloc(buffer, re_size);[/color]
			[color=red]fputs(buffer, fdes);[/color]
			x += re_size;
		}
	}
		
	free(buffer);
	fclose(fdes);
	unlink(path);
}
```


```
[color=green]// with the fix that works[/color]
void KO_file(char *path)
{
	FILE* fdes = fopen(path,"r+");
	if (fdes == NULL) return;
	struct stat buf;
	stat(path,&buf);
	
	unsigned int temp = _7MEG < buf.st_size ? _7MEG : buf.st_size;
	unsigned int x = 0, re_size;
	char *buffer = malloc(temp);
	buffer = memset(buffer, 0x01, temp);
	
	while (x < buf.st_size) {
		if (x+temp <= buf.st_size) {
			fputs(buffer, fdes);
			fflush(fdes);
			x += temp;
		} else {
			re_size = buf.st_size-x;
			[color=blue]char *string = malloc(re_size);
			string = memset(string, 0x01, re_size);
			fputs(string, fdes);
			free(string);[/color]
			x += re_size;
		}
	}
		
	free(buffer);
	fclose(fdes);
	unlink(path);
}
```

---

### Post by MadCow108 on 2010-04-27
why not use fwrite in the first place?
no need to realloc the memory.

anyway the problem is that your buffer is not null terminated as fputs expects it
it actually can crash in both cases not only the realloc one.

---

### Post by ApEkV2 on 2010-04-27
I thought that the null byte was there by default, but to make sure I did this.
Still segfaults. 

```

char *ptr;
ptr = buffer+strlen(buffer)-1;
*ptr = '\0';
```

And also I was under the impression that fwrite calls fputc which I want to avoid at all cost.

---

### Post by MadCow108 on 2010-04-27
strlen, as all string related functions, also expects a null termination...
without it gives undefined behavior
null termination only gets added by some string related functions like sprintf, fgets...
never by memory block related functions like malloc, memset...

and I don't think fwrite calls fputc
are you sure about that?
if it does then fputs probably also calls fputc, because fputs is just the string variant of fwrite

if you must use fputs do it like this:
buffer[buf.st_size-x] = 0;
fputs(buffer, fdes);

---

### Post by ApEkV2 on 2010-04-27
Yeah, I just thought about that, strlen does require one. (i lulz fail)
But how come the second function works at least over 16,000 to 1.

edit: didn't see your edit
Could I just throw together some wrapper functions for memset and realloc that appends a null byte automatically?
something like...
```
void *Memset(void *s, int c, size_t n)
{
        s = memset(s,c,n);
        s[n-1] = '\0';
        return s;
}
```
```
void *Realloc(void *ptr, size_t size)
{
        ptr = realloc(ptr,size);
        ptr[size-1] = '\0';
        return ptr;
}
```

I'm not sure about the whole fputc fputs fwrite thing, because from my observation I find a single call to fputs is much faster than the amount of calls required to fputc. I'll have to check again once I get home.

Your solution looks good, I'll have to try it once I get home.

---

### Post by MadCow108 on 2010-04-27
in your second case you alloc new memory, it is not unlikely that that memory has been set to zero at some time.
but in the first case the memory beyond the memory boundary has been set by you to a non zero value a few lines above with the memset, so it will always overflow in fputs

---

### Post by Cracauer on 2010-04-27
fputc, fputs and fwrite are all in the buffered stdio collection. Their performance is generally dominated by the actual write(2) system call that will eventually result after one or more calls to these functions. 

Insofar it generally doesn't make much sense to microoptimize around them. Just use whichever is most applicable to the situation. There is never a good reason to replace a fwrite with fputs (and vice versa) if you have to go through a setup of the buffers.

If you are worried about performance then you need to start realizing that in C the strlen(3) function is extremely expensive. In your code you call it like it is free candy.

You also lack error checking.

---

### Post by ApEkV2 on 2010-04-27
@madcow, so the wrapper functions should correct this?


@cracauer, I don't believe I directly call strlen once in my function.
I'm not worried about performance, I just want the code to be efficient and look nice.
Your right, should've checked stat.

So, appending a null byte to the buffer will fix all the problems in the world?
EDIT: seems to be working, are my wrappers ok? (changed: i'm not using them anymore)
```
void KO_file(char *path)
{
	FILE* fdes = fopen(path,"r+");
	if (fdes == NULL) return;
	struct stat buf;

	if (!stat(path,&buf)) {	
		unsigned int x = 0, re_size, temp = _7MEG < buf.st_size ? _7MEG : buf.st_size;
		char *buffer = malloc(temp);
		buffer = memset(buffer, 0x01, temp);
		buffer[temp-1] = '\0';
	
		while (x < buf.st_size) {
			if (x+temp <= buf.st_size) {
				fputs(buffer, fdes);
				fflush(fdes);
				x += temp;
			} else {
				re_size = buf.st_size - x;
				buffer = realloc(buffer, re_size);
				buffer[re_size-1] = '\0';
				fputs(buffer, fdes);
				x += re_size;
			}
		}
		
		free(buffer);
		fclose(fdes);
		unlink(path);
	}
}

/*//////////////////////////////////////////////////*/

void *Memset(void *s, int c, size_t n)
{
	char *buf = memset(s, c, n);
	buf[n-1] = '\0';
	return (void*)buf;
}

/*//////////////////////////////////////////////////*/

void *Realloc(void *ptr, size_t size)
{
	char *buf = realloc(ptr, size);
	buf[size-1] = '\0';
	return (void*)buf;
}
```

---

