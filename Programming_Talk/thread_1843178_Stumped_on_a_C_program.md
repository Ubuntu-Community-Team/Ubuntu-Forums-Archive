---
title: "Stumped on a C program"
date: 2011-09-13
forum: Programming Talk
---

### Post by Lubert on 2011-09-13
I have a program that takes input, formats it, and prints it out. When I use some input the program works fine. However, when I input something like ">I hope this a b c d" I get a seg fault. This seems to always happen when i = 6.
```
Program received signal SIGSEGV, Segmentation fault.
0x000000000040100d in format_args (command=0x7fffffffda70 ">hello I hope a b c d", params=0x603010) at parse_ops.c:72
72                    args[i][x++] = *token;
(gdb) print i
$1 = 6

``` Any thoughts?

```
#ifndef _main_h
#define _main_h

/* don’t test program with more than this many tokens for input */
#define MAXARGS 32
#define EXIT "exit"
#define CMD_LEN 2048

/* structure to hold input data */
struct PARAM{
    char *inputRedirect;                        /* file name or NULL */
    char *outputRedirect;                        /* file name or NULL */
    int background;                                                    /* either 0 (false) or 1 (true) */
    int argumentCount;                                            /* same as argc in main() */
    char *argumentVector[MAXARGS];    /* array of strings */
};

/* a typedef so we don’t need to use "struct PARAM" all the time */
typedef struct PARAM Param_t;

//
//    @breif                This function takes a string, tokenizes each word, removes any trailing '\n'
//                                characters, and inserts them into the 2D array args. The argument count
//                                is changed in params inside this funciton as well.
//    @param                command is a string of input read from the user. command cannot be NULL.
//    @param                args is a 2D array that holds the tokens from command. args cannot be NULL.
//    @param                params is a Param_t struct. params must have memory allocated to it
//                                already and cannot be NULL. 
//    @return                A pointer to the 2D array args is returned.
//
char **format_args(char command[CMD_LEN], Param_t *params);

//
//    @brief                This function allocates memory for a new Param_t struct
//                                and initializes the items.
//    @param                There are no parameters.
//    @return                A pointer to the new Param_t struct is returned.
//
Param_t *new_paramt(void);

//
//    @brief                This function prints all arguments in the argumentVector array
//                                and prints every other item of the struct to stdout.
//    @param                param is a Param_t struct. It must have memory allocated to it.
//    @return                Nothing is returned.
//
void printParams(Param_t *param);

#endif
``````

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "parse.h"

Param_t *new_paramt(void){
    Param_t *new_paramt = (Param_t *) malloc(sizeof(Param_t));
    new_paramt->inputRedirect = NULL;
    new_paramt->outputRedirect = NULL;
    new_paramt->argumentCount = 0;
    new_paramt->background = 0;
    new_paramt->inputRedirect = (char *) malloc(sizeof(char) * CMD_LEN);
    new_paramt->outputRedirect = (char *) malloc(sizeof(char) * CMD_LEN);    
    int x;
    for(x = 0; x < MAXARGS; x++)
        new_paramt->argumentVector[x] = (char *) malloc(sizeof(char) * CMD_LEN);
    return ((new_paramt != NULL) ? new_paramt:NULL); 
}

void printParams(Param_t *param){
    int i;
    printf ("InputRedirect: [%s]\n", (param->inputRedirect != NULL) ? param->inputRedirect:"NULL");
    printf ("OutputRedirect: [%s]\n", (param->outputRedirect != NULL) ? param->outputRedirect:"NULL");
    printf ("Background: [%d]\n", param->background);
    printf ("ArgumentCount: [%d]\n", param->argumentCount);
    for (i = 0; i < param->argumentCount; i++)
        printf("ArgumentVector[%2d]: [%s]\n", i, param->argumentVector[i]);
}

char **format_args(char command[CMD_LEN], Param_t *params){    
    int x = 0;
    char **args;
    args = (char **) malloc(sizeof(char) * MAXARGS);
    for(x = 0; x < MAXARGS; x++)
        args[x] = (char *) malloc(sizeof(char) * CMD_LEN);    


int len = strlen(command);
    char result[CMD_LEN];

    if(command[len-1] == '\n')
        command[len-1] = '\0';

    strcpy(result, command);
    char *token = (char *) malloc(sizeof(char) * CMD_LEN);

    x = 0;
    if((token = strtok(result, " "))){
        while(*token){
            args[0][x++] = *token;
            token++;
        }
        args[0][x] = '\0';
    }
    else
        args[0][0] = '\0';
    
    int arg_count = 0, i = 1;
        while((token = strtok(NULL, " ")) && i < MAXARGS){
            x = 0;
            arg_count++;
            while(*token){
                args[i][x++] = *token;
                token++;
            }
        args[i++][x] = '\0';
        }
    params->argumentCount = arg_count;

    return args;
}
``````

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "parse.h"

int main(void){
    int repeat = 1, x = 0;
    system("clear");

    Param_t *params = new_paramt();
    if(params == NULL){
        fprintf(stdout, "Memory allocation failed");
        exit(1);
    }

    while(repeat){
        fprintf(stdout, ":~$ ");
        
        char command[CMD_LEN];
        fgets(command, CMD_LEN, stdin);        

        char **args = format_args(command, params);
        int arg_count = params->argumentCount;
        params->argumentCount = 0;

        if(!strcmp(args[0], EXIT))
            repeat = 0;
        else{
            for(x = 0; x <= arg_count; x++){
                if(args[x][0] == '>'){
                    char temp[CMD_LEN];
                    int y = 1, z = 0;
                    while(args[x][y] != '\0')
                        temp[z++] = args[x][y++];
                    temp[z] = '\0';
                    strcpy(params->outputRedirect, temp);                    
                }
                else if(args[x][0] == '<'){
                    char temp[CMD_LEN];
                    int y = 1, z = 0;
                    while(args[x][y] != '\0')
                        temp[z++] = args[x][y++];
                    temp[z] = '\0';
                    strcpy(params->inputRedirect, temp);
                }
                else if(args[x][0] == '&'){
                    params->background = 1;
                }
                else{
                    if(args[x][0] != '\0'){
                        strcpy(params->argumentVector[params->argumentCount], args[x]);
                         params->argumentCount += 1;
                    }
                }
            }
        }
        printParams(params);
        
    }
    
    return 0;
}
```

---

### Post by Bachstelze on 2011-09-13
```
    char **args;
    args = (char **) malloc(sizeof(char) * MAXARGS);
```

Probably not what you want. ;)

---

### Post by Senesence on 2011-09-13
@ Bachstelze

Man, you're fast.

@ Lubert

Yea, the fact that you're allocating space for chars instead of space for char pointers is probably the culprit here.

When you declare char** args, you're declaring pointer to pointer to char.

---

### Post by Lubert on 2011-09-13
I was not seeing that at all yesterday. You know how those late nights programming get :shock:...Anyways, I changed that malloc and everything seems fine now. Thanks to both of you.

---

