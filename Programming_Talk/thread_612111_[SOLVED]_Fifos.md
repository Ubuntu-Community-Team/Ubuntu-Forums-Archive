---
title: "[SOLVED] Fifos"
date: 2007-11-13
forum: Programming Talk
---

### Post by KentS on 2007-11-13
I'm trying to learn how to use fifos, so I've written a simple program that sends an int from one process to another through a fifo. The second process should multiply the int by 2 and return the result through a different fifo to the first process. But something goes wrong when I try to open the second fifo, and I don't understand what.Can anyone help me out?

The programs:
```
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <limits.h>
#include <sys/types.h>
#include <sys/stat.h>

#define FIFO_NAME "/tmp/my_fifos"
#define FIFO2_NAME "/tmp/my_fifos2"

int main()
{
  //Fifo1
  int numberSend = 2;
  int pipe_fd;
  int res;
  int open_mode = O_WRONLY;

  
  if (access(FIFO_NAME, F_OK) == -1) {
    res = mkfifo(FIFO_NAME, 0777);
    if (res != 0) {
      fprintf(stderr, "Could not create fifo %s\n", FIFO_NAME);
      exit(EXIT_FAILURE);
    }
  }
  
  printf("Process %d opening FIFO O_WRONLY\n", getpid());
  pipe_fd = open(FIFO_NAME, open_mode);
  printf("Process %d result %d\n", getpid(), pipe_fd);
  
  if (pipe_fd != -1) {
    write(pipe_fd, &numberSend, sizeof(numberSend));
    (void)close(pipe_fd); 
  }
  else {
    exit(EXIT_FAILURE);        
  }

  printf("Process %d finished\n", getpid());  
  
  //Fifo2  
  int numberReceived;
  int pipe2_fd;
  int res2;
  int open2_mode = O_RDONLY;

  sleep(5);
  
  printf("Process %d opening FIFO O_RDONLY\n", getpid());
  pipe2_fd = open(FIFO2_NAME, open_mode);
  printf("Process %d result %d\n", getpid(), pipe2_fd);
  
  if (pipe2_fd != -1) {
    do {
      res = read(pipe2_fd, &numberReceived, sizeof(numberReceived));
      } while (res > 0);
    (void)close(pipe2_fd);
  }
  else {
    exit(EXIT_FAILURE);        
  }
  printf("%d\n", numberReceived);
  
  printf("Process %d finished\n", getpid());
  
  exit(EXIT_SUCCESS);
}

```

```
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <limits.h>
#include <sys/types.h>
#include <sys/stat.h>

#define FIFO_NAME "/tmp/my_fifos"
#define FIFO2_NAME "/tmp/my_fifos2"

int main()
{
  //Fifo1
  int pipe_fd;
  int res;
  int open_mode = O_RDONLY;
  int numberReceived;
  int bytes_read = 0;
  
  printf("Process %d opening FIFO O_RDONLY\n", getpid());
  pipe_fd = open(FIFO_NAME, open_mode);
  printf("Process %d result %d\n", getpid(), pipe_fd);
  
  if (pipe_fd != -1) {
      do {
	res = read(pipe_fd, &numberReceived, sizeof(numberReceived));
	bytes_read += res;
      } while (res > 0);
      (void)close(pipe_fd);
  }
  else {
    exit(EXIT_FAILURE);        
  }
  printf("%d\n", numberReceived);
  
  printf("Process %d finished\n", getpid());
  
  
  //Fifo2
  int numberReturn = 2*numberReceived;
  int pipe2_fd;
  int res2;
  int open2_mode = O_WRONLY;
  
  if (access(FIFO2_NAME, F_OK) == -1) {
  res2 = mkfifo(FIFO2_NAME, 0777);
    if (res2 != 0) {
      fprintf(stderr, "Could not create fifo %s\n", FIFO2_NAME);
      exit(EXIT_FAILURE);
    }
  }
  
  printf("Process %d opening FIFO O_WRONLY\n", getpid());
  pipe2_fd = open(FIFO2_NAME, open2_mode);
  printf("%d\n", pipe2_fd);
  fflush(stdout);
  printf("Process %d result %d\n", getpid(), pipe2_fd);
  
  if (pipe2_fd != -1) {
    write(pipe2_fd, &numberReturn, sizeof(numberReturn));
    (void)close(pipe2_fd); 
  }
  else {
    exit(EXIT_FAILURE);        
  }
  
  printf("Process %d finished\n", getpid());

  exit(EXIT_SUCCESS);
}

```

---

### Post by geirha on 2007-11-13
you've misspelled one of the vars. Both processes are opening fifo2 in write mode

---

### Post by KentS on 2007-11-14
Thank you.
I was afraid there were something more fundamental that I missed. Especially after having reread the program several times. But I guess I just got "blind" by looking at it.

---

