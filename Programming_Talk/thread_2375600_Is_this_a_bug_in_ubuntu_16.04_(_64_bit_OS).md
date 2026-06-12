---
title: "Is this a bug in ubuntu 16.04 ( 64 bit OS) ?"
date: 2017-10-25
forum: Programming Talk
---

### Post by mrj22 on 2017-10-25
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/wait.h>
#include <unistd.h>
#define BUF_ROWS 100
#define BUF_COLS 64
/*@
 * this demo code can run on ubuntu 14.04 (32bit & 64bit) and mac osx (64bit). 
 * But NOT on ubuntu 16.04 (64bit) as tested !
 */
#define dbg(...) fprintf(stderr,__VA_ARGS__)
void split_r(char* str, char* delim, char* toks[], size_t* sz)
{
    char* x, *sp;
    int i;
    x = strtok_r(str, delim, &sp);
    i = 0;
    while (x) {
        toks[i] = malloc(strlen(x)+1);
        strcpy(toks[i], x);
        i++;
        x = strtok_r(NULL, delim, &sp);
    }
    *sz = i;
}

int main(int argc, char** argv) {
    int gCnt, done =0;
    char ibuf[4096];

    char delim[] = " ";
    char* toks[8] = {NULL};
    size_t n;
    char** in;
    FILE* fp=fopen(argv[1],"r");   
   if(!fp) { fprintf(stderr,"open %s file err. \n",argv[1]); exit(1); }

    while(!done) {
        gCnt=0;
        in = malloc(BUF_ROWS * BUF_COLS * sizeof(char*) );
        while (gCnt < BUF_ROWS*BUF_COLS) {
            if(fgets(ibuf, 4096, fp)) {
                ibuf[strcspn(ibuf, "\n")] = '\0';
                in[gCnt]=malloc(strlen(ibuf)+1);
                strcpy(in[gCnt], ibuf);
                char tm[128];
                strcpy(tm, in[gCnt]);
                dbg("In:'%s'\n", tm);
                split_r(tm, delim, toks, &n);
                if( n != 4) {
                 fprintf(stderr,"Fatal:in parse line '%s' to split n=%ld.\n", tm, n), exit(1);
                }
                gCnt++;
            } else {
                done=1;
                break; 
           }

        }
        pid_t pid;
        if((pid=fork()) == 0) {
          // do sth 
          exit(0);
        }
       wait(NULL);
       for (int i=0; i<gCnt; i++)
          printf("%s\n",in[i]), fflush(0);
       for(int i=0; i< BUF_ROWS * BUF_COLS; i++) free(in[i]);
       free(in);
 } // end of done
}

```
The code above is removed error checking for brevity ! the input file each line has 4 strings only. this code only chokes on ubuntu 16.04 (64 bit os) at middle of the input file
 as I tested on various platforms. Could anybody help & verify it ? Thanks a lot !!!

---

### Post by TheFu on 2017-10-26
a) Wrong forum.  General help isn't for C programming.

b) if you want help, post a complete program AND data files that shows the problem.  Where's the void main()?

BTW, I'd initialize all variables, including pointers, to known values. This is a best practice for C programming.  More descriptive variables would be nice too.

---

### Post by slickymaster on 2017-10-26
*Thread moved to **Programming Talk**.*

---

