---
title: "C conditional fork() problem"
date: 2010-08-22
forum: Programming Talk
---

### Post by smmalmansoori on 2010-08-22
I was recently introduced to programming in C using multiple processes.

These are the conditions of the program I am making:

[LIST=1]
[*]If "exit" is entered quit the program
[*]Process arbitrary commands as shell commands by using execl()
[*]Implement your own "cd" (change directory) command
[*]If commands are passed normally make a fork() and let the parent wait for it using wait()
[*]If commands are appended by "&" (i.e. "ls &")don't let the parent wait, and avoid zombie processes by using "signal(SIGCHLD, SIG_IGN)"
[/LIST]
I'm halfway through implementing my "cd" command so I did some testing and found out when running the program everything works except when using the "cd" command without appending "&" (i.e. "cd /tmp") it would output fine but then the program won't quit if I type "exit" after that.

Any advice or explanation is greatly appreciated. here is my code:
[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/wait.h>
#include <signal.h>

char *getLine(FILE *in);
int my_system(char *line);
void my_cd(char *line);

int main(int argv, char *args[])
{
  char *exitLine = "exit\n";
  int status = EXIT_SUCCESS;

  for(;;)
    {
      char *line = getLine(stdin);

      if(strcmp(line, exitLine) == 0)
    {
      break;
    }
      status = my_system(line);
    }
  return status;
}

char *getLine(FILE *in)
{
  int c = 0;
  unsigned long i = 0;
  size_t line_size = 80;
  char *line = malloc(line_size);

  if(ferror(in) == 0)
    {
      while(line != NULL && c != EOF)
    {
      while(i < line_size - 1)
        {
          if((c = getc(in)) == EOF)
        {
          break;
        }
      
          line[i++] = c;
      
          if(c == '\n' || c == '\0')
        {
          c = EOF;
          break;
        }
        }
      
      if(i >= line_size - i)
        {
          line_size *= 2;
          line = realloc(line, line_size);
        }
    }

        if(line != NULL)
      {
        line[i] = '\0';
      }
    }
  else
    {
      free(line);
      exit(EXIT_FAILURE);
    }

  

  return line;
}

int my_system(char *line)
{
  int status;
  int size;
  
  if(line == NULL)
    {
      perror("Line is NULL");
      status =  EXIT_FAILURE;
    }
  else
    {
      size = strlen(line);
      if(line[size-2] == '&')
    {
      signal(SIGCHLD, SIG_IGN);
      line[size-3] = '\0';
    }
      else
    {
      line[size-1] = '\0';
    }
      pid_t pid = fork();
      switch(pid)
    {
    case -1:
      perror("fork failed");
      status = EXIT_FAILURE;
      break;
    case 0:
      if( (line[0] == 'c') && (line[1] == 'd') )
        {
          my_cd(line);
        }
      else
        {
          execl("/bin/sh", "sh", "-c", line, NULL);
        }
      break;
    default:
      if(line[size-2] != '&')
        {
          wait(&status);
        }
    }
    }
  return status;
}

void my_cd(char *line)
{
  char *dirPath;
  char *delim = " ";

  dirPath = strtok(line, delim);
  dirPath = strtok(NULL, delim);
  
  printf("dirPath is: %s", dirPath);
}[/PHP]

---

### Post by splicerr on 2010-08-22
Your implementation of the cd command forks of a new instance of your program which after running the my_cd function will do exactly the same as the first instance, while the first instance is waiting for the second to finish. Typing exit 2 times will terminate both instances.

You'll probably don't want to fork the cd command.

---

### Post by smmalmansoori on 2010-08-22
Could you please explain to me why is this happening? what am I missing here?

EDIT:
I assign the my_cd() function to the child so why does it happen twice? and why is it that when I append an "&" this doesn't happen?

---

### Post by dwhitney67 on 2010-08-22
If I may weigh in...

First of all, replace getLine() with fgets(); there's no reason to reinvent the wheel.  Use a comfortably sized buffer to store whatever the user may enter (say 1024 bytes).

```

char* cmd = malloc(1024);

while (fgets(cmd, 1024, stdin))
{
   // replace the newline character with a null
   char* nl = strchr(cmd, '\n');
   if (nl)
   {
      *nl = '\0';
   }

   // trim leading and trailing white-space from the 'cmd'
   // TODO:  Left as an exercise.

   if (strcmp(cmd, exitLine) == 0) break;

   my_system(cmd);
}

```

Now as for my_system(), two things stick out... one, you are not initializing the 'status' variable, and two, you are not setting it to anything once (and this is if), the child is forked.

The other thing you should avoid is using signal(); this function has been deprecated.  Use sigaction() instead.

---

### Post by smmalmansoori on 2010-08-22
Thanks for pointing out fgets()  it's certainly much better than doing the whole getLine() function.

> you are not setting it to anything once (and this is if), the child is forked

How am I not setting it once? this is the exact dilemma that I can't understand, why is it run twice?

---

### Post by splicerr on 2010-08-22
> **smmalmansoori said:**
> Could you please explain to me why is this happening? what am I missing here?

EDIT:
I assign the my_cd() function to the child so why does it happen twice?


You don't assign a function to a child. What's happening is that when you issue the cd command the my_cd function is called and when that returns the execution continues after the function call just like normal. If you don't want that add an _exit() call right after my_cd(). But again forking of a process just to change directories is useless and probably not what you want.

---

### Post by dwhitney67 on 2010-08-22
When you attempt to perform a 'cd' (change directory), the child process does not exit.  After calling your my_cd(), the program returns to normal processing back in the main-loop of the main() function.

The call to execl() never returns (unless a failure occurred).  Thus the child process implicitly terminates at that point.

IMO, forget the fork().  How about using popen()?
```

#include <string.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <stdio.h>

int my_system(const char* cmd);
int my_cd(const char* cmd);

int main()
{
   const char* exitLine = "exit";

   char* cmd = malloc(1024);

   for (;;)
   {
      fprintf(stdout, "\n$ ");

      if (!fgets(cmd, 1024, stdin)) break;

      // replace the newline character with a null
      char* nl = strchr(cmd, '\n');
      if (nl)
      {
         *nl = '\0';
      }

      // trim leading and trailing white-space from the 'cmd'
      // TODO:  Left as an exercise.

      if (strcmp(cmd, exitLine) == 0) break;

      int status = my_system(cmd);

      if (status != 0) fprintf(stderr, "command failed.\n");
   }

   free(cmd);
   return 0;
}

int my_system(const char* cmd)
{
   int status = EXIT_FAILURE;

   if (strncmp(cmd, "cd ", 3) == 0)
   {
      status = my_cd(cmd);
   }
   else
   {
      FILE* fd = popen(cmd, "r");

      if (fd)
      {
         char result[1024];

         while (fgets(result, sizeof(result), fd))
         {
            fprintf(stdout, "%s", result);
         }

         pclose(fd);

         status = EXIT_SUCCESS;
      }
   }

   return status;
}

int my_cd(const char* cmd)
{
   const char  space = ' ';
   const char* path  = strchr(cmd, space);

   int status = EXIT_FAILURE;

   if (path)
   {
      status = chdir(++path);
   }

   return status;
}

```

---

### Post by smmalmansoori on 2010-08-22
Took me a while to wrap my hand around it but now I get it, thanks for your patience and answers :)

---

