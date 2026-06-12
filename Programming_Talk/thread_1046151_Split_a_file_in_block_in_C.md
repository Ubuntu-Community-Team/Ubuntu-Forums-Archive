---
title: "Split a file in block in C"
date: 2009-01-21
forum: Programming Talk
---

### Post by C4nc3l on 2009-01-21
Hi, i have created a function to split a file in 10kb blocks with fread and fwrite.
If i try to use it with a txt file it works, but if i try to use it with a binary file the file isn't the same (for example if i try to split and unsplit a pdf file the unsplitted file is unreadable add diff says that the two file differ).
Where's the problem? or where i can find another way to split a file in C?

---

### Post by eye208 on 2009-01-21
> **C4nc3l said:**
> Where's the problem?
That's hard to tell without taking a look at your program.

---

### Post by mdurham on 2009-01-21
It sounds like you are reading/writing the files in text mode, you must use binary mode.
Cheers, Mike

---

### Post by bruce89 on 2009-01-21
> **mdurham said:**
> It sounds like you are reading/writing the files in text mode, you must use binary mode.
Cheers, Mike

It does, but I was under the impression it makes no difference in UNIX.

---

### Post by mdurham on 2009-01-21
> **bruce89 said:**
> It does, but I was under the impression it makes no difference in UNIX.
It does make a difference, as you have discovered!
Cheers, Mike

---

### Post by C4nc3l on 2009-01-21
> **mdurham said:**
> It sounds like you are reading/writing the files in text mode, you must use binary mode.
Cheers, Mike

Sorry, i didn't want to busy you with my code it's about 100 lines of idiot comments and prints :) 
How can i use binary mode?
I read/write with fread/fwrite and i use a buffer of unsigned char... i was thinking there's a bynary mode reading/writing too but i didn't found anything...
Ok and now... that's the code, this function split a file in block of 10kb...there are many lines that can be deleted, but i was going crazy with this problem so i've tried all things pass on my head :P  
```
void esplodi(char *name){
	FILE* fp;
	FILE* fw;
	int len=filelen(name);
	int num_blocchi=len/10240;
	int byte_scritti=0;
	int byte_letti=0;
	fp=fopen(name, "r");
	if (fp==NULL){
		printf("Errore nell'apertura del file %s", name);
		return;
	}
	printf("File lungo %dB. Saranno creati %d blocchi di file da 10240 byte e un file da %d byte",len,num_blocchi, len%10240);
	unsigned char buffer[10240];
	int n;
	int i=0;
	char nomeblockfile[BUFSIZ];
	char num[10];
	for(i=0; i< num_blocchi; i++){
		memset(buffer,'\0',10240);
		n =fread(buffer, sizeof(char), 10240, fp);
		buffer[10240]='\000';
		byte_letti+=n;
		printf("\nletti %dB ", strlen(buffer));
		if (n==0) {
			printf("\nFine file inaspettata");
			break;
		}
		if (strlen(buffer)==0){
			printf("buffer vuoto");
			continue;
		}
		sprintf(num, "%d", i+1);
		strcpy(nomeblockfile, "");
		strcat(nomeblockfile, name);
		strcat(nomeblockfile, ".");
		strcat(nomeblockfile,num);
		printf("trying to print file block in %s",nomeblockfile);
		fw=fopen(nomeblockfile, "w");
		if (fw==NULL){
			printf("errore nella creazione del file");
			break;
		}
		buffer[10240]='\000';
		n=fwrite(buffer, sizeof(char), strlen(buffer), fw);
		byte_scritti+=((n!=1)?strlen(buffer):0);
		printf(" scritti %d", ((n!=1)?strlen(buffer):0));
		fclose(fw);
		//do the explosion
	}
	if (n!=0){
		memset(buffer,'\0',10240);
		byte_letti+=fread(buffer, sizeof(char), len%10240, fp);
		sprintf(num, "%d", i+1);
		strcpy(nomeblockfile, name);
		strcat(nomeblockfile, ".");
		strcat(nomeblockfile,num);
		printf("\nletti %d ", strlen(buffer));
		printf("trying to print file block  %s", nomeblockfile);
		fw=fopen(nomeblockfile, "w");
		n=(fwrite(buffer, sizeof(char), strlen(buffer), fw));
		byte_scritti+=((n!=1)?strlen(buffer):0);
		printf(" scritti %dB", ((n!=1)?strlen(buffer):0));
	}
	printf("\nFINE ESPLODI: byte_scritti: %d \t byte_letti:%d", byte_scritti, byte_letti);
	fclose(fw);
	fclose(fp);
}
```

---

### Post by s|fr on 2009-01-21
like mdurham said. you need to read the file in binary mode if its binary:
like so:

```

fp=fopen(name, "rb")

```

note the b. check the C docs for other forms/flags and usage.

---

### Post by stroyan on 2009-01-21
You assign to buffer[10240], but the highest allocated index is buffer[10239].
You use "strlen(buffer) in multiple places to determine how much was read.
But binary files often have '0' characters in them.  You can't stop at the
first '0' character as strlen does.

---

### Post by WitchCraft on 2009-01-21
> **stroyan said:**
> You assign to buffer[10240], but the highest allocated index is buffer[10239].
You use "strlen(buffer) in multiple places to determine how much was read.
But binary files often have '0' characters in them. You can't stop at the
first '0' character as strlen does.
 
 
> **WitchCraft said:**
> If you need to get the size of a file, then it's best to use The C standard library:
```

#include <stdio.h>
#include <stdlib.h>
 
     FILE *ain=fopen("d:\\BigExample.txt","rb");
     fseek( ain,0,SEEK_END);
     long size=ftell(ain);
     fseek(ain,0,SEEK_SET);
 
     char* buffer=(char*)malloc(size);
     size_t count0=fread(buffer,1,size,ain);

```
 
The C++ standard library:
```

#include <iostream>
#include <cstdlib>
 istrLogFile.seekg (0, std::ios::end);   // Set the position of the get pointer
 uiFileSize = istrLogFile.tellg ();     //  Tell/Get the position of the get pointer.
 istrLogFile.seekg (0, std::ios::beg); //   Set the position of the get pointer

```
 
The other way is to use POSIX API's:
```

    FILE* intFileDescriptor ;
    struct stat stat_FileStatistics ;
 
    intFileDescriptor = fopen(path, "r") ;
    fstat(fileno(intFileDescriptor), &stat_FileStatistics) ;
    unsigned long size = stat_FileStatistics.st_size ;

```
 
 
The other way is to use POSIX API's
 
```

    FILE* intFileDescriptor ;
    struct stat stat_FileStatistics ;
 
    intFileDescriptor = fopen(path, "r") ;
    fstat(fileno(intFileDescriptor), &stat_FileStatistics) ;
    unsigned long size = stat_FileStatistics.st_size ;

```

---

### Post by C4nc3l on 2009-01-22
> **WitchCraft said:**
> If you need to get the size of a file, then it's best to use the C standard library:
```

#include <iostream>
#include <cstdlib>

     FILE *ain=fopen("d:\\BigExample.txt","rb");
     fseek( ain,0,SEEK_END);
     long size=ftell(ain);
     fseek(ain,0,SEEK_SET);

     char* buffer=(char*)malloc(size);
     size_t count0=fread(buffer,1,size,ain);

```the other way is to use POSIX API's

```

    FILE* intFileDescriptor ;
    struct stat stat_FileStatistics ;

    intFileDescriptor = fopen(path, "r") ;
    fstat(fileno(intFileDescriptor), &stat_FileStatistics) ;
    unsigned long size = stat_FileStatistics.st_size ;

```

Thanks to all, when i read with strlen(buf) to get the number of bytes read i only want to get a statistic control on the bytes read..., it's not to retrieve the size of the file, these line of code can be helpful for another problem i have thanks :)

---

### Post by mdurham on 2009-01-22
> **C4nc3l said:**
> Thanks to all, when i read with strlen(buf) to get the number of bytes read i only want to get a statistic control on the bytes read..., it's not to retrieve the size of the file, these line of code can be helpful for another problem i have thanks :)
'strlen()' can **only** be used on strings of chars, not binary data, the result would be meaningless. Consider if the first byte was zero 00h strlen() would return zero (0) no matter how many bytes were read into the buffer.

---

