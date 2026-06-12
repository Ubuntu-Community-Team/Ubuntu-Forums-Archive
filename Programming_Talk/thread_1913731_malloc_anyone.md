---
title: "malloc anyone?"
date: 2012-01-23
forum: Programming Talk
---

### Post by conradin on 2012-01-23
Hi all,
Im trying to get a hnadle on malloc() but having some brian cramps over it. 
I want to stat a file, and assign the file size in a char type variable
My program runs ok, and compiles without error but doesn tell me what in assigned in the pointer ptr. I named this program 2args
```
$ ./2args helloWelt.c 
File size:                77 bytes
 allocated:

```

Source:
```
       #include <sys/types.h>
       #include <sys/stat.h>    //Allows for linux system Calls
       #include <stdlib.h>
       #include <fcntl.h>
       #include <stdio.h>
       #include <time.h>

//####StatFucntion taken from man 2 page
int main(int argc, char ** argv){
         struct stat sb;
        if (argc > 2 || argc == 1) {
            perror("Please include 1 and only 1 filename in the format:\n ./2args <filename> \n");
	        exit(EXIT_FAILURE);
	   }

           if (stat(argv[1], &sb) == -1) {
               perror("stat");
               exit(EXIT_FAILURE);
           }
//Show the file size:
           printf("File size:                %lld bytes\n",
                   (long long) sb.st_size);
		  

//assign memory with malloc
/* Allocate space for an array with elements of type
   char where char is assumed to be a byte. */
char *ptr = (char *) malloc(sb.st_size * sizeof (char));
if (ptr == NULL) {
	printf("memory could not be allocated:\n");
    /* Memory could not be allocated, the program should
       handle the error here as appropriate. */
} else {
    /* Allocation succeeded.  Do something.  */
    printf("%s allocated:\n", ptr);
    free(ptr);  /* We are done with the int objects, and
                   free the associated pointer. */
    ptr = NULL; /* The pointed-to-data  must not be used again,
                   unless re-assigned by using malloc
                   again. */
}

  //Open the file next:

FILE *fp; //File is a pointer to a file.
     if (( fp = fopen(argv[1],"r")) == NULL){
    	perror("Please Enter a valid filename");
        fp = fopen(argv[1], "a");
        //fprintf(fp, "%s\n ", "Hello World, Where there is will, there is a way.");
   exit(1);

  }

  fclose(fp) ; //put toys away

return 0;
}


```


What am I doing wrong? I just want to verify the blocks assigned to ptr via malloc()

---

### Post by Barrucadu on 2012-01-23
Your printf is wrong. It's %p to print out the address of a pointer.

---

### Post by Bachstelze on 2012-01-23
Also please watch your indentation. Your code is a pain to read.

---

### Post by trent.josephsen on 2012-01-23
I'll add:
- Don't cast the return value of malloc()
- Use EXIT_FAILURE and EXIT_SUCCESS consistently
- Be careful opening files.  Just because fopen() failed doesn't mean the file doesn't exist; it could also be a permissions issue or a dozen other things.  In any case, you certainly shouldn't assume you can write to a file if you can't read it.

---

