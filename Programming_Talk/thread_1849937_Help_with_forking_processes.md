---
title: "Help with forking processes"
date: 2011-09-25
forum: Programming Talk
---

### Post by Lubert on 2011-09-25
I am writing a program that emulates a shell. I am supposed to be able  to background processes or run them in the foreground. I looked up some  examples like [this]("http://www.gnu.org/software/libc/manual/html_node/Process-Creation-Example.html"), however my program is freezing up when my parent process is (supposedly) waiting for the child. It always gets to the line
```
if(waitpid(pid, &status, 0) != pid)
```and just hangs there. I end up having to kill the program with CTRL + C.  As a side note, can anybody explain to me how to background a process  and how to wait for all of my child processes to be finished before the  program exits on command?

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include "parse.h"

int main(void){
    int repeat = 1;
    char args[MAX_ARGS][CMD_LEN];

    while(repeat){
        fprintf(stdout, ":~$ ");
        
        Param_t *params = new_paramt();
        if(params == NULL){
            fprintf(stdout, "Memory allocation failed");
            exit(1);
        }

        init_args(args);
        char command[CMD_LEN];
        fgets(command, CMD_LEN, stdin);        
        format_args(command, params, args);

        if(!strcmp(params->program, EXIT)){
            repeat = 0;
        }
        else{
            pid_t pid;
            int status;

            pid = fork();
            if(pid == 0){
                if(params->outputRedirect){
                    FILE *fout = freopen(params->outputRedirect, "w", stdout);
                    if(!(fout)){
                        fprintf(stdout, "Error! Output redirection failed.");
                    }
                }
                if(params->inputRedirect){
                    FILE *fin = freopen(params->outputRedirect, "r", stdin);
                    if(!(fin)){
                        fprintf(stdout, "Error! Input redirection failed.");
                    }
                }
                execvp(params->program, params->argumentVector);
            }
            else if(pid < 0){
                fprintf(stdout, "Error! Process fork failed.");
                status = -1;
            }
            else{
                if(waitpid(pid, &status, 0) != pid){
                    status = -1;
                }
                return status;
            }
        }
        free_param_t(params);
    }
    return 0;
}
```

---

### Post by Arndt on 2011-09-25
> **Lubert said:**
> I am writing a program that emulates a shell. I am supposed to be able  to background processes or run them in the foreground. I looked up some  examples like [this]("http://www.gnu.org/software/libc/manual/html_node/Process-Creation-Example.html"), however my program is freezing up when my parent process is (supposedly) waiting for the child. It always gets to the line
```
if(waitpid(pid, &status, 0) != pid)
```and just hangs there. I end up having to kill the program with CTRL + C.  As a side note, can anybody explain to me how to background a process  and how to wait for all of my child processes to be finished before the  program exits on command?

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include "parse.h"

int main(void){
    int repeat = 1;
    char args[MAX_ARGS][CMD_LEN];

    while(repeat){
        fprintf(stdout, ":~$ ");
        
        Param_t *params = new_paramt();
        if(params == NULL){
            fprintf(stdout, "Memory allocation failed");
            exit(1);
        }

        init_args(args);
        char command[CMD_LEN];
        fgets(command, CMD_LEN, stdin);        
        format_args(command, params, args);

        if(!strcmp(params->program, EXIT)){
            repeat = 0;
        }
        else{
            pid_t pid;
            int status;

            pid = fork();
            if(pid == 0){
                if(params->outputRedirect){
                    FILE *fout = freopen(params->outputRedirect, "w", stdout);
                    if(!(fout)){
                        fprintf(stdout, "Error! Output redirection failed.");
                    }
                }
                if(params->inputRedirect){
                    FILE *fin = freopen(params->outputRedirect, "r", stdin);
                    if(!(fin)){
                        fprintf(stdout, "Error! Input redirection failed.");
                    }
                }
                execvp(params->program, params->argumentVector);
            }
            else if(pid < 0){
                fprintf(stdout, "Error! Process fork failed.");
                status = -1;
            }
            else{
                if(waitpid(pid, &status, 0) != pid){
                    status = -1;
                }
                return status;
            }
        }
        free_param_t(params);
    }
    return 0;
}
```

When you say it hangs there, do you mean it should not hang there, in other words, the child process in fact exits at some time?

---

### Post by Lubert on 2011-09-25
> **Arndt said:**
> When you say it hangs there, do you mean it should not hang there, in other words, the child process in fact exits at some time?

To the best of my knowledge it shouldn't be hanging there....right? When I use gdb, the situation is such that the first process being executed is the parent process, once it gets to waitpid() the program just... waits..then nothing else happens and then I have to kill it.

---

### Post by Arndt on 2011-09-26
> **Lubert said:**
> To the best of my knowledge it shouldn't be hanging there....right? When I use gdb, the situation is such that the first process being executed is the parent process, once it gets to waitpid() the program just... waits..then nothing else happens and then I have to kill it.

And the child process? Does it start? Does it do what it should, and does it exit? Until it exits, the parent process should hang in waitpid.

Maybe WNOHANG is what you want. See the manual page for waitpid.

---

