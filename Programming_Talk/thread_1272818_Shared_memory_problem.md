---
title: "Shared memory problem"
date: 2009-09-22
forum: Programming Talk
---

### Post by bovus on 2009-09-22
I need to make a char** object in shared memory.  I am using the shmget function to get the id for the shared memory and shmat to get a pointer to the shared memory.  However, shmat returns a void*.  Is there anyway to get a double pointer in shared memory.  Or, is there anyway to convert a single pointer into a double pointer?

Program is being written in C

thanks

---

### Post by MadCow108 on 2009-09-22
you can allocate one block of shared memory for every string in the array and one block for the pointers to those blocks (just like the original char**)

*edit:* did a little reading on shmget and shmat, they seem like shared memory equivalents of malloc, so the above solution is probably what you want, just mimic how you would declare the char** with malloc with shmget and shmat and do normal copying
the rest of this post can probably be ignored

or you copy every element in the array behind each other into one block returned by shmat.
in that case you must take care of what your data consists.
If it for example does not contain null bytes you can just copy them all into memory and delimit every entry by a null byte.
if this is not the case and the data has variable size it gets more complicated. You would need to add data size indicators in front of every datablock to read it out of the memory correctly again.
Same sized entries would be easy again as you can use simple pointer arithmetics to calculate the element start and end in the memory block

here would be example when you have guaranteed null terminated strings.
its pretty bad but maybe gives you an idea how to do it
```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
int main (int argc, char *argv[])
{
	char * str1 = "string1";
	char * str2 = "stridfdfng2";
	char * str3 = "string3";
	char * data[3];
	data[0] = str1;
	data[1] = str2;
	data[2] = str3;
	char * mem=0;
	int size = strlen(str1)+strlen(str2)+strlen(str3)+3+1;
	{
		// write into memory, in your case no malloc but shmat
		mem = malloc(sizeof(char)*size);
		char * pos=mem;
		for (int i=0; i<3; i+=1)
		{
			memcpy(pos,data[i],strlen(data[i])+1);
			pos += strlen(data[i])+1;
		}
		mem[size-1] = 0;
		printf("written: %s %s %s\n",data[0],data[1],data[2]);
	}
	
	{
		//read data from memory
		char * readdata[3];
		char * data = mem;
		char * end=mem+size;
		int i=0;
		while (data < end && *data) {
			readdata[i] = data;
			data += strlen(readdata[i])+1;
			i++;
		}
		printf("read: %s %s %s\n",readdata[0],readdata[1],readdata[2]);
	}
	return 0;
}

```

---

