---
title: "Splitting of large files based on a hex value"
date: 2009-02-25
forum: Programming Talk
---

### Post by strycore on 2009-02-25
Ok, say that I have several huge files that I want to split into smaller pieces. The separator for theses files would be some hexadecimal chain (for example : 52 49 46 46 E8 CC 6C 01 (no ASCII characters, just plain hex data)

Is there a nice way to do this with : 
- some bash commands ?
- a python script ?
- some C code ?
- something else ?

---

### Post by Can+~ on 2009-02-25
You'll probably have to open a file in binary [FONT="Courier New"]open("filename", "rb")[/FONT] and [read]("http://docs.python.org/library/stdtypes.html#file.read") bytes until you find it. Then [truncate]("http://docs.python.org/library/stdtypes.html#file.truncate").

---

### Post by stroyan on 2009-02-25
You could do the splitting operation using bash, grep and dd.
bash has a notation for creating strings from hex byte values.
grep has an option to report byte offsets for strings.
dd can skip and copy a specific number of bytes.
This example read from a "data" file and puts the delimiter at the start of each part_n file.

```

#!/bin/bash
part=1
prev=0
for offset in $(grep -bo $'\x52\x49\x46\x46\xe8\xcc\x6c\x01' data )
do
  offset=${offset%%:*}
  if [ ${offset} = 0 ]; then continue; fi
  echo dd from ${prev} to ${offset} into part_${part}
  dd if=data of=part_${part} bs=1 skip=${prev} count=$((${offset}-${prev})) status=noxfer
  prev=${offset}
  let part+=1
done
echo dd from ${prev} to end into part_${part}
dd if=data of=part_${part} bs=1 skip=${prev} status=noxfer

```

---

### Post by geirha on 2009-02-25
Since ghostdog hasn't come around with an elegant awk-solution yet, I thought I'd give it a try myself.
```

$ hd testfile.txt
00000000  66 69 72 73 74 20 70 61  72 74 52 49 46 46 e8 cc  |first partRIFF..|
00000010  6c 01 73 65 63 6f 6e 64  20 70 61 72 74 52 49 46  |l.second partRIF|
00000020  46 e8 cc 6c 01 6c 61 73  74 20 70 61 72 74 0a     |F..l.last part.|
0000002f
$ awk 'BEGIN { RS="\x52\x49\x46\x46\xe8\xcc\x6c\x01" } { printf $0 > FILENAME"."NR }' testfile.txt
$ for file in testfile.txt.*; do echo $file: "$(<$file)"; done
testfile.txt.1: first part
testfile.txt.2: second part
testfile.txt.3: last part

```

---

### Post by soltanis on 2009-02-25
C got long.

```

/* C code */

#include <stdio.h>
#include <assert.h>

char delim[8] = { 0x52, 0x49, 0x46, 0x46, 0xE8, 0xCC, 0x6C, 0x01 };
char file[] = "/path/to/file";
int file_number = 0;

/* you should probably modify this to accept command-line arguments */

/* copy the contents of src to dest */
void copy(FILE *src, FILE *dest, long from_offset, long to_offset) {
	char buf;
	long offset = from_offset;
	fseek(src, SEEK_SET, from_offset);
	while(fread(&buf, 1, sizeof(char), src) > 0 && offset <= to_offset) {
		assert(fwrite(buf, 512, sizeof(char), dest) > 0);
		offset++;
	}
}

/* split the file into two parts. then, modify
	 the file pointer to point to the next file */
int split(long cutoff, FILE **fp) {
	long offset = cutoff, flen;
	FILE *before, *after;
	char before_name[100], after_name[100]; /* eh, filenames < 100 chars */

	/* measure the file length */
	fseek(*fp, SEEK_END, 0);
	flen = ftell(*fp);
	rewind(*fp);

	/* open some files */
	sprintf(before_name, "%s%n", file, file_number++); /* post-incremented */
	sprintf(after_name, "%s%n", file, file_number); /* not incremented */
	assert((before = fopen(before_name, "wb")));
	assert((after = fopen(after_name, "wb")));

	/* now copy the current file up to cutoff into before */
	copy(*fp, before, 0, cutoff);
	/* copy from cutoff to the end into after */
	copy(*fp, after, cutoff, flen);
	
	/* close files */
	fclose(before);
	fclose(after);
	
	/* reset the pointer of fp to the new file */
	fclose(*fp);
	assert((*fp = fopen(after_name, "rb")));

	return 1;
}

/* walk through the file trying to match the delimiter
	 and split the file when the entire delimiter is matched */
void walkfile(FILE *fp) {
	long offset = 0;
	char nextbyte;
	int index = 0, max = 8; /* max is the delimiter's length */
	
	while(fread(&nextbyte, 1, sizeof(char), fp) > 0) {
		offset++;
		
		if(nextbyte == delim[index]) {
			
			if(index == max) { /* matched the entire delimiter */
				assert(split(offset, &fp));
				index = 0;
			} else {
				index++; /* increment matching index */
			}

		} else { /* didn't match, reset index to 0 */
			index = 0;
		}

	}
}

/* adding command-line argument support should probably be done */
int main() {
	FILE *fp;
	assert((fp = fopen(file, "rb")));
	walkfile(fp);
	
	return 0;
}

```

---

### Post by sea_monkey987 on 2009-05-31
story - been googling all over for this.  this is the perfect thread for my issue.  my camcorder records in the DVD-VR format.  I can import the .vro files onto my computer just fine.  However, it's one big file, not separated into multiple files for each time I press record/stop.  i looked in the .vro file with a hex editor.  I found that each "chapter" is separated by constant hex string.


question - How do I split my file using the this hex string?  The bash script doesn't work because grep just says "binary file matches" with no further information.  awk works on my small test file.  As soon as I feed it a video file, it says "ran out on this one".  the C program doesn't seem to actually output any files.  if it does, where would i find them?

---

### Post by soltanis on 2009-05-31
I never tested that program myself, so sorry about that. Hooray for broken solutions posted on forums.

The C program is supposed to output your files thusly: if your file were named "filename", it would split along boundaries into "filename1" "filename2", et cetera.

---

### Post by stroyan on 2009-05-31
You can cure the problem with the bash solution by changing
"grep -bo" to be 
"grep -abo" .
The -a option tells grep to treat binary files as text files.

---

### Post by sea_monkey987 on 2009-05-31
> **stroyan said:**
> You can cure the problem with the bash solution by changing
"grep -bo" to be 
"grep -abo" .
The -a option tells grep to treat binary files as text files.

yeah i saw that in the man page.  I tried it but it doesn't work, unfortunately.  it ends up spitting out a 0 byte part 1 and rest of it in part 2.  I know my test file is setup properly because the awk script spits out two correct parts (i still can't use it to split the video because of the ran out error).

---

### Post by sea_monkey987 on 2009-05-31
> **soltanis said:**
> I never tested that program myself, so sorry about that. Hooray for broken solutions posted on forums.

The C program is supposed to output your files thusly: if your file were named "filename", it would split along boundaries into "filename1" "filename2", et cetera.

don't know what i'm doing wrong.  I changed the array size to 19 and the max size later in the program to 19 (line 62).  the array itself is 
```
0x00, 0x00, 0x01, 0xba, 0x44, 0x00, 0x04, 0x04, 0x94, 0xab, 0x01, 0x89, 0xc3, 0xf8, 0x00, 0x00, 0x01, 0xbd, 0x07
```
i also changed the path to my file.  it's hard-coded for now.

i compiled it using "gcc program.c".  it makes a.exe.  i run a.exe and nothing seems to happen.

p.s. gcc outputs
```
csplit.c: In function `copy':
csplit.c:18: warning: passing arg 1 of `fwrite' makes pointer from integer without a cast
```

---

### Post by soltanis on 2009-05-31
Correction on that same line where the error was flagged:

Should look like this.

```

assert(fwrite(&buf, 512, sizeof(char), dest) > 0);
/* fwrite takes a pointer */

```

This may or may not significantly impact the program.

PS. This was written for a Linux system (sounds like you're running on Windows) but seeing as how it is ANSI C it should be portable between the two.

---

