---
title: "read file into array?"
date: 2012-02-01
forum: Programming Talk
---

### Post by conradin on 2012-02-01
hi all, 
Im trying to read a file into an array after its been assigned a memory location. but Im getting confuses about how to do that. I have a memory location named ptr, that I hope is the same size as the file being read in, but I have no idea what to do to get the data into the memory allocation. I would appreciate any help I can get. 
I tried 

```

#include <sys/types.h>   //Specified in man 2 open
#include <sys/stat.h>    //Allows for linux system Calls
#include <stdlib.h>
#include <unistd.h>      //Specified in man 2 read
#include <errno.h>  	 //Allows use of error numbers
#include <fcntl.h>       //Specified in man 2 open
#include <stdio.h>


//StatFucntion taken from man 2 page
int main(int argc, char * argv[]){ 
    struct stat sb; 
    if (argc > 2 || argc == 1) { 
		perror("Please include 1 and only 1 filename in the format:\n .<program> <filename> \n");
		printf("errno = %d.\n", errno); //give error number
        exit(EXIT_FAILURE);             //Reads Success on exit??
	    } 

    if (stat(argv[1], &sb) == -1) {  
        perror("stat Error"); 
        printf("errno = %d.\n", errno);
        exit(EXIT_FAILURE); 
		}
  	//Show filesize: long long used because its the type used by stat.
    printf("File size: %lld bytes\n",(long long) sb.st_size); 
     
    //assign memory with malloc: char used because it is 1 byte.
	char *ptr = (char *) malloc(sb.st_size * sizeof (char)); 
	 
	if (ptr == NULL) {
		perror("memory could not be allocated:\n");
		printf("errno = %d.\n", errno);
		exit(EXIT_FAILURE);		
  	}
  	else {        
	//Open the file next:
	int fp; //File open syntax:(<path> <readonly arg>)
    if ((fp = open(argv[1],O_RDONLY))==-1){ 
		perror("Open Crashed");
		printf("errno = %d.\n", errno);
		exit(EXIT_FAILURE); 
       	}
	else {
			
		do  { 
			
			int n = 0;
			for (k=0; k < 255; k++){
				
			}
////////////////////////////////////////////////////////////////////////
/////////////////////Not Sure what to put here//////////////////////////////
//////////////////////////////////////////////////////////////////////////			
			
			
			printf("%s Stuff:", ptr);
			}while((read(fp,ptr,4096)!=0));
	
	}
	
 
  	close(fp);  /* Close the file */
  	free(ptr);  /* Free the memory allocated in malloc */ 
  	ptr = NULL; /* The pointed-to-data  must not be used again,*/
    }        	 /*unless re-assigned by using malloc again. */ 
	return 0;   //Program ended successfully.
}
```

---

### Post by dwhitney67 on 2012-02-01
open(), close(), read(), etc are great for low-level I/O, however for your case, I would recommend using fopen(), fclose, fread(), etc.

Thus something like this would probably work for you:
```

    ...
	//Open the file next:
	FILE* fp = fopen(argv[1], "r");

        if (fp == null)
        { 
	    perror("Open failed");
	    printf("errno = %d.\n", errno);
	    exit(EXIT_FAILURE); 
       	}

        // Read data from the file
        size_t result = fread(ptr, 1, sb.st_size, fp);

        if (result != sb.st_size)
        {
            // error reading file
        }
    ...

```

By the way, if your file contains text, which presumably should be stored in a buffer containing a terminating null-character, then you should augment the number of bytes you allocate by 1.
```

char *ptr = malloc(sb.st_size + 1);

```

---

