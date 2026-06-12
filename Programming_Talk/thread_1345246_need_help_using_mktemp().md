---
title: "need help using mktemp()"
date: 2009-12-03
forum: Programming Talk
---

### Post by BlackSwordD2 on 2009-12-03
doing a lab in C and i can't seem to get my temp file to open heres the code segment in question

```

        char *path, name[10];
	FILE *fpntr;
	
	snprintf(name, 10, "lab5XXXXXX");
	path = mktemp(name);
	if((fpntr = fopen(path, "a")) == NULL)
	{
		perror("Error while opening file");
		return(EXIT_FAILURE);
	}

```

---

### Post by johnl on 2009-12-04
The problem is that your 'name' is getting truncated by one 'X' since you pass 10 as the size to snprintf.  This size doesn't include the null terminator, so the last 'X' is overwritten by a null.

Declare name with 11 elements instead, and pass sizeof(name) as the argument to snprintf:

```

        char *path, name[11];
	FILE *fpntr;
	
	snprintf(name, sizeof(name), "lab5XXXXXX");
	path = mktemp(name);
	if((fpntr = fopen(path, "a")) == NULL)
	{
		perror("Error while opening file");
		return(EXIT_FAILURE);
	}

```

---

### Post by BlackSwordD2 on 2009-12-04
so though i made the changes to the code, i still cant find the desired temp file... so for sake of time ill link all of my code thus far

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <signal.h>

int main(int argc, char** argv)
{	
	char *path, name[1];
	FILE *fpntr;
	
	snprintf(name, sizeof(name), "lab5XXXXXX");
	printf("hey");
	path = mktemp(name);
	if((fpntr = fopen(path, "a")) == NULL)
	{
		perror("Error while opening file");
		return(EXIT_FAILURE);
	}
	
	struct sigaction act;
	//act.sa_handler = writer;
	sigemptyset(&act.sa_mask);
	act.sa_flags = SA_RESTART;
	
	// Run the other program in a subprocess
	if(fork() > 0)
	{
	      char *line = NULL;
	      
	      // Initilally prompts user to enter a line of text
	      printf("Please Enter Line: ");
	      fflush(stdout);
	      fgets(line, 200, stdin);
	      
	      while(strncmp(line, "quit", 4) != 0)
	      {
		    // write each entered line of text to a temporary file
		    fprintf(fpntr, "%s\n", line);
		    
		    // signals the child
		    sigaction(SIGUSR1,&act, NULL); // When signal SIGUSR1 is sent, it is intercepted and restarted
		    
		    // Iteratively prompt the user to enter a line of text until "quit"
		    printf("Please Enter Line: ");
		    fflush(stdout);
		    fgets(line, 200, stdin);
	      }
	}
	else
	  printf("Child Code");
	
	return EXIT_SUCCESS;
}

```

---

### Post by dwhitney67 on 2009-12-04
Look at your declaration for the variable 'name'.  Should that not be declared as 11-bytes, not 1... right?

Or just declare the damn thing to be 255 bytes.  I believe that is the largest filename length supported under Linux.

P.S.  What is the point of the fork()???

P.S. #2  This line of code will crap out...
```

fgets(line, 200, stdin);

```

---

### Post by BlackSwordD2 on 2009-12-04
> **dwhitney67 said:**
> Look at your declaration for the variable 'name'.  Should that not be declared as 11-bytes, not 1... right?

Or just declare the damn thing to be 255 bytes.  I believe that is the largest filename length supported under Linux.

P.S.  What is the point of the fork()???

P.S. #2  This line of code will crap out...
```

fgets(line, 200, stdin);

```

yes, thats my mistake in copying over, it is 11 not 1

---

### Post by Arndt on 2009-12-05
> **BlackSwordD2 said:**
> yes, thats my mistake in copying over, it is 11 not 1

Did you copy by hand?

Go through it step by step with a debugger, or insert print statements.

---

### Post by BlackSwordD2 on 2009-12-05
> **Arndt said:**
> Did you copy by hand?

Go through it step by step with a debugger, or insert print statements.

nah just a lot of wrtiting and unwriting, the result is copying and pasting something i hadn't finished typing yet

---

