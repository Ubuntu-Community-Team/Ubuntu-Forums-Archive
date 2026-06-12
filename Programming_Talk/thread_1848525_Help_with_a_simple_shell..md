---
title: "Help with a simple shell."
date: 2011-09-22
forum: Programming Talk
---

### Post by lLuxe on 2011-09-22
Well I have a simple shell that is receiving a segmentation fault.  I believe that it is something to do with the pointers that I used in main().  I would like to get a little help debugging because Ive sat here looking things up trying to find out what is wrong but I cant seem to figure this out. (If there is a better way to post this let me know)

Thanks for your time,
Cody
------------------------------------------------------------------------------Code Below---------------------------------
```

/* shell.c
 * This program is a simple shell which illustrates how fork and execvp are
 * used to execute a program entered on the command line.  The simple shell
 * displays a prompt where you enter the command, the comamnd you enter is
 * separated into tokens or "parsed", and then executed as a child of the
 * simple shell process.  If the command line ends with a & character, the
 * simple shell process, which is the parent process, resumes execution
 * and executes concurrently with the child process.  If the command line does
 * NOT end with a & character, the parent process waits until the child process
 * finishes, and then the parent process resumes execution.
*/
#include <stdio.h>
#include <unistd.h>
#include <errno.h>
#include <stdlib.h>

#define MAX_LINE 80    // 80 chars per line, per command 

/**
 * The setup function below will not return any value, but 
 * setup() reads in the next command line, separating or "parsing" it into 
 * distinct tokens using whitespace as delimiters. setup() sets 
 * the args parameter as a  null-terminated, C-style string.
 */

void setup(char inputBuffer[], char *args[],int *background)
{
  int length; // # of characters in the command line 
  int i;      // loop index for accessing inputBuffer array 
  int start;  // index where beginning of next command parameter is 
  int ct = 0;     // index of where to place the next parameter into args[] 
  for (i=0; i<length; i++)    // blank out the input buffer
   *(inputBuffer + i) = ' ';
 
/* read what the user enters on the command line */
length = read(STDIN_FILENO, inputBuffer, MAX_LINE);  

/* 0 is the system predefined file descriptor for stdin (standard input),
   which is the user's screen in this case. inputBuffer by itself is the
   same as &inputBuffer[0], i.e. the starting address of where to store
   the command that is read, and length holds the number of characters
   read in. inputBuffer is not a null terminated C-string. */

start = -1;
if (length == 0) {
    exit(0);     // ^d was entered, end of user command stream 
    }
if (length < 0) {
    perror("error reading the command");
    exit(-1);     // terminate with error code of -1 
    }

/* examine every character in the inputBuffer */
for (i=0; i<length; i++) { 
    switch (inputBuffer[i]) {
     case ' ':
     case '\t' :               // argument separators 
              if(start != -1) {
                   args[ct] = &inputBuffer[start]; // set up pointer
           ct++;
           }
              inputBuffer[i] = '\0'; // add a null char; 
                                       // to make a C string 
              start = -1;
              break;

         case '\n':         // should be the final char examined 
              if (start != -1) {
                   args[ct] = &inputBuffer[start];     
           ct++;
           }
              inputBuffer[i] = '\0';
              args[ct] = NULL; // no more arguments to this command
              break;

     default :             // some other character 
              if (start == -1)
           start = i;
              if (inputBuffer[i] == '&') {
           *background  = 1;
                   inputBuffer[i] = '\0';
                   }  // end if
     }   // end switch 
    }  // end for    
    args[ct] = NULL; // just in case the input line was > 80 
}  // end setup() 

int main(void)
{
char inputBuffer[MAX_LINE]; // buffer to hold the command entered
int background;         // equals 1 if a command is followed by '&'
char *args[MAX_LINE/+1];// command line has max of 40 arguments 
int pid;                // return code from fork()    

while (1) { // endless while, program terminates normally inside setup
     background = 0;
     printf(" COMMAND->\n");
     setup(inputBuffer,args,&background);    // get next command 
     pid = fork();
      if(pid <0){ /*error occurred */
    printf("Fork Failed");
    return 1;
      }
      else if(pid == 0){/*child process*/
    execvp(args[0], args);
      }
      else{
    if(background==0){
      wait(NULL);
      printf("child complete\n");
    }

      }
      

     /* the steps to modify main() are:
       (1) fork a child process using fork()
       (2) the child process will invoke execvp()
       (3) if background == 0, the parent will wait, 
        otherwise returns to the setup() function. */
    }  // end while
}

```



SOLVED THANKS FOR THE HELP EVERYONE!!!

---

### Post by sisco311 on 2011-09-22
Is this your homework?

---

### Post by Simian Man on 2011-09-22
Use a debugger.

---

### Post by lLuxe on 2011-09-22
> **Simian Man said:**
> Use a debugger.
whats a good debugger to use to find a segmentation fault that has to be something with my pointers?
I was using gedit to create the code.

---

### Post by Bachstelze on 2011-09-22
```
  int length; // # of characters in the command line 
  for (i=0; i<length; i++)    // blank out the input buffer
   *(inputBuffer + i) = ' ';
```

You use length without initializing it. There should be no need to "blank out" the buffer. Use fgets() to read instead of read().

---

### Post by karlson on 2011-09-22
> **lLuxe said:**
> whats a good debugger to use to find a segmentation fault that has to be something with my pointers?
I was using gedit to create the code.

1.  compile with -Wall enabled and assume that all warnings are actually errors.
2.  Read your code after you wrote it.  Don't underestimate the power of the second look
3.  If all else fails use gdb, valgrind, callgrind, gprof...

---

### Post by lLuxe on 2011-09-24
Thank you guys for the tips... Im still stuck but Ive tried a couple of them and I think Im getting closer.

Thanks,
Cody

---

