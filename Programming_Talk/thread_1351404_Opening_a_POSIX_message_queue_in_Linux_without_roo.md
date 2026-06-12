---
title: "Opening a POSIX message queue in Linux without root privileges"
date: 2009-12-10
forum: Programming Talk
---

### Post by not_a_phd on 2009-12-10
Hello All, I am writing a multi-threaded application in Linux that I would like to be POSIX compliant. I would also like to use POSIX message queues to synchronize activities and pass data between threads. My problem is that the message queue open call fails unless I run the application as root (using sudo ./my_test_app). 



 The open statement is as follows:
           my_mq = mq_open("/mymq", O_CREAT | O_RDWR, S_IRWXU, &mq_attr);


 The mq_open man page specifies that the queue name must be of the form “/somename”. If I had to guess, I think the issue is a file-system permission issue. Though I do not have any problem at all using the POSIX sem_open or shm_open commmands which require a similar resource 'file' naming convention.


 I have flailed with this issue for quite a while now trying all manner of permutations on the open statement, mounting the message queue first on the command line and changing the ownership to me, and many other things.


 Any insight as to why I can run the app as root, but not run it as me would be appreciated.

---

### Post by dwhitney67 on 2009-12-10
You're in luck... here's a complete example which I have, which not only works properly, but also does not require root-privileges.

You will probably be most interested in the Sender.c module.

I apologize if the code is not commented to your satisfaction.

Msg.h:
```

#ifndef MSG_H
#define MSG_H

typedef struct
{
  unsigned int x;
  unsigned int y;
  unsigned int z;
} Msg;

#endif

```

Sender.c:
```

#include "Msg.h"

#include <mqueue.h>
#include <stdbool.h>
#include <signal.h>
#include <stdio.h>
#include <stdlib.h>    // for srand(), rand()
#include <time.h>      // for time()
#include <errno.h>
#include <string.h>


bool quit = false;

void sigHandler(int sig)
{
  quit = true;
}


int main(int argc, char** argv)
{
  if (argc != 2)
  {
    printf("Usage:  %s /qname\n", argv[0]);
    return 1;
  }

  char*  name  = argv[1];
  int    flags = O_RDWR | O_CREAT;
  mode_t mode  = S_IRUSR | S_IWUSR | S_IRGRP | S_IWGRP | S_IROTH | S_IWOTH;

  struct mq_attr attr;
  attr.mq_flags   = 0;
  attr.mq_maxmsg  = 10;
  attr.mq_msgsize = sizeof(Msg);
  attr.mq_curmsgs = 0;

  mqd_t qid = mq_open(name, flags, mode, &attr);

  if (qid == -1)
  {
    printf("error: %s (%d)\n", strerror(errno), errno);
    return 1;
  }

  signal(SIGINT, sigHandler);

  srand(time(0));

  printf("Press enter to send a message...");
  getchar();

  do
  {
    Msg msg = {rand() % 100, rand() % 100, rand() % 100};

    printf("sending msg = (%03d, %03d, %03d)\n", msg.x, msg.y, msg.z);

    if (mq_send(qid, (char*) &msg, sizeof(Msg), 0) == -1)
    {
      perror("Failed to send msg");
    }

    printf("Press enter to send another message...");
    getchar();

  } while (!quit);

  mq_close(qid);
  mq_unlink(argv[1]);

  return 0;
}

```
Receiver.c:
```

#include "Msg.h"

#define _XOPEN_SOURCE 600
#include <time.h>
#include <mqueue.h>
#include <signal.h>
#include <stdio.h>
#include <errno.h>
#include <string.h>
#include <stdbool.h>


bool quit = false;

void sigHandler(int sig);


int main(int argc, char** argv)
{
  if (argc != 2)
  {
    printf("Usage:  %s /qname\n", argv[0]);
    return 1;
  }

  char* name  = argv[1];
  int   flags = O_RDONLY;

  mqd_t qid = mq_open(name, flags);

  if (qid == -1)
  {
    perror("Failed to open the message queue");
  }

  signal(SIGINT, sigHandler);

  while (!quit)
  {
    Msg msg = {0,0,0};
    unsigned int priority = 0;
    struct timespec ts = {time(0) + 5, 0};

    if (mq_timedreceive(qid, (char*) &msg, sizeof(msg), &priority, &ts) != -1)
    {
      printf("msg = (%03d, %03d, %03d)\n", msg.x, msg.y, msg.z);
    }
    else
    {
      printf("error: %s (%d)\n", strerror(errno), errno);
    }
  }

  mq_close(qid);

  return 0;
}


void sigHandler(int sig)
{
  quit = true;
}

```
To build the code, I used a Makefile... here it is:
```

SRC1     = Sender.c
SRC2     = Receiver.c
OBJ1     = $(SRC1:.c=.o)
OBJ2     = $(SRC2:.c=.o)
CFLAGS   = -Wall -pedantic -D_GNU_SOURCE -std=gnu99
INCLUDES = -I./
LIBS     = -lrt
LIBPATH  =
DEP_FILE = .depend
SNDR     = sndr
RCVR     = rcvr

.PHONY: all clean distclean


all: depend $(SNDR) $(RCVR)

$(SNDR): $(OBJ1)
	@echo Makefile - linking $@
	@$(CC) $(LIBPATH) $(LIBS) $^ -o $@

$(RCVR): $(OBJ2)
	@echo Makefile - linking $@
	@$(CC) $(LIBPATH) $(LIBS) $^ -o $@

.c.o:
	@echo Makefile - compiling $<
	@$(CC) $(CFLAGS) $(INCLUDES) -c $< -o $@

clean:
	$(RM) $(OBJ1) $(OBJ2)

distclean: clean
	$(RM) $(SNDR) $(RCVR)
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CC) -E -MM $(CFLAGS) $(INCLUDES) $(SRC1) >> $(DEP_FILE)
	@$(CC) -E -MM $(CFLAGS) $(INCLUDES) $(SRC2) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

---

### Post by not_a_phd on 2009-12-10
Thank You dwhitney!! 

I was able to spot my problem by inspecting your code. I was setting the mq_maxmsg parameter to a value that is higher than the currently supported kernel default value (10). This was what required the root privilege. Since I do not need such a large message stack, I can avoid the root privilege conundrum.

Thanks Again!!

---

