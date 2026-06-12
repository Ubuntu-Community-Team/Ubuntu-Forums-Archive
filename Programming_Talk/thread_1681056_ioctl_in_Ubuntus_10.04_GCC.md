---
title: "ioctl in Ubuntus 10.04 GCC"
date: 2011-02-03
forum: Programming Talk
---

### Post by BGraaf on 2011-02-03
Hi,

is there anyone to help me using the ioctl-function. My code looks like this:

------
```

#include <stdio.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <linux/dvb/dmx.h> 
#include <linux/dvb/frontend.h>


int main()
{
  char front[254];
  int adapter = 0;
  int s_adapter = 0;
  int f_open;
  int ioctl;
  int request = FE_GET_INFO;
  struct dvb_frontend_info info;
  

  for (adapter = 0; adapter < 4; ++adapter)
  {
    printf("Adapter = %i\n", adapter);
    for (s_adapter = 0; s_adapter != -1; ++s_adapter)
    {
    sprintf(front,"/dev/dvb/adapter%i/frontend%i", adapter, s_adapter);
    printf("Prüfe Adapter: %s\n", front);
    if((f_open = open(front,O_RDONLY)) < 0)
        { 
          printf("Device '%s' konnte nicht geöfnnet werden\n", front);
          s_adapter = -2;
        }
    else
    {
      if ( ioctl(f_open, request, info ) ) perror("ioctl");
      printf("Status %s\n",info.name);
        } 
    close(f_open);
    }
  }
}

```
-----------------
I compile this code very simple with following command:
gcc -o dvb_test2 dvb_test2.c

The error code I get is:
vb_test2.c:33: error: called object &#8216;ioctl&#8217; is not a function

Is there anybody who can help me?
Thanks a lot!!!!

---

### Post by johnl on 2011-02-03
```

#include <stdio.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <linux/dvb/dmx.h>
#include <linux/dvb/frontend.h>
**#include <unistd.h>  /* for close() */**

int main()
{
    char front[254];
    int adapter = 0;
    int s_adapter = 0;
    int f_open;
[B]    /* you declared an unused(?) variable named ioctl which conflicts with
     * the function named ioctl() you tried to use below.  remove or rename
     * this variable */
    /* int ioctl; */[/B]
    int request = FE_GET_INFO;
    struct dvb_frontend_info info;


    for (adapter = 0; adapter < 4; ++adapter)
    {
        printf("Adapter = %i\n", adapter);
        for (s_adapter = 0; s_adapter != -1; ++s_adapter)
        {
            sprintf(front,"/dev/dvb/adapter%i/frontend%i", adapter, s_adapter);
            printf("Prüfe Adapter: %s\n", front);
            if((f_open = open(front,O_RDONLY)) < 0)
            {
                printf("Device '%s' konnte nicht geöfnnet werden\n", front);
                s_adapter = -2;
            }
            else
            {
                if ( ioctl(f_open, request, info ) ) perror("ioctl");
                printf("Status %s\n",info.name);
            }
            close(f_open);
        }
    }
}


```

---

### Post by BGraaf on 2011-02-03
Thanks a lot.

that something we called in Germany "Den Wald vor lauter Bäumen nicht sehen".
Now its working!

---

### Post by Tony Flury on 2011-02-04
> **BGraaf said:**
> Thanks a lot.

that something we called in Germany "Den Wald vor lauter Bäumen nicht sehen".
Now its working!

An equivalent in English is "You can't see the wood for the trees"

---

