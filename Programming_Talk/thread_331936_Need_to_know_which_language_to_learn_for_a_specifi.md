---
title: "Need to know which language to learn for a specific project"
date: 2007-01-05
forum: Programming Talk
---

### Post by oasmar on 2007-01-05
Hello, i have used Ubuntu for a month now and i want to make a simple (i think) program for a game. I want it to kinda be like this:

[LOOK HERE]("http://img232.imageshack.us/my.php?image=loaderprogramdh9.png")

Basically has two text inputs and an "ok" button.
I want it to compile the following script using the information the user has input and run it:

[COLOR="SeaGreen"]#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <sys/ptrace.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <asm/ptrace.h>
#include <errno.h>


#define AD_START 0x851f000 //0x855d000
#define AD_HOST_FIRST 0x15d8c0 //0x15d540
#define NUM_HOST 5
#define HOST_SEP 0x70
#define HOST_TO_PORT_SEP 0x64
#define HOST_MAX_SIZE 0x40

#define AD_RSAKEY 0x45efe0 //0x4638c0

const char rsakey[]=
"10912013296739942927886096050899"
"55415282375029027981291234687579"
"37266291492576446330739696001110"
"60390723088861007265581882535850"
"34290575928276294364131085660290"
"93628212635953836686562675849720"
"62078627943109021801768106152175"
"50567108238764764442605581471797"
"07119674283982419152118103759076"
"030616683978566631413";


//#define _DUMP

int main(int argc, char *argv[]) {

    char host[HOST_MAX_SIZE]="[/COLOR][COLOR="Red"]PUT IP HERE[/COLOR][COLOR="SeaGreen"]";
    long port=[/COLOR][COLOR="Red"]PORT[/COLOR][COLOR="SeaGreen"];
    char path[256]="./Tibia";

#ifdef _DUMP
    unsigned long d_start = AD_START;
    long d_size = 4;
    if(argc > 2) d_size = atol(argv[2]);
    if(argc > 1) d_start = strtoul(argv[1], NULL, 0);
#else
    if(argc > 3) strcpy(path, argv[3]);
    if(argc > 2) port = atol(argv[2]);
    if(argc > 1) strcpy(host, argv[1]);
#endif

    int fdin, fdout;
    fdin = open(path, O_RDONLY);
    if(-1 == fdin) {
        fprintf(stderr, "Failed to open %s.\n", path);
        return 1;
    }
    strcat(path, ".ot");
    fdout = open(path, O_WRONLY | O_CREAT | O_TRUNC, 0700);
    if(-1 == fdout) {
        fprintf(stderr, "Failed to open or create %s.\n", path);
        close(fdin);
        return 1;
    }
    
    char buf[8192];
    int n;
    while(n = read(fdin, buf, 8192)) {
        if(-1 == n) {
            fprintf(stderr, "Error in read.\n", path);
            close(fdin);
            close(fdout);
            return 1;
        }
        if(-1 == write(fdout, buf, n)) {
            fprintf(stderr, "Error in write.\n", path);
            close(fdin);
            close(fdout);
            return 1;
        }
    }
    
    if(-1 == lseek(fdout, AD_RSAKEY, SEEK_SET)) {
        fprintf(stderr, "Error in lseek.\n", path);
        close(fdin);
        close(fdout);
        return 1;
    }
    if(-1 == write(fdout, rsakey, sizeof(rsakey))) {
        fprintf(stderr, "Error in write(2).\n", path);
        close(fdin);
        close(fdout);
        return 1;
    }
    
    close(fdin);
    close(fdout);
    
    
    int pid;
    int wait_val;
    switch (pid = fork()) {
        case -1:
            perror("fork");
            break;
        case 0:
            if(-1 == ptrace(PTRACE_TRACEME, 0, NULL, NULL) && errno) {
                perror("ptrace(1)");
                return 1;
            }
            if(-1 == execl(path, path, NULL)) {
                perror("execl");
                return 1;
            }
            break;
        default:
            if(-1 == wait(&wait_val)) {
                perror("wait(1)");
                return 1;
            }
            
            int i,j;
            long pos;
            long *plong;
            int counter=0;
            while (!WIFEXITED(wait_val)) {
                counter++;
                if(counter == 2) {
                    
#ifdef _DUMP
                    printf("Dumping from 0x%x to 0x%x (%lu KB).\n", d_start, d_start + (d_size*1024), d_size);
                    FILE *fp;
                    long data;
                    fp = fopen("dump.txt", "w+b");
                    if(!fp) {
                        fprintf(stderr, "Failed to open or create dump.txt.\n");
                        return 1;
                    }
                    for(i=0; i<(d_size*1024); i+=4) {
                        data = ptrace(PTRACE_PEEKDATA, pid, d_start + i, NULL);
                        if(-1 == data && errno) {
                            perror("ptrace(2)");
                            fclose(fp);
                            return 1;
                        }
                        if(!fwrite(&data, sizeof(long), 1, fp)) {
                            fprintf(stderr, "fwrite failed.\n");
                            fclose(fp);
                            return 1;
                        }
                    }
                    fclose(fp);
#else
                    pos = AD_START + AD_HOST_FIRST;
                    
                    for(j=0; j<NUM_HOST; j++) {
                        plong = (long *) host;
                        for(i=0; i<HOST_MAX_SIZE; i+=4) {
                            if(-1 == ptrace(PTRACE_POKEDATA, pid, pos+i+(j*HOST_SEP), *(plong+i/4)) && errno) {
                                perror("ptrace(3)");
                                return 1;
                            }
                        }
                        if(-1 == ptrace(PTRACE_POKEDATA, pid, pos+HOST_TO_PORT_SEP+(j*HOST_SEP), port) && errno) {
                            perror("ptrace(4)");
                            return 1;
                        }
                    }
#endif
					if(-1 == kill(pid, SIGALRM)) {
						perror("kill SIGALRM");
						return 1;
					}
                	if(-1 == ptrace(PTRACE_DETACH, pid, NULL, NULL) && errno) {
                    	perror("ptrace(5)");
                    	return 1;
                	}
                	return 0;
                }
                
                if(-1 == ptrace(PTRACE_CONT, pid, NULL, NULL) && errno) {
                    perror("ptrace(6)");
                    return 1;
                }
                if(-1 == wait(&wait_val)) {
                    perror("wait(2)");
                    return 1;
                }
            }
    }
    return 0;
}
[/COLOR]

Any help/guidance would be great!

---

### Post by pmasiar on 2007-01-05
web-based game? GUI on desktop? Linux only?

---

### Post by oasmar on 2007-01-05
Ive got the script done i just need to make the prgram which compiles the file with the users IP and PORT then runs. The script works fine because u can compile it with the terminal g++ command and put it in the game directory then run it, but i want to make a program which does that for you.

---

### Post by Engnome on 2007-01-05
You should try and get those parameters from the command line instead. So that when a user starts he uses ./filename -ip -portnumber. (port number should be standard unless specified.)

Compiling the script every time is not a good idea.

---

### Post by oasmar on 2007-01-05
Thanks, Im Very new to prgramming, Ive only just learnt PHP (barely :P) so ill need help like which language to use, programs to use, ways of implementing my idea. I would like guides, help and ure own opinions on how to make my program.

---

### Post by slavik on 2007-01-05
look up 'command line options in C' in google, that should give you some insight, also if you can, get the C Programming Language book by Kerninghan and Ritchie (reffered to as the K&R book): [http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/sr=8-1/qid=1168013893/ref=pd_bbs_1/102-5119516-8340140?ie=UTF8&s=books](http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628/sr=8-1/qid=1168013893/ref=pd_bbs_1/102-5119516-8340140?ie=UTF8&s=books)

---

### Post by pmasiar on 2007-01-05
> **oasmar said:**
> Thanks, Im Very new to prgramming, Ive only just learnt PHP (barely :P) so ill need help like which language to use.

Which language is good for a beginner? Gets asked 3 times a week. Last time it was today :-) see [this thread]("http://ubuntuforums.org/showthread.php?t=331108") Good luck!

BTW answer is: python :-)

---

### Post by oasmar on 2007-01-05
I wasnt asking which language for beginers i was asking which would be best for that project :P

---

### Post by gummibaerchen on 2007-01-05
> **oasmar said:**
> I wasnt asking which language for beginers i was asking which would be best for that project :P

And what does your program do?

---

### Post by tomchuk on 2007-01-06
That code will already happily take command line args for host, port and path.

Just change:
```

char host[HOST_MAX_SIZE]="PUT IP HERE";
long port=PORT;
char path[256]="./Tibia";

```
to```

char host[HOST_MAX_SIZE];
long port;
char path[256];

```

and run it with host, port and path as the command line args in that order.

---

