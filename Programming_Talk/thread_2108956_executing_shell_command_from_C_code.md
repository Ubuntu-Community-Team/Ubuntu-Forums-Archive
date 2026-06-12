---
title: "executing shell command from C code"
date: 2013-01-26
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-26
Hi,
To run a shell command from C, I normally use the system method.

1)Is there a better method(I've heard of execve, but never used it.
2)Is it possible to save the output of the shell command in a program variable inside the C code. Normally I write the output of the shell command to a file, and then read from the file using fopen. Works, but would be cool if there was an easier way.

```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
 system("ls > mylsout.txt");
 
 /* read from the file and store in a variable for processing by the program logic*/
}

```

Thanks.

PS : I am not lazy, just curious to know if there is an easier way :)

---

### Post by Sazhen86 on 2013-01-26
If you want to run a command and capture the output without using a temporary file, you can use the popen() function.  The man page for popen(3) should explain it pretty well.

The exec() family of calls will replace the current executable with the new one, which is probably not what you want to do.

---

### Post by IAMTubby on 2013-01-26
> **Sazhen86 said:**
> If you want to run a command and capture the output without using a temporary file, you can use the popen() function.  The man page for popen(3) should explain it pretty well.

Sazhen86, thanks a lot for letting me know about popen. I was taking some time to try out a few things and get back to you.

I)I went through the manual and wrote this sample code.
```

#include <stdio.h>
#include <stdlib.h>
#include <limits.h>

int main(void)
{
 FILE* fp;
 char* command;
 char* line;

 line = malloc(200 * sizeof(char));
 command = malloc(200 * sizeof(char));
 strcpy(command,"ls -l");

 fp = popen(command,"r");
 while((fgets(line, **need some help here**, fp)))
 {
  printf("\n[%s]",line);
 }

 return 0;
}

```
I have a couple of questions here
1)I understand that the second argument to fgets limits size, and I also understand why there is a need to limit size(otherwise people would overshoot the size and this may result in problems). But how do I make it read everything that ls outputs ? Is giving INT_MAX under <limits.h> the answer or is there another way ?

2)Since, we are running fgets in a while loop, that means, fgets reads line-by-line, but not in chunks of the size mentioned, correct ? Is there something which reads the entire chunk, without running in a while loop?
Okay we can do using [b]while((fgets(line, INT_MAX, fp)))
 {
  strcat(full,line);
 }
[/b]
but I was thinking if there is an option in fgets to read the entire buffer.

Please advise.
Thanks.

---

### Post by IAMTubby on 2013-01-26
> **Sazhen86 said:**
> 
The exec() family of calls will replace the current executable with the new one, which is probably not what you want to do.

Thanks a lot for letting me know of the exec family.I tried going through exec but I'm confused.I have a couple of questions here as well.
1)I couldn't understand why we need exec with so many arguments when we have system(" ");
2)I was finding the exec family syntax slightly confusing.
[b]int execl(const char *path, const char *arg, ...);
[/b]. I mean, say we are executing execl("/bin/ls", "ls", "-l",(char *) 0),
 a)firstly, why give path to executable, system doesn't require that.(**Is the answer that : system is meant only for system calls, but exec family can be used even for my own exectables**
 b)second, why mention the name of the executable as the second argument, when you are anyways giving the exact absolute path to the executable, why do you have to give the name of the executable as the second arg ?

Thanks.

---

### Post by Bachstelze on 2013-01-26
> **IAMTubby said:**
> 
2)Since, we are running fgets in a while loop, that means, fgets reads line-by-line, but not in chunks of the size mentioned, correct ? Is there something which reads the entire chunk, without running in a while loop?
Okay we can do using [b]while((fgets(line, INT_MAX, fp)))
 {
  strcat(full,line);
 }
[/b]
but I was thinking if there is an option in fgets to read the entire buffer.


The whole point of fgets() is that it reads line by line. If you want to read a chunk of data of a specified size, use fread().

> **IAMTubby said:**
> 
1)I couldn't understand why we need exec with so many arguments when we have system(" ");


system() spawns a new shell, which runs the specified command. How do you think the shell is able to run the command? By making another call to system()? ;)

---

### Post by IAMTubby on 2013-01-26
> **Bachstelze said:**
> The whole point of fgets() is that it reads line by line. If you want to read a chunk of data of a specified size, use fread().
Thanks Bachstelze, I tried re-writing a program using popen to get the output of ls command using fread instead of fgets. But because ftell returns -1 for the size of the file descriptor, it gives read error. Please check out the code(partly from google) and suggest me what I should change.
```

/* fread example: read an entire file */
#include <stdio.h>
#include <stdlib.h>

int main () {
  FILE * pFile;
  long lSize;
  char * buffer;
  size_t result;
  char* command;

  command = malloc(100 * sizeof(char));
  strcpy(command,"ls");

  pFile = popen ( command , "r" );
  if (pFile==NULL) {fputs ("File error",stderr); exit (1);}

  // obtain file size:
  fseek (pFile , 0 , SEEK_END);
  lSize = ftell (pFile);
  rewind (pFile);

  // allocate memory to contain the whole file:
  buffer = (char*) malloc (sizeof(char)*lSize);
  if (buffer == NULL) {fputs ("Memory error",stderr); exit (2);}

  // copy the file into the buffer:
  result = fread (buffer,1,lSize,pFile);
  if (result != lSize) {fputs ("Reading error",stderr); exit (3);}

  /* the whole file is now loaded in the memory buffer. */
  printf("\nbuffer == [%s]",buffer);

  // terminate
  pclose (pFile);
  free (buffer);
  return 0;
}

```

Thanks.
PS : Just to say it once again, my objective is to read the entire output of the ls command at once than using fgets and read it line-by-line.

---

### Post by IAMTubby on 2013-01-26
> **Bachstelze said:**
> system() spawns a new shell, which runs the specified command. How do you think the shell is able to run the command? By making another call to system()? ;)
Okay, thanks Bachstelze, you mean, system internally uses fork, exec and wait. I get it.
So as as end user who just want to execute shell commands within a C code, I don't have to use exec and would go with "system" which is the easier way, right ?

---

### Post by Bachstelze on 2013-01-26
What popen() gives you is not a "real" file, it is a pipe. Generally speaking, you have no way to know in advance how much data there is in it. You have to keep reading until you reach the end. This means in particular that you have no way to know in advance the "right" size for your buffer, you have to decide on an "initial" size and start reading. Then if you find that you have filled your buffer but there is still data to be read, you can for example use realloc() to make your buffer larger.

Yes, it is a lot of trouble. At this point you would do well to ask yourself whether you really need to do this in C.

---

### Post by IAMTubby on 2013-01-26
> **Bachstelze said:**
> What popen() gives you is not a "real" file, it is a pipe. Generally speaking, you have no way to know in advance how much data there is in it. You have to keep reading until you reach the end. This means in particular that you have no way to know in advance the "right" size for your buffer, you have to decide on an "initial" size and start reading. Then if you find that you have filled your buffer but there is still data to be read, you can for example use realloc() to make your buffer larger.

Yet, it is a lot of trouble. At this point you would do well to ask yourself whether you really need to do this in C.
Right Bachstelze, get the point. Thanks a lot.

---

