---
title: "c piping program need help!!!"
date: 2008-12-15
forum: Programming Talk
---

### Post by adramalech on 2008-12-15
okay so for an assignment i have to be able to do redirection, piping, and background processing....and some dos commands that are going to be used but switched at runtime with unix commands that are equivalent...

i am having issues which i have highlighted red...

the two main errors i have and have found is that when i know it is a pipe i will pipe the command then fork it...at the end i make sure the file descriptors are closed but it doesn't like me when i do it at the end of the if statement but it is okay being right after i do the execute command....

what i mean is this....if i do this code it errors at the lines in red..

```


          pipe(file_des);
                        if(fork()==0){
                                close(file_des[1]);
                                dup2(file_des[0], 0);
                                execvp(argv[0], argv);
                        }//end if statement
                        if((new_cid = fork()) == 0){
                                close(file_des[0]);
                                dup2(file_des[1], 1);
                                execvp(argv[3], argv+3);
                        }//end if statement
                     [COLOR="Red"]   close(file_des[0]);
                        close(file_des[1]);[/COLOR]

```

if i do this code it doesn't error at all....this is when i switch the close statements...
```

          pipe(file_des);
                        if(fork()==0){
                                close(file_des[1]);
                                dup2(file_des[0], 0);
                                execvp(argv[0], argv);
                             [COLOR="Red"]   close(file_des[0]);[/COLOR]
                        }//end if statement
                        if((new_cid = fork()) == 0){
                                close(file_des[0]);
                                dup2(file_des[1], 1);
                                execvp(argv[3], argv+3);
                              [COLOR="Red"]  close(file_des[1]);[/COLOR]
                        }//end if statement

```

here is the full source code for the entire piping program...i found i have some small glitches in running it....it also doesn't like the line where 
dup2(file_des, 1); 
because it gives me a warning that i i am using a pointer  to an integer without a cast...this is in the redirection part...

```

#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <sys/file.h>
#include <sys/types.h>
#include <signal.h>

#define MAX_SIZE 80

int fg_id = 0, pid = 0, status = 0;

void sigchldHandler(){
        pid = wait(&status);
        if(pid == fg_id){
                fg_id = 0;
        }//end if statement
        signal(SIGCHLD, sigchldHandler);
}

int main(int argc, char *argvv[]){
        char *dosCmd[] = {"exit","dir","md","type","sort", "del", "copy", ">", ">>", "&"},
             *unixCmd[] = {"exit","ls","mkdir","cat","sort","rm", "cp", ">", ">>", "&"};

        int file_des[2], i, z, forgrnd, redir, reder,file_ptr, new_cid, args;
        char command[MAX_SIZE], *delimenator = " \n", *argv[10];
        signal(SIGCHLD, sigchldHandler);

        while(1){
                i = redir = reder = file_ptr = new_cid = 0; forgrnd = 1;

                printf("terminal@piping> ");
                gets(command);

                if(command[0]==0) continue;
                argv[i] = strtok(command, delimenator);
                args++;

                while(argv[i] != NULL){
                        for(z = 0; (z < 10) && (strcmp(argv[i], dosCmd[z])!= 0); z++);
                        switch(z){
                                case 0: return 0; break;
                                case 1:
                                case 2:
                                case 3:
                                case 4:
                                case 5:
                                case 6: argv[i] = unixCmd[z]; break;
                                case 7: reder++; argv[i] = NULL; break;
                                case 8: redir++; argv[i] = NULL; break;
                                case 9: forgrnd = 0; break;
                        }
                        argv[++i] = strtok(NULL, delimenator);
                        args++;
                }
                if(args > 2){
                        pipe(file_des);
                        if(fork()==0){
                                close(file_des[1]);
                                dup2(file_des[0], 0);
                                execvp(argv[0], argv);
                                close(file_des[0]);
                        }
                        if((new_cid = fork()) == 0){
                                close(file_des[0]);
                                dup2(file_des[1], 1);
                                execvp(argv[3], argv+3);
                                close(file_des[1]);
                        }
                        else{
                                if((new_cid = fork()) == 0){
                                        if(reder > 0){
                                              file_ptr= open(argv[z+1],O_WRONLY|O_CREAT|O_TRUNC, 0666);
                                        }
                                        if(redir > 0){
                                                file_ptr = open(argv[z+1], O_WRONLY|O_APPEND, 0666);
                                        }
                                        if(file_des){
                                         [COLOR="Red"]       dup2(file_des, 1);[/COLOR]
                                        }
                                        if((redir > 0)|| (reder > 0)){
                                                close(file_ptr);
                                        }
                                        execvp(argv[0], argv);
                                }
                        }
                }
                if(forgrnd){
                        fg_id = new_cid;
                        while(fg_id);
                }
        }
        return 0;
}


```

*****************EDIT******************

okay so i have done some debugging and found it is really difficult to keep track of things like where i am at in command char array....

i think there is also an issue with any redirection command also any background commands given...this code only will work for 1 pipe...between two different commands that are dos commands...

i decided that for redirection that i will put a NULL where i should have the > or >> in the array that way i know when to execute the redirection and to what file...but i seems that i am lacking something...

---

### Post by slavik on 2008-12-15
exec() doesn't return on success ...

---

### Post by adramalech on 2008-12-16
i am in the process of finishing up a better source code with error handling in it...

but besides that i don't know what else to do to make it work...because i am only allowed to have 10 strings...so 10 words surrounded by spaces....

i have found one problem to work with...

this is the command i write to my shell:

md files | dir

it will then error with:

files is already a directory
| is already a directory
dir is already a directory

which tells me the code is looping twice through because it would make the directories first time through then it would list the directories!!

the other thing is that it is making everything after the command md a directory thus the piping evaluation is wrong...and i am not opening the correct file

which leads me to believe that i should make a search algorthim where at a "|" or a ">" ">>" it will return the position of that plus 1...

or i could keep track by using the variable i which is the counter for tokenizing the string...

---

### Post by adramalech on 2008-12-16
also because i am testing this program for bugs and i am debugging and fixing stuff as i go...there are major issues with crashing the ssh client because of forking....and the process running infinity is there a way to keep this from happening because i am having to kill processes before i log off to keep me from crashing...

this is what i get when i relog from an infinite loops even after i press ^z!!

-bash: fork: Resource temporarily unavailable

i have to wait till the server refreshes for me to be able to relog

---

### Post by dwhitney67 on 2008-12-16
Did you ever test your program's logic prior to ever calling fork()??

I took a look at the code you posted, and it seemed a bit strange.  So I took some of it, placed it into a small program to debug it, and surely enough you do not store all of the information given at your prompt.

Here's the code I tested with:
[php]
#include <stdio.h>
#include <string.h>

int main()
{
  int   args = 0;
  char* argv[10];
  char* delimiter = " \n";

  while (1)
  {
    char command[80] = {0};

    printf("terminal@piping> ");
    fgets(command, sizeof(command), stdin);

    // this will never occur with an fgets()
    //if (command[0] == 0) continue;

    argv[args++] = strtok(command, delimiter);

    printf("argv[%d] = %s\n", args-1, argv[args-1]);

    // ...
  }

  return 0;
}
[/php]

I presume if one types in a shell command such as "dir foo", that the DOS command will be translated to a comparable *nix command.  Well, the second part of the string ("foo") is tossed away.  That does not seem right.

It seems to me that you should place the strtok() in a loop, so that you can save all of the tokens given on the command line.  Hypothetically you should only have to translate the first token, which is the command from DOS to *nix.

Btw, is this a homework assignment, or something that you are merely fiddling with??

-----  EDIT -----

I just noticed that you are indeed performing the strtok() in a loop.  It was buried in the command translation code.  I need to pay more attention next time.:tongue:

Anyhow, I copied your code, revamped it a bit, and I believe it is working now.  Btw, you will notice that I trimmed down the use of the fork() calls; now there is only one.

[php]
#include <stdio.h>
#include <string.h>
#include <stdbool.h>
#include <unistd.h>
#include <sys/wait.h>
#include <fcntl.h>
#include <assert.h>


int fg_id = 0;

void sigchldHandler(int sig)
{
  int status = 0;
  int pid = wait(&status);

  if (pid == fg_id)
  {
    fg_id = 0;
  }
}


int main()
{
  char* dosCmd[]  = {"exit", "dir", "md",    "type", "sort", "del", "copy", ">", ">>", "&"};
  char* unixCmd[] = {"exit", "ls",  "mkdir", "cat",  "sort", "rm",  "cp",   ">", ">>", "&"};

  signal(SIGCHLD, sigchldHandler);

  while (1)
  {
    int   args = 0;
    char* argv[10];
    char* delimiter = " \n";
    char  command[80] = {0};

    int redir = 0;
    int reder = 0;
    bool foreground = true;

    printf("terminal@piping> ");
    fgets(command, sizeof(command), stdin);

    if (command[0] == '\n') continue;

    // gather input tokens
    argv[args++] = strtok(command, delimiter);
    do
    {
      int z = 0;
      for(; (z < 10) && (strcmp(argv[args-1], dosCmd[z]) != 0); ++z);

      switch(z)
      {
        case 0: return 0; break;

        case 1:
        case 2:
        case 3:
        case 4:
        case 5:
        case 6: argv[args-1] = unixCmd[z]; break;

        case 7: reder = args-1;  argv[args-1] = NULL; break;
        case 8: redir = args-1;  argv[args-1] = NULL; break;
        case 9: foreground = false; argv[args-1] = NULL; break;
      }
    } while ((argv[args] = strtok(NULL, delimiter)) != NULL && (++args < 10));

    if (args > 0)
    {
      int file_des[2];
      int new_cid;

      pipe(file_des);

      if ((new_cid = fork()) == 0)
      {
        // child process
        usleep(10000);      // delay for parent to setup semaphore for foreground processes

        close(file_des[1]);
        assert(dup2(file_des[0], 0) != -1);

        int file_ptr = 0;

        if (reder)
        {
          file_ptr = open(argv[reder+1], O_WRONLY | O_CREAT | O_TRUNC, 0666);
        }
        else if (redir)
        {
          file_ptr = open(argv[redir+1], O_WRONLY | O_APPEND, 0666);
        }

        if (file_des[1]) dup2(file_des[1], 1);

        execvp(argv[0], argv);

        close(file_des[0]);

        if (file_ptr) close(file_ptr);
      }
      else if (foreground)
      {
        fg_id = new_cid;
        while(fg_id) usleep(10000);   // don't pound the CPU
      }
    }
  }

  return 0;
}
[/php]

---

### Post by adramalech on 2008-12-16
thanks i will definitely be using this....

but right now i am locked out of the stupid ssh client viewer because i have a process running that is using all my resources available to me!!!

gotta restart me...but when i can access the code then i will certainly use what help you have given me....

idk why he had us forking so much....we did 3 times...the first time i can see...

the second and third idk why he made us to that...it was the professor's framework and pseudo-code he gave me...to us..

---

### Post by dwhitney67 on 2008-12-16
The only thing you should be concerned about is what slavik pointed out earlier, and that is that execvp() will replace the child process, and it will not return (unless there is an error).  Thus under nominal situations, the lines following the execvp() will *not* be executed!

[php]
...

execvp(argv[0], argv);

close(file_des[0]);                // NOT executed!

if (file_ptr) close(file_ptr);     // NOT executed!
[/php]

You may want to consider declaring file_des and file_ptr as global variables and then using them within the signal handler.

[php]
int fg_id = 0;
int file_des[2];
int file_ptr = 0;


void sigchldHandler(int sig)
{
  int status = 0;
  int pid = wait(&status);

  if (pid == fg_id)
  {
    fg_id = 0;

    if (file_des[0]) close(file_des[0]);

    if (file_ptr) close(file_ptr);
  }
}

...

      if ((new_cid = fork()) == 0)
      {
        ...

        execvp(argv[0], argv);

        fprintf(stderr, "%s: command not found\n", argv[0]);
        exit(1);
      }
      ...
[/php]

---

### Post by adramalech on 2008-12-18
okay well i understand that if the execvp command is actually ran, that all the commands after it will not be ran...

but i still need to leave the close command of the side of the pipe used by the process because it will not compile if i put it outside of the evaluations...(what i mean is this):
if(args > 2){
      pipe(file_des);
      ......
      if(fork()==0){
      ....
      }
      if((new_cid = fork())==0){
      ....
      }

      close(file_des[0]);//this will error
      close(file_des[1]);//this will error
   .......

}

even if i don't close the side i don't use when i fork() either file_des[0] or file_des[1] it will still error when i close both after i do the evaluations and the execvp commands...

should i even bother then to close the other side of the pipe??? or will it cause even work problems???

---

### Post by dwhitney67 on 2008-12-18
What do you mean the close() statements won't work?  Do you mean it won't compile, or that it doesn't do as you expect?

I was able to use the close() statements in the signal handler.  See my previous post.

---

### Post by adramalech on 2008-12-18
won't compile....

but i have done some major fixing to the program because it was not piping correctly...

there is a huge problem though...i cannot seem to compile this either and all i did was add one element to both dosCmd pointer and unixCmd pointer!!!

made a variable for the pipe unix character...and switched evaluation from args > 2 to just the variable pipe!!

every line has an error and before it on the old version there wasn't a single compile error!!

```

#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <sys/file.h>
#include <sys/types.h>
#include <signal.h>
#define MAX_SIZE 80

int fg_id = 0, pid = 0, status = 0;

void sigchldHandler(){
        pid = wait(&status);
        if(pid == fg_id){
                fg_id = 0;
        }
        signal(SIGCHLD, sigchldHandler);
}

int main(int argc, char *argvv[]){
        char *dosCmd[] = {"exit","dir","md","type","sort", "del", "copy", ">", ">>", "&", "|"};
             *unixCmd[] = {"exit","ls","mkdir","cat","sort","rm", "cp", ">", ">>", "&", "|"};

        int file_des[2], i, z, forgrnd, redir, reder,file_ptr, new_cid, args, pipes;
        char command[MAX_SIZE], *delimenator = " \n", *argv[10];
        signal(SIGCHLD, sigchldHandler);

        while(1){
                i = redir = reder = file_ptr = new_cid = pipes = 0; forgrnd = 1;

                printf("\nterminal@piping> ");
                gets(command);

                if(command[0]==0) continue;
                argv[i] = strtok(command, delimenator);
                args++;

                while(argv[i] != NULL){
                        for(z = 0; (z < 10) && (strcmp(argv[i], dosCmd[z])!= 0); z++);
                        switch(z){
                                case 0: return 0; break;
                                case 1:
                                case 2:
                                case 3:
                                case 4:
                                case 5:
                                case 6: argv[i] = unixCmd[z]; break;
                                case 7: reder = i; argv[i] = NULL; break;
                                case 8: redir = i; argv[i] = NULL; break;
                                case 9: forgrnd = 0;argv[i] = NULL; break;
                                case 10: pipes = i; argv[i] = NULL; break;
                        }
                        argv[++i] = strtok(NULL, delimenator);
                        args++;
                }
                if(pipes){
                        pipe(file_des);
                        if(fork()==0){
                                close(file_des[1]);
                                dup2(file_des[0], 0);
                                execvp(argv[0], argv);
                                close(file_des[0]);
                        }
                        if((new_cid = fork()) == 0){
                                close(file_des[0]);
                                dup2(file_des[1], 1);
                                execvp(argv[pipes+1], argv + pipes);
                                close(file_des[1]);
                        }
                        else{
                                if((new_cid = fork()) == 0){
                                        if(reder > 0){
                                                file_ptr = open(argv[reder+1], O_WRONLY|O_CREAT|O_TRUNC, 0666);
                                        }
                                        if(redir > 0){
                                                file_ptr = open(argv[redir+1], O_WRONLY|O_APPEND, 0666);
                                        }
                                        if(file_ptr){
                                                dup2(file_ptr, 1);
                                        }
                                        execvp(argv[0], argv);
                                }
                        }
                }
                if(forgrnd){
                        fg_id = new_cid;
                        while(fg_id);
                }
        }
        return 0;
}

```

---

### Post by adramalech on 2008-12-18
nvm about it erroring on trying to compile fixed it just had a ; where i need a ,

---

