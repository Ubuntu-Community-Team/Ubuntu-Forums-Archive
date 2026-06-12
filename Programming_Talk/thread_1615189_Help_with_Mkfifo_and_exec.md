---
title: "Help with Mkfifo and exec"
date: 2010-11-06
forum: Programming Talk
---

### Post by dano88tole on 2010-11-06
Hello guys!

I am doing a project for the university and I have to do that a process has to create several children through fork(). The father process sends a pathname to each one through exec and the children must send to the father a list with the files from each directory.

The father is waiting and the children don't send anything. I must to do the pipe with mkfifo. I am trying to send text from the children but nothing happens. This is the code that I have wroten:


```

struct stat buf;
 mkfifo(NOMBREFIFO, S_IRWXU);
    while (--argc>0){
        stat (argv[argc], &buf);
        if (S_ISDIR(buf.st_mode)){
            pid = fork();
            
            if (pid<0) fprintf (stderr, "error %d", errno);
            if (pid==0) printf ("hhhhhhhhh");
            if (pid==0 && (exec=execl ("./listarordenado", argv[argc], NULL))<0) fprintf (stderr, "error %d", errno);
            if (pid>0 && wait(&status) && waitpid (pid, &status, 0)){
                printf ("ssssssssss");
                 while(TRUE) {
                      fp=open(NOMBREFIFO,O_RDONLY);
                      nbytes=read(fp,buffer,TAM_BUF-1);
                      buffer[nbytes]='\0';
                      printf("%d Cadena recibida: %s \n",i, buffer);
                      close(fp);
                      i++;
                }
                 }
         }
      }


/////***code of listarordenado*//


for (i=0; i<50; i++){
        if ((fp=open(NOMBREFIFO,O_WRONLY))==-1)
            perror("fopen");
          else {    
                descr=write(fp,argv[1],strlen(argv[1]));
        }
        
      close(fp);
    }    
```thanks,
daniel

---

### Post by craigp84 on 2010-11-07
Yuk yuk yuk! You need a role model, this is not good quality code! Lazy code.

Anyways, lecture over :-)

I suspect your code just hangs, right? Absolutely nothing happens?

Parent - forks a child, then immediately blocks, waiting for the child

Child - writes to fifo, blocks waiting for write(2) to complete. This only happens when parent read(2)'s from the fifo, but the parent is waiting, not reading.

Hope this helps

---

### Post by dwhitney67 on 2010-11-07
I would suspect that the child is not being supplied the correct args; consider this app:
```

#include <unistd.h>
#include <stdio.h>
#include <sys/wait.h>

int main(void)
{
   char* const appargv[] = { "/bin/ls", "-1", NULL };

   pid_t pid = fork();

   if (pid == 0)
   {
      /* child process */
      execl(appargv[0], appargv[0], appargv[1], appargv[2]);

      perror("execl() failed.");
   }
   else if (pid > 0)
   {
      /* parent process */
      int status = -1;
      waitpid(pid, &status, 0);
      printf("child exited with status = %d\n", status);
   }
   else
   {
      perror("Fork failed.");
   }

   return 0;
}

```
Pay close attention to the parameters passed to execl().

P.S.  execv() would be an easier function to use.

---

### Post by dano88tole on 2010-11-08
Hello!! Thank you for your answers!

---

