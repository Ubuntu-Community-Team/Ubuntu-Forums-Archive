---
title: "Write a structure to a file"
date: 2010-03-06
forum: Programming Talk
---

### Post by quanganht on 2010-03-06
I'm new in C and I'm looking for help.
I have an structure, and I tried to write it to a file, binary mode. Neither of them works:
```
write(fd, &desc, sizeof(desc))
```
and
```
fwrite(&desc, sizeof(desc), 1, fd)
```

Nothing get written to file.

---

### Post by napsy on 2010-03-06
How do you open the file?

---

### Post by MadCow108 on 2010-03-06
please show more code.
those lines seem correct but are probably used wrong in a greater context

---

### Post by quanganht on 2010-03-06
The whole damn thing:
```
#include <stdio.h>

struct SB_DESC
{
	char magic[4];
	unsigned int index_num;
	unsigned long data_num;
	unsigned long total_num;
	char name[8];
}

int main()
{
	int c,i;
	void *code;
	FILE *fd, *boot;

	struct SB_DESC desc;

	printf("Building floppy image with BSFS...\n");
	
	fd=fopen("floppy.img","wb");
	boot=fopen("boot","rb");
	if (boot==NULL)
	{
		printf("boot binary does not exist!");
		exit(0);
	}
	
	while ((c=fgetc(boot))!=EOF)	// copy boot binary
	{
		fputc(c,fd);
	}
	fclose(boot);
	
	//TODO: add code for inserting missing datas and kernel files.

	desc.magic[1]='B';
	desc.magic[2]='S';
	desc.magic[3]='F';
	desc.magic[4]='S';
	desc.index_num=32;
	desc.data_num=2847;
	desc.total_num=2880;
	
	for (i=0;0<=8;i++)
		desc.name[i]=' ';
	
	if (fwrite(&desc, sizeof(desc), 1, fd) == NULL)
		printf("ERROR!\n");

	fputc(0x55,fd); fputc(0xAA,fd);

	fflush(fd);

	fclose(fd);

	printf("Done!\n\n");
}
```

---

### Post by quanganht on 2010-03-06
I got it working now. Thanks guys for helping.
Close thread plz.

---

### Post by SledgeHammer_999 on 2010-03-06
Maybe post the solution for others to benefit too?

---

### Post by MadCow108 on 2010-03-06
theres a buffer overrun here:
desc.magic[4]='S';
and an infinite loop (+buffer overrun) here:
for (i=0;0<=8;i++)
desc.name[i]=' ';

and a few signed/unsigned comparisons

otherwise the code should work

---

