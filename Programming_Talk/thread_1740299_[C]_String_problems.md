---
title: "[C] String problems"
date: 2011-04-26
forum: Programming Talk
---

### Post by stlbhoy on 2011-04-26
Hi this is my second post, also related to the project I needed help on in my first post. I'm terrible with pointers (and C in general, but that's what this project has to be done in), so I've been trying to use character arrays. However I keep getting segmentation faults and I believe they are related to this.

Anyway here's a small program that takes a "Tuple" file, which would look like a longer version of this:

```

(ASSIGN,R5,M[FP+5])
(ASSIGN,R6,R5)
(ASSIGN,M[SP],R6)
(ADDI,SP,SP,1)
(SUBI,FP,SP,5)
(JUMP,1)
(LABEL,4)
(ASSIGN,SP,M[FP+2])
(ASSIGN,FP,M[FP+1])
(JUMP,M[FP])
(LABEL,1)
(ASSIGN,R7,M[FP+3])
(ASSIGN,R8,R7)

```The program should then make an array of basic blocks from the above code (basic block meaning anything that starts with LABEL and may or may not end with JUMP). Therefore I'm using an array of these structures:

```

struct BB{
  int BBid;
  char * code;
}

```Where the "char * code" is just the concatenation of all the lines of code between a LABEL and JUMP (inclusive) or between a LABEL and another LABEL.

I think the problem is when I try to do this concatenation but it could be elsewhere. Here is my main source file. Be gentle I don't use C very often :redface:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include "buffer.c"
#include "types.c"

#define MAXLINE 50
#define MAXBB 20

int main(int argc, char *argv[]){
    
    FILE *fp; // initialize file pointer
    if( argc != 2 ){ //check for argument
        printf("Error: Please put .tup file argument. Program exit...\n");
        exit(0);
    }
    if( ( fp = fopen( argv[1], "r" ) ) == NULL ){ //open file
        printf("Error: unable to open file %s. Program exit...\n", argv[1]);
        exit(0);
    }
    
    printf("no segfault -1");
    
    struct BB * BBarray[MAXBB]; // initialize array of basic blocks
    int currBBid = 0; // begin with basic block 0
    
    printf("no segfault 0");
    
    BBarray[currBBid]->code = "\0"; // initialize code in first basic block to be end of string
    
    char line[MAXLINE];
    
    int count;
    int length; // initialize variables for getting the line
    
    char flag = 'N';
    char c;
    
    while( (c=getch(fp)) != EOF ){
    
            printf("no segfault 1");
    
            for(count = 0; count < MAXLINE; count++){
                line[count] = '\0';
            }
    
            // get line
            line[0] = c;
            for(count = 1; (count < MAXLINE) && (((c=getch(fp)) != '\n') && (c != '\r')); count++){
                
                line[count] = c;
                
            }
            ungetch(c);
            line[count++] = '\n';
            line[count] = '\0';
            length = strlen(line);
            
            printf("no segfault2");
            
            /*
                put line in basic block code
                if JUMP, put line in code and increment to next BB
                if LABEL, increment (if fall through to label, not jump to label) then put line in code (unless already incremented because of jump shown by flag)
                else put line in code
            */
            if(strncmp(line, "(JUMP", 5) == 0){
            
                printf("no segfault 3");
                
                BBarray[currBBid]->BBid = currBBid; // redundant, oh well
                BBarray[currBBid]->code = (BBarray[currBBid]->code == "\0") ? line : strcat(BBarray[currBBid]->code, line); // check to make sure not concatinating to end of string 
                
                currBBid++; // new basic block
                BBarray[currBBid]->code = "\0"; // initialize new basic block
                
                flag = 'J'; // flag to show currBBid has already been incremented because a JUMP has been reached
                
            }else if(strncmp(line, "(LABEL", 5) == 0){
            
                printf("no segfault 4");
                
                if(flag != 'J'){ // fall through to label, new basic block
                    currBBid++;
                    BBarray[currBBid]->code = "\0";
                }
                
                BBarray[currBBid]->BBid = currBBid;
                BBarray[currBBid]->code = (BBarray[currBBid]->code == "\0") ? line : strcat(BBarray[currBBid]->code, line);
                
                flag = 'N'; // no flag after this change
            
            }else{
            
                printf("no segfault 5");
                
                BBarray[currBBid]->BBid = currBBid;
                BBarray[currBBid]->code = (BBarray[currBBid]->code == "\0") ? line : strcat(BBarray[currBBid]->code, line);
            
            }
                
    }
    
    printf("BBid\t\tCode");
    for(count=0; count <= currBBid; count++){
        printf("%d\t\t%s", BBarray[count]->BBid, BBarray[count]->code);
    }
    
    return 0;
}

```buffer.c contains getch and ungetch, and those printf's scattered through the code are to check where the segfault is. Thus far none of them are even reached.

Any help would be greatly appreciated. Thanks!

---

### Post by NovaAesa on 2011-04-26
There's an easy way to find out where seg faults are occurring. Recompile with the -g flag then run
```
gdb program_name
```
then type
```
run
```
If everything went okay, it should show you where the segfault occurred.

---

### Post by stlbhoy on 2011-04-26
Hey thanks for the reply. I did run it with gdb and it was giving me unhelpful answers as to where the segfaults were coming from, like:

```

Program received signal SIGSEGV, Segmentation fault.
0x0000003c4320cd22 in _dl_fixup () from /lib64/ld-linux-x86-64.so.2

```

Anyway, I've since tried several different things and at least now it is giving me reasonable issues. I learned that my include files were causing a problem, since I had them declared as ".c" so I just copied and pasted them into my main file to save time.

Here is an updated look at my code.
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define BUFSIZE 1000
#define MAXLINE 50
#define MAXBB 20
#define MAXDATA 100

char buf[BUFSIZE];
int bufp = 0;

int getch(FILE *fp){
    return (bufp > 0) ? buf[--bufp] : getc(fp);
}

void ungetch(int c){
    if (bufp >= BUFSIZE)
        printf("Error: ungetch buffer overflow\n");
    else
        buf[bufp++] = c;
}

struct BB{
    int BBid;
    char code[MAXDATA];
};


int main(int argc, char *argv[]){
    
    //printf("no segfault -2");
    
    FILE *fp = NULL;
    if( argc != 2){ // check for argument
        printf("Error: Please use at least one file argument. Program Exit...\n");
        exit(0);
    }
    
    if( (fp = fopen(argv[1], "r")) == NULL ){ // try to open file
        printf("Error: Unable to open file %s. Program Exit...\n", *argv);
        exit(0);
    }
    
    struct BB * BBarray[MAXBB]; // initialize array of basic blocks
    int currBBid = 0; // begin with basic block 0
    int codePt = 0;
    
    // initialize EVERYTHING!!!
    int i, j;
    for (i = 0; i < MAXBB; i++){
        for (j = 0; j < MAXDATA; j++){
            BBarray[i]->code[j] = '\0';
        }
        BBarray[i]->BBid = -1;
    }
    
    char line[MAXLINE];
    // initialize line
    for(i=0; i<MAXLINE; i++){
        line[i] = '\0';
    }
    
    int linePt = 0;
    
    int count;
    int length; // initialize variables for getting the line
    
    char flag = 'N';
    char c;
    
    while( (c=getch(fp)) != EOF ){
    
            // get line
            line[0] = c;
            for(count = 1; (count < MAXLINE) && (((c=getch(fp)) != '\n') && (c != '\r')); count++){
                
                line[count] = c;
                
            }
            ungetch(c);
            line[count++] = '\n';
            line[count] = '\0';
            length = strlen(line);
                        
            /*
                put line in basic block code
                if JUMP, put line in code and increment to next BB
                if LABEL, increment (if fall through to label, not jump to label) then put line in code (unless already incremented because of jump shown by flag)
                else put line in code
            */
            if(strncmp(line, "(JUMP", 5) == 0){
                
                BBarray[currBBid]->BBid = currBBid; // redundant, oh well
                
                linePt = 0;
                while(linePt < length){
                    BBarray[currBBid]->code[codePt++] = line[linePt++];
                }

                BBarray[currBBid]->code[codePt++] = '\n';
                
                currBBid++; // new basic block
                codePt = 0; // initialize new basic block
                
                flag = 'J'; // flag to show currBBid has already been incremented because a JUMP has been reached
                
            }else if(strncmp(line, "(LABEL", 5) == 0){
                
                if(flag != 'J'){ // fall through to label, new basic block
                    currBBid++;
                    codePt = 0;
                }
                
                BBarray[currBBid]->BBid = currBBid;
                
                linePt = 0;
                while(linePt < length){
                    BBarray[currBBid]->code[codePt++] = line[linePt++];
                }
                
                BBarray[currBBid]->code[codePt++] = '\n';
                
                flag = 'N'; // no flag after this change
            
            }else{
                
                BBarray[currBBid]->BBid = currBBid;
                
                linePt = 0;
                while(linePt < length){
                    BBarray[currBBid]->code[codePt++] = line[linePt++];
                }
            
            }
                
    }
    
    printf("BBid\t\tCode");
    for(count=0; count <= currBBid; count++){
        printf("%d\t\t%s", BBarray[count]->BBid, BBarray[count]->code);
    }
    
    return 0;
}


```

GDB is telling me I have a segfault issue at these lines:
```


    // initialize EVERYTHING!!!
    int i, j;
    for (i = 0; i < MAXBB; i++){
        for (j = 0; j < MAXDATA; j++){
            BBarray[i]->code[j] = '\0';
        }
        BBarray[i]->BBid = -1;
    }


```

Specifically, the line "BBarray[i]->code[j] = '\0';"

Is there some way this is going out of the bounds of the array?

---

### Post by Arndt on 2011-04-27
> **stlbhoy said:**
> Hey thanks for the reply. I did run it with gdb and it was giving me unhelpful answers as to where the segfaults were coming from, like:

```

Program received signal SIGSEGV, Segmentation fault.
0x0000003c4320cd22 in _dl_fixup () from /lib64/ld-linux-x86-64.so.2

```

Anyway, I've since tried several different things and at least now it is giving me reasonable issues. I learned that my include files were causing a problem, since I had them declared as ".c" so I just copied and pasted them into my main file to save time.

Here is an updated look at my code.
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define BUFSIZE 1000
#define MAXLINE 50
#define MAXBB 20
#define MAXDATA 100

char buf[BUFSIZE];
int bufp = 0;

int getch(FILE *fp){
    return (bufp > 0) ? buf[--bufp] : getc(fp);
}

void ungetch(int c){
    if (bufp >= BUFSIZE)
        printf("Error: ungetch buffer overflow\n");
    else
        buf[bufp++] = c;
}

struct BB{
    int BBid;
    char code[MAXDATA];
};


int main(int argc, char *argv[]){
    
    //printf("no segfault -2");
    
    FILE *fp = NULL;
    if( argc != 2){ // check for argument
        printf("Error: Please use at least one file argument. Program Exit...\n");
        exit(0);
    }
    
    if( (fp = fopen(argv[1], "r")) == NULL ){ // try to open file
        printf("Error: Unable to open file %s. Program Exit...\n", *argv);
        exit(0);
    }
    
    struct BB * BBarray[MAXBB]; // initialize array of basic blocks
    int currBBid = 0; // begin with basic block 0
    int codePt = 0;
    
    // initialize EVERYTHING!!!
    int i, j;
    for (i = 0; i < MAXBB; i++){
        for (j = 0; j < MAXDATA; j++){
            BBarray[i]->code[j] = '\0';
        }
        BBarray[i]->BBid = -1;
    }
    
    char line[MAXLINE];
    // initialize line
    for(i=0; i<MAXLINE; i++){
        line[i] = '\0';
    }
    
    int linePt = 0;
    
    int count;
    int length; // initialize variables for getting the line
    
    char flag = 'N';
    char c;
    
    while( (c=getch(fp)) != EOF ){
    
            // get line
            line[0] = c;
            for(count = 1; (count < MAXLINE) && (((c=getch(fp)) != '\n') && (c != '\r')); count++){
                
                line[count] = c;
                
            }
            ungetch(c);
            line[count++] = '\n';
            line[count] = '\0';
            length = strlen(line);
                        
            /*
                put line in basic block code
                if JUMP, put line in code and increment to next BB
                if LABEL, increment (if fall through to label, not jump to label) then put line in code (unless already incremented because of jump shown by flag)
                else put line in code
            */
            if(strncmp(line, "(JUMP", 5) == 0){
                
                BBarray[currBBid]->BBid = currBBid; // redundant, oh well
                
                linePt = 0;
                while(linePt < length){
                    BBarray[currBBid]->code[codePt++] = line[linePt++];
                }

                BBarray[currBBid]->code[codePt++] = '\n';
                
                currBBid++; // new basic block
                codePt = 0; // initialize new basic block
                
                flag = 'J'; // flag to show currBBid has already been incremented because a JUMP has been reached
                
            }else if(strncmp(line, "(LABEL", 5) == 0){
                
                if(flag != 'J'){ // fall through to label, new basic block
                    currBBid++;
                    codePt = 0;
                }
                
                BBarray[currBBid]->BBid = currBBid;
                
                linePt = 0;
                while(linePt < length){
                    BBarray[currBBid]->code[codePt++] = line[linePt++];
                }
                
                BBarray[currBBid]->code[codePt++] = '\n';
                
                flag = 'N'; // no flag after this change
            
            }else{
                
                BBarray[currBBid]->BBid = currBBid;
                
                linePt = 0;
                while(linePt < length){
                    BBarray[currBBid]->code[codePt++] = line[linePt++];
                }
            
            }
                
    }
    
    printf("BBid\t\tCode");
    for(count=0; count <= currBBid; count++){
        printf("%d\t\t%s", BBarray[count]->BBid, BBarray[count]->code);
    }
    
    return 0;
}


```

GDB is telling me I have a segfault issue at these lines:
```


    // initialize EVERYTHING!!!
    int i, j;
    for (i = 0; i < MAXBB; i++){
        for (j = 0; j < MAXDATA; j++){
            BBarray[i]->code[j] = '\0';
        }
        BBarray[i]->BBid = -1;
    }


```

Specifically, the line "BBarray[i]->code[j] = '\0';"

Is there some way this is going out of the bounds of the array?

You don't seem to set BBarray[i] to anything. You need to allocate space for the nodes.

---

### Post by BkkBonanza on 2011-04-27
You have declared an array of "struct BB *". This is an array of pointers not an array of structs. The thing you need to remember about pointers is that they are just addresses. When you have a pointer you have the address of the thing not the thing itself.

So when you go thru the loop you are looping thru arrays of addresses and at this point the addresses point at "nowhere in particular". You don't have actual structs to initialize yet. If you want to store pointers then you need to use "new" to create the actual structs. Otherwise declare actual structs not pointers to structs.

I think you are going about this the wrong way with an array and should be using a list method. Put a self referencing pointer inside your BB and then chain them together as a list. You are processing them in order anyway. Each time before you add a BB, you dynamically create it and link it into the list.
eg.

```

typedef struct _BB {
   int BBid;
   char code[MAXDATA];
   struct _BB *next;
} BB;


...
BB *head = malloc(sizeof(BB));
BB *now = head;

each time you read in a line and need to add a new BB you 
use code like this in a loop reading/parsing each line,


...copy string into code, init as desired
now->next = malloc(sizeof(BB));
now = next;

```
This method works better for input of unknown and unlimited length and doesn't preallocate a large array. Read up on lists as this above is just very rough.

BTW for gdb to give you useful info you need to look at the stack to see where your code called the std library, where it seg faulted. You may have already figured that out though.

Edit: fixed for C malloc not C++ new op.

More detail...
```

// array of tokens to scan for, can add as needed
char *tokens[] = { "JUMP", "LABEL" };

char buf[128];
BB *phead = NULL, *pnow;

// to fill list
while(fgets(buf, sizeof(buf), fp) != NULL) {
    for(int BBid = 0; n < sizeof(tokens); BBid++)
        if(!strncmp(buf, tokens[BBid], strlen(tokens[BBid])) {
            insertBB(BBid);
            break;
            }
    pnow->code = realloc(pnow->code, pnow->code ? strlen(pnow->code) : 0) + strlen(buf)+2);
    strcat(pnow->code, buf);
    }

// to print list
pnow = phead;
while(pnow != NULL) {
    printf("%d\t\t%s", pnow->BBid, pnow->code);
    pnow = pnow->next;
    }
}


void insertBB(int id)
{
    BB *ptmp = malloc(sizeofBB));
    ptmp->code = NULL;
    ptmp->next = NULL;
    if(phead == NULL)
        phead = ptmp;
    else
        pnow->next = ptmp;
    pnow = ptmp;
    pnow->BBid = id;
}

```
Again, this is a very rough sketch as I haven't made any attempt to compile and debug this. It's more a roadmap than final code.

---

