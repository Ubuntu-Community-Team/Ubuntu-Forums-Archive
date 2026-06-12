---
title: "C - rrx encryption - sigabrt problem"
date: 2010-05-25
forum: Programming Talk
---

### Post by ApEkV2 on 2010-05-25
Hey there, I have two questions to ask. One does rrx encryption simply mean you keep rotating the bits of each byte of the key around?
And second, I made this code, but it receives SIGABRT. I compiled with -g and ran with gdb, but that doesn't produce much.
It says something about double free or corruption. I'll post the output too.
I don't know where I'd be freeing twice. If someone could point out what I'm doing wrong as I can't see it.
```
/*____________________________________________________________________________*/
/******************************************************************************/
#include <dirent.h>
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*____________________________________________________________________________*/
/******************************************************************************/	

void Rrx_xor(const char *src, struct stat buf)
{
	FILE *fsrc = fopen(src, "rb+");		        // open in read/write/binary
	if (fsrc == NULL) {
		printf("%10d\n",errno);
		return;
	}

	register unsigned x = 0, y = 0,		        // setup/initialize registers
		key_size = strlen(src),		        // length of the key
		f_size = buf.st_size;		        // size of the file

	unsigned char *key = [color=red]malloc (key_size);  // was the problem[/color]	        // allocate key size
	unsigned char *buffer = malloc(f_size);   	// allocate file size
	if (key) sprintf(key,"%s",src);		        // key is the file name
	if (!fread(buffer, f_size, 1, fsrc)) {	        // read file into buffer
		printf("%10d\n",errno);
		free(buffer);
		fclose(fsrc);			        // exit abort
		free(key);
		return;
	}

	for (; x < f_size; ++x, ++y) {
		if (y == key_size) y = 0;				// don't go beyond the length of the key
		key[y] = (key[y] << 1) | (key[y] >> 7);			// rotate current key byte 1 bit left
		if (!(x % 2))						// is position even?
			buffer[x] ^= (key[y] >> 1) | (key[y] << 7);	// xor with key byte rotated 1 bit right
		else							// else
			buffer[x] ^= (key[y] << 1) | (key[y] >> 7);	// xor with key byte rotated 1 bit left
	}

	rewind(fsrc);				        // rewind file position
	if(!fwrite(buffer, f_size, 1, fsrc)) {	        // overwrite file with buffer
		printf("%10d\n",errno);
	}
	
	free(buffer);
	fclose(fsrc);				        // exit normally
	free(key);
	return;
}

/*____________________________________________________________________________*/
/******************************************************************************/

void Toptier(const char *argv, struct stat buf)
{
	DIR *dirp = opendir(argv);
	if (dirp == NULL) {
		printf("%10d\n",errno);
		return;
	}

	struct dirent *dep;
	while ((dep = readdir(dirp)) != NULL) {
		if (!strcmp(".",dep->d_name) || !strcmp("..",dep->d_name))
			continue;

		char *path = malloc(strlen(argv) + strlen(dep->d_name)+2);
		if (path) sprintf(path,"%s/%s", argv, dep->d_name);
		else 	continue;
		
		switch(dep->d_type) {
			case DT_REG: Rrx_xor(path, buf);
		break;
			case DT_DIR: Toptier(path, buf);
		break;
			default: break;
		}

		free(path);
	}
	closedir(dirp);
	return;
}

/*____________________________________________________________________________*/
/******************************************************************************/

int main(int argc, char *argv[])
{
	int x = 1;
	struct stat buf;
	for (; argv[x] != NULL; ++x) {
		if (!stat(argv[x],&buf)) {
			if (S_ISDIR(buf.st_mode)) {
				Toptier(argv[x], buf);
			}
			else if (S_ISREG(buf.st_mode)) {
				Rrx_xor(argv[x], buf);
			}

		}

	}
	return 0;
}

/*____________________________________________________________________________*/
/******************************************************************************/
```
output from gdb, I have no idea how to read this other than "double free or corruption"
```
Starting program: /home/mclovin/Desktop/a.out '/home/mclovin/firestarter-1.0.3'
         0
         0
         0
         0
         0
         0
         0
         0
         0
*** glibc detected *** /home/mclovin/Desktop/a.out: double free or corruption (!prev): 0x0805b248 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x198ff1]
/lib/tls/i686/cmov/libc.so.6[0x19a6f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x19d7cd]
/home/mclovin/Desktop/a.out[0x804886b]
/home/mclovin/Desktop/a.out[0x8048a48]
/home/mclovin/Desktop/a.out[0x8048a70]
/home/mclovin/Desktop/a.out[0x8048b5d]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x144b56]
/home/mclovin/Desktop/a.out[0x80486c1]
======= Memory map: ========
00110000-0012b000 r-xp 00000000 08:01 886        /lib/ld-2.10.1.so
0012b000-0012c000 r--p 0001a000 08:01 886        /lib/ld-2.10.1.so
0012c000-0012d000 rw-p 0001b000 08:01 886        /lib/ld-2.10.1.so
0012d000-0012e000 r-xp 00000000 00:00 0          [vdso]
0012e000-0026c000 r-xp 00000000 08:01 394059     /lib/tls/i686/cmov/libc-2.10.1.so
0026c000-0026d000 ---p 0013e000 08:01 394059     /lib/tls/i686/cmov/libc-2.10.1.so
0026d000-0026f000 r--p 0013e000 08:01 394059     /lib/tls/i686/cmov/libc-2.10.1.so
0026f000-00270000 rw-p 00140000 08:01 394059     /lib/tls/i686/cmov/libc-2.10.1.so
00270000-00273000 rw-p 00000000 00:00 0 
00273000-0028f000 r-xp 00000000 08:01 3164       /lib/libgcc_s.so.1
0028f000-00290000 r--p 0001b000 08:01 3164       /lib/libgcc_s.so.1
00290000-00291000 rw-p 0001c000 08:01 3164       /lib/libgcc_s.so.1
08048000-08049000 r-xp 00000000 08:01 655613     /home/mclovin/Desktop/a.out
08049000-0804a000 r--p 00000000 08:01 655613     /home/mclovin/Desktop/a.out
0804a000-0804b000 rw-p 00001000 08:01 655613     /home/mclovin/Desktop/a.out
0804b000-08074000 rw-p 00000000 00:00 0          [heap]
b7e00000-b7e21000 rw-p 00000000 00:00 0 
b7e21000-b7f00000 ---p 00000000 00:00 0 
b7fe9000-b7fea000 rw-p 00000000 00:00 0 
b7ffc000-b8000000 rw-p 00000000 00:00 0 
bffeb000-c0000000 rw-p 00000000 00:00 0          [stack]

Program received signal SIGABRT, Aborted.
0x0012d422 in __kernel_vsyscall ()
```

---

### Post by johnl on 2010-05-25
You're not allocating space for the null terminator for your "unsigned char* key".  Even if you are not using it, sprintf() will surely add a null terminator.  This might or might not be the cause of your problem.

Have you tried running your program under valgrind?

---

### Post by johnl on 2010-05-25
I suspect that that's your problem.  Here's what I got from valgrind:


```

ledbettj@reznor:~$ valgrind --leak-check=full ./test ./Temp
==25903== Memcheck, a memory error detector
==25903== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==25903== Using Valgrind-3.5.0-Debian and LibVEX; rerun with -h for copyright info
==25903== Command: ./test ./Temp
==25903==
==25903== Invalid write of size 1
==25903==    at 0x4C2625F: strcpy (mc_replace_strmem.c:303)
==25903==    by 0x400ADE: Rrx_xor (test.c:27)
==25903==    by 0x400D99: Toptier (test.c:77)
==25903==    by 0x400EA3: main (test.c:100)
==25903==  Address 0x51a13a5 is 0 bytes after a block of size 21 alloc'd
==25903==    at 0x4C25153: malloc (vg_replace_malloc.c:195)
==25903==    by 0x400AB1: Rrx_xor (test.c:25)
==25903==    by 0x400D99: Toptier (test.c:77)
==25903==    by 0x400EA3: main (test.c:100)
==25903==
         0
==25903== Invalid write of size 1
==25903==    at 0x4C2625F: strcpy (mc_replace_strmem.c:303)
==25903==    by 0x400ADE: Rrx_xor (test.c:27)
==25903==    by 0x400D99: Toptier (test.c:77)
==25903==    by 0x400DBF: Toptier (test.c:79)
==25903==    by 0x400DBF: Toptier (test.c:79)
==25903==    by 0x400EA3: main (test.c:100)
==25903==  Address 0x51bbd0f is 0 bytes after a block of size 31 alloc'd
==25903==    at 0x4C25153: malloc (vg_replace_malloc.c:195)
==25903==    by 0x400AB1: Rrx_xor (test.c:25)
==25903==    by 0x400D99: Toptier (test.c:77)
==25903==    by 0x400DBF: Toptier (test.c:79)
==25903==    by 0x400DBF: Toptier (test.c:79)
==25903==    by 0x400EA3: main (test.c:100)

```

---

### Post by ApEkV2 on 2010-05-25
And I agree, I changed key to a global [255] and got rid of the dynamic allocation, and it works.
However, I thought I tried adding 1 to malloc and that didn't work.
Turns out I probably made the change and didn't save before compiling/testing.
I lolz fail like that.

I decided to go with a global key, maybe save some ticks by getting rid of some malloc calls.
Here is what I got to work.
```
/*____________________________________________________________________________*/
/******************************************************************************/
#include <dirent.h>
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*____________________________________________________________________________*/
/******************************************************************************/

unsigned char key[255];
void Rrx_xor(const char *src, struct stat buf);
void Toptier(const char *argv,struct stat buf);

int main(int argc, char *argv[])
{
	int x = 1;
	struct stat buf;
	for (; argv[x] != NULL; ++x) {
		if (!stat(argv[x],&buf)) {
			if (S_ISDIR(buf.st_mode)) {
				Toptier(argv[x], buf);
			}
			else if (S_ISREG(buf.st_mode)) {
				Rrx_xor(argv[x], buf);
			}

		}

	}
	return 0;
}

/*____________________________________________________________________________*/
/******************************************************************************/	

void Rrx_xor(const char *src, struct stat buf)
{
	FILE *fsrc = fopen(src, "rb+");			// open in read/write/binary
	if (fsrc == NULL) {
		printf("1%9d\n",errno);
		return;
	}

	register unsigned x = 0, y = 0,			// setup/initialize registers
		key_size = strlen(src),			// length of the key
		f_size = buf.st_size;			// size of the file
	
	for (; x < key_size; ++x) key[x] = src[x];	// load file name into key
	unsigned char *buffer = malloc(f_size);		// allocate file size
	if (!fread(buffer, f_size, 1, fsrc)) {		// read file into buffer
		printf("2%9d\n",errno);
		free(buffer);
		fclose(fsrc);				// exit abort
		return;
	}

	for (x = 0; x < f_size; ++x, ++y) {
		if (y == key_size) y = 0;				// don't go beyond the length of the key
		key[y] = (key[y] << 1) | (key[y] >> 7);			// rotate current key byte 1 bit left
		if (!(x % 2))						// is position even?
			buffer[x] ^= (key[y] >> 1) | (key[y] << 7);	// xor with key byte rotated 1 bit right
		else							// else
			buffer[x] ^= (key[y] << 1) | (key[y] >> 7);	// xor with key byte rotated 1 bit left
	}

	rewind(fsrc);					// rewind file position
	if(!fwrite(buffer, f_size, 1, fsrc)) {		// overwrite file with buffer
		printf("3%9d\n",errno);
	}
	
	free(buffer);
	fclose(fsrc);					// exit normally
	return;
}

/*____________________________________________________________________________*/
/******************************************************************************/

void Toptier(const char *argv, struct stat buf)
{
	DIR *dirp = opendir(argv);
	if (dirp == NULL) {
		printf("%10d\n",errno);
		return;
	}

	struct dirent *dep;
	while ((dep = readdir(dirp)) != NULL) {
		if (!strcmp(".",dep->d_name) || !strcmp("..",dep->d_name))
			continue;

		char *path = malloc(strlen(argv) + strlen(dep->d_name)+2);
		if (path) sprintf(path,"%s/%s", argv, dep->d_name);
		else 	continue;
		
		switch(dep->d_type) {
			case DT_REG: Rrx_xor(path, buf);
		break;
			case DT_DIR: Toptier(path, buf);
		break;
			default: break;
		}

		free(path);
	}
	closedir(dirp);
	return;
}

/*____________________________________________________________________________*/
/******************************************************************************/
```

EDIT: does anyone have anything to say about whether I'm close on the rrx encryption?
I only found one source on google about random rotating xor encryption.
[http://www.acm.org/crossroads/xrds11-3/xorencrypt.html](http://www.acm.org/crossroads/xrds11-3/xorencrypt.html)

---

