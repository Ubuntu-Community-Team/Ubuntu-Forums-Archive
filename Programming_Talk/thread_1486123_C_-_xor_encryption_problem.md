---
title: "C - xor encryption problem"
date: 2010-05-17
forum: Programming Talk
---

### Post by ApEkV2 on 2010-05-17
Hey there, I just started messing with this cryptography book and made this rudimentary xor encryption code to get things going.
The problem is that upon decrypting, the first byte isn't the same and I can't see any problem with the code.
Any help would be appreciated, or a link if this has already been brought up before.
Also using the name as the key is not supposed to be strong at all, just trying to start out small.
```
/*____________________________________________________________________________*/
/******************************************************************************/
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*____________________________________________________________________________*/
/******************************************************************************/

int Encrypt(const char*, struct stat);

int main(int argc, char *argv[])
{
	int x = 1;
	struct stat buf;
	for (; argv[x] != NULL; ++x)
		if (!stat(argv[x],&buf))
			Encrypt(argv[x], buf);
	
	return 0;
}

/*____________________________________________________________________________*/
/******************************************************************************/

int Encrypt(const char *src, struct stat buf)
{
	register int key_size = strlen(src);
	register unsigned x = 0, y = 0, c;
	
	FILE *fsrc = fopen(src, "rb+");
	if (fsrc == NULL) {
		printf("%10d\n",errno);
		return 0;
	}

	for (; x < buf.st_size; ++x, ++y)
	{
		if (y == key_size) y = 0;	// reset key increment
		c = fgetc(fsrc);		// read 1 character
		c ^= src[y];			// XOR with the file name byte
		if (x) fseek(fsrc,x-1,SEEK_SET);// rewind the file position 1 byte
		else rewind(fsrc);		// only for the first byte
		fputc (c, fsrc);		// write xor'd byte
	}
	
	fclose(fsrc);
	
	return 1;
}

/*____________________________________________________________________________*/
/******************************************************************************/
```

---

### Post by soltanis on 2010-05-17
I'd suspect the seeking code. You seem to have done some premature optimization here (with the register ints and all), which isn't really necessary.

I'd just eliminate the seeking thing altogether (stop trying to modify the file in place) and instead just open two files, one in read mode, the other in write mode. If you want one to replace the other, then at the end of writing the second file you can either
1) remove the first and rename the second to the name of the first
or if you are paranoid about people scanning the disk for fragments of the unencrypted file, you can also do
2) reopen the first in write mode, position your write pointer at the front, and then overwrite the entire file with the encrypted data, then remove the second.

---

### Post by ApEkV2 on 2010-05-17
Thanks for the reply, originally I was using two file streams which worked, but decided to go smaller. 
Smaller didn't work, however, I did get rid of seeking and instead am now inputing the xor'd bytes into a buffer.
Then overwrite the file. So now there's only one rewind. And now it works. *tada*
```
/*____________________________________________________________________________*/
/******************************************************************************/
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <unistd.h>
/*____________________________________________________________________________*/
/******************************************************************************/

int Encrypt(const char*, struct stat);

int main(int argc, char *argv[])
{
	int x = 1;
	struct stat buf;
	for (; argv[x] != NULL; ++x)
		if (!stat(argv[x],&buf))
			if (!Encrypt(argv[x], buf))
				return -1;
	
	return 0;
}

/*____________________________________________________________________________*/
/******************************************************************************/

int Encrypt(const char *src, struct stat buf)
{
	register int key_size = strlen(src);
	register unsigned x = 0, y = 0, c;
	
	FILE *fsrc = fopen(src, "rb+");
	if (fsrc == NULL) {
		printf("%10d\n",errno);
		return 0;
	}

	char *buffer = malloc(buf.st_size);
	if (!buffer) return 0;
	for (; (c = fgetc(fsrc)) != EOF && x < buf.st_size; ++x, ++y)
	{
		if (y == key_size) y = 0;
		c ^= src[y];
		buffer[x] = c;
	}

	rewind(fsrc);
	for (x = 0; x < buf.st_size; ++x)
		fputc(buffer[x],fsrc);

        free(buffer);
	fclose(fsrc);
	
	return 1;
}

/*____________________________________________________________________________*/
/******************************************************************************/
```

---

