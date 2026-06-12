---
title: "C - Continuously analyze of standard output from other program"
date: 2011-07-09
forum: Programming Talk
---

### Post by lifedj87 on 2011-07-09
I have to create a program that do this

start another existing program
capture the standard output of the previos program and depending on what it print, it do something else.

I will try to explain the situation with an example:

Let's think that I have a program (example.c) that print a sequence of number (from 1 to 1000).
I have to create a program that start the "example.c" program and read  the output continuously, so, when it print the number 348, it stop the  example program!

I could separate the two processes (caller and example) with a fork, but I don't know how to analyze continuously the output!

Is there someone that can help me?

Thank you very much!

---

### Post by Arndt on 2011-07-09
> **lifedj87 said:**
> I have to create a program that do this

start another existing program
capture the standard output of the previos program and depending on what it print, it do something else.

I will try to explain the situation with an example:

Let's think that I have a program (example.c) that print a sequence of number (from 1 to 1000).
I have to create a program that start the "example.c" program and read  the output continuously, so, when it print the number 348, it stop the  example program!

I could separate the two processes (caller and example) with a fork, but I don't know how to analyze continuously the output!

Is there someone that can help me?

Thank you very much!

Have you been told about pipes?

---

### Post by lifedj87 on 2011-07-10
No, I've never studied it!
Thank you for the help! I will look for pipes and I will ask you something else if necessary! ;-)

---

### Post by lifedj87 on 2011-07-11
I'm near the right solution, but the program i've created doesn't work properly!
I would pause the parent process when it print the number 345, but it doesn't do it: if i print all the output, after the line "Process stopped" it print all the other numbers!

I think that the problem is that it doesn't anayze the output as a runtime, but that it analyze it only after the end of the execution.
Is there someone who can help me?

This is the code:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <signal.h>

int main() {
    
    int pdes[2];

    pipe(pdes);

    int r = fork();
    
    if (r == -1)
    {
        /* errore */
        printf("Errore nella fork!\n");
        
    }
    else if(r == 0)
    {
        /* son */
        close(pdes[1]);
        char buf[20];
        size_t nbytes;
        ssize_t bytes_read;
        nbytes = sizeof(buf);
        bytes_read = read(pdes[0], buf, nbytes);
        char string_to_recognize[]="345";
        int j=0;
        int l=0;
        int ok=0;
        int indice=1;
        int found=0;
        while(bytes_read = read(pdes[0], buf, nbytes))
        {
            int i;
            for(i = 0; i < 20;i++)
            {
                if ((buf[i] == string_to_recognize[0]) && (found!=1))
                {
                    j=1;
                    ok=1;
                }
                if ((ok!=1) && (found!=1))
                {
                    if (buf[i] == string_to_recognize[j])
                    {
                        j++;
                        ok=1;
                    }
                    else
                    {
                        j=0;
                    }
                }
                if (j==(sizeof(string_to_recognize)-1))
                {
                    
                    /* after the identification of the string, count 10 letters and then bring the process in pause*/
                    if (l==10)
                    {
                        int id_proc=getppid();  /* get parent id */
                        //execlp("kill", "KILL", "-SIGSTOP "+id_proc, NULL);
                        signal(SIGTSTP, SIG_DFL);   /* reset disposition to default */

                        kill(id_proc, SIGTSTP);     /*process pause */
                    }
                    l++;
                    //j=0;
                    found=1;
                }
                //printf("%c",buf[i]);
                ok=0;
            }
        }
        if (found ==1)
        {
            l++;
            /* after the pause, count 10000-10 letters and then i restart the process*/
                    
            //if (l==10000)
            //{
            //    int id_proc=getppid();  /* get the parent id*/
            //    kill(id_proc, SIGCONT);     /*restart the process */
            //        
            //}
        }
    }
    else
    {
        /* parent code */
        close(pdes[0]);
        dup2(pdes[1], STDOUT_FILENO);
        execlp("/home/lifedj/progetto/comando.sh", "./comando.sh", "", NULL);
    }
    return 0;
}

```

---

### Post by Bachstelze on 2011-07-11
(never mind)

---

### Post by Bachstelze on 2011-07-11
What does your .sh script do?  Most likely the problem is that between the moment your program detects the target string and the moment the target program is actually killed, it will still be running and outputting text.  With this program:

```
#include <signal.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char **argv, char **envp) {
    
    int pdes[2];

    if (pipe(pdes) != 0) {
            perror("Couldn't create the pipe");
            exit(EXIT_FAILURE);
    }

    int r = fork();
    if (r == -1) {
        perror("Couldn't fork");
        exit(EXIT_FAILURE);
    } else if (r == 0) {
        /* Child */
        close(pdes[1]);
        dup2(pdes[0], STDIN_FILENO);
        char buf[20];
        char target[] = "350";
        FILE *ofile = fopen("output.txt", "w");
        while (fgets(buf, 20, stdin) != NULL) {
                fputs(buf, ofile);
                /* Remove the newline so that it does not interfere with strncmp() */
                if (buf[strlen(buf) - 1] == '\n') {
                        buf[strlen(buf) - 1] = 0;
                }

                if (strncmp(buf, target, 20) == 0) {
                        fputs("Target number found!\n", ofile);
                        int ppid = getppid();
                        kill(ppid, SIGINT);
                }
        }
        fclose(ofile);
    } else {
        /* Parent */
        close(pdes[0]);
        dup2(pdes[1], STDOUT_FILENO);
        execve("./sequence", argv, envp);
    }
    return 0;
}

```

And sequence being this:

```
#include <stdio.h>

int main(void)
{
        int i=0;
        for (;;) {
                printf("%d\n", i++);
        }
        return 0;
}

```

I get the numbers up to about 3500 in output.txt, so it means that the process does get killed, just not right after the target string is detected. I don't think there is a way to make it terminate right away without modifying its code.

---

### Post by lifedj87 on 2011-07-11
Symply print a sequence of 1000 numbers from 0 to 999!

---

### Post by Bachstelze on 2011-07-11
> **lifedj87 said:**
> Symply print a sequence of 1000 numbers from 0 to 999!

Then just make it indefinitely output numbers as I did above and you will see it does eventually terminate. ;)

---

### Post by lifedj87 on 2011-07-11
I haven't seen your answer!
I will try immediately!
Thank you!!!

Another question: if I want to resume the process from pause after x seconds, how I have to modify your code?

---

### Post by lifedj87 on 2011-07-11
I've just tried your code: the error is the same:
Even if the code works, if i try to add

fputs(buf, stderr);

after
fputs(buf, ofile);

It prints all the numbers (from 350 to 999), so the problem is not solved: the program execcute all the script and then it analyzes the output! Is there a way to do it simultaneosly?
The only modification that I did to your code is that I continue to use execlp instead of execve because I can't let it work with execve (if I try to compile and then execute the program, it doesn't start the script thet you call sequence!

Could it be the reason why the code doesn't work?

PS. Thank you for your help!

---

### Post by Bachstelze on 2011-07-11
> **lifedj87 said:**
> 
It prints all the numbers (from 350 to 999), so the problem is not solved: the program execcute all the script and then it analyzes the output! Is there a way to do it simultaneosly?

Did you read what I said? Between the moment you run kill() and the moment the process is actually killed, there is a lot of time during which the process is still running and outputting text. There no way to kill the process immediately (that I know of, and I would be very surprised if there were).

---

### Post by lifedj87 on 2011-07-12
Ah, ok! I didn't undestand!
Thank you very much!

However: if I would like to resume the process from pause, where I have to modify the code?
I would like to pause it and then restart after x seconds!

---

### Post by Bachstelze on 2011-07-12
Just replace

```
kill(ppid, SIGINT);
```

with something like

```
kill(ppid, SIGSTOP);
sleep(10);
kill(ppid, SIGCONT);
```

---

### Post by lifedj87 on 2011-07-12
Ok, i will try! Thank you very much!!! ;-)

---

