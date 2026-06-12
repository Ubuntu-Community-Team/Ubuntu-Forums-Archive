---
title: "[SOLVED] Make and Run Problems"
date: 2008-05-22
forum: Packaging and Compiling Programs
---

### Post by przemeklach on 2008-05-22
I'm new to Linux and even newer to programming in linux. 

For one of my classes in school I'm rquired to write a C program. At school they use Scientific Linux but I've decided that I want to code at home on my Ubuntu machine. I've written a bit of code at school and the program 'makes' and runs correctly on the school computer; however, it does not make or run on Ubuntu at home.


The MakeFile was given to me by my prof and looks as follows: 

PROJECT = MyShell
OBJS = MyShell.o

CC = /usr/bin/gcc

#compiler flags
CFLAGS = -Wall -g

#library flags 
LFLAGS = -lreadline -lhistory -ltermcap

$(PROJECT): $(OBJS)
        $(CC) $(CFLAGS)   -o $(PROJECT) $(OBJS) $(LFLAGS) 

clean: 
        rm -rf $(OBJS) $(PROJECT) 


The code that compiles, at school, looks as follows:

#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <readline/readline.h>
#include <readline/history.h>

int asArrayOfSubstrings(char *cmd, char **args){
  char cmdCopy[100];
  char* token = NULL;
  int argC = 0;

  if (strlen(cmd) == 0){
    return 0;
  }else{
    strcpy(cmdCopy, cmd);
    token = strtok(cmdCopy, " ");

    while(token){
      args[argC] = malloc(sizeof(char) * (strlen(token) + 1));
      strncpy(args[argC], token, (strlen(token) + 1));
      token = strtok(NULL, " ");
      argC++;
    }

    args[argC] = '\0';

    return argC;
  }
}

int main (void){
  char *cmdsAsArray[20];

  for(;;){
    char *cmd = readline("SHELL>");
    asArrayOfSubstrings(cmd, cmdsAsArray);

    if(strcmp(cmdsAsArray[0], "exit") == 0){
      exit (0);
    }

    if(strcmp(cmdsAsArray[0], "help") == 0){
      printf("Help me\n");
    }

  //execvp(*cmdsAsArray, cmdsAsArray);
  }
}


Here is the error message I get when I run 'make':

/usr/bin/gcc -Wall -g     -c -o MyShell.o MyShell.c
MyShell.c:5:31: error: readline/readline.h: No such file or directory
MyShell.c:6:30: error: readline/history.h: No such file or directory
MyShell.c: In function ‘main’:
MyShell.c:36: warning: implicit declaration of function ‘readline’
MyShell.c:36: warning: initialization makes pointer from integer without a cast
make: *** [MyShell.o] Error 1


Here is the error I get when I try to run by typing './MyShell':

bash: ./MyShell: cannot execute binary file

Now I'm assuming ./ fails cause the make fails. And the make fails because I haven't installed the proper libraries at home. Is that correct? If so what libraries do I need and how to I install them.

Thanks in advance.


ShAm

---

### Post by przemeklach on 2008-05-22
As I guessed I was missing a library. In order to run the mising library run "sudo apt-get install libreadline5-dev" in terminal. Running just "sudo apt-get install build-essential g++" will not work.

---

