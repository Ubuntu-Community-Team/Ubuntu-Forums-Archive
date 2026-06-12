---
title: "&quot;Undefined reference to...&quot; When trying to compile using libuvc functions"
date: 2018-05-19
forum: Programming Talk
---

### Post by Voc on 2018-05-19
Hello everyone,

I've been trying to write a program that makes use of the new libuvc library and provided functions, however I am having difficulty getting it to compile correctly in my program.  The two files of interest are the main.c:

```

#include <stdio.h>
#include <stdlib.h>
#include <wiringPi.h>
#include <math.h>
#include "ESC.h"
#include "gyro.h"
#include "camera.h"

int main(int argc, char **argv)
{
    int error = wiringPiSetupGpio();
    
        
    return 0;
}

```

and the camera.h header:

```

#include <stdio.h>
#include <stdlib.h>
#include "libuvc/libuvc.h"
#include <turbojpeg.h>

#ifndef vision_h
#define vision_h

uvc_context_t *ctx;
uvc_device_t *dev;
uvc_device_handle_t *devh;
uvc_stream_ctrl_t ctrl;
uvc_error_t res;

void cb(uvc_frame_t *frame, void *ptr);
int initializeVision(void);
int getStereoImage(void);

int initializeVision(void)
{
    res = uvc_init(&ctx, NULL);
    res = uvc_find_device(ctx, &dev, 0, 0, NULL);
    res = uvc_open(dev, &devh);
    return 0;
}


int getStereoImage(void)
{
    return 0;
}

```

I am using geany with the following settings for compile:  ```
gcc -Wall -c "%f" 
``` and for build:  ```
gcc -Wall -o "%e" "%f" -lm -lwiringPi -lpthread
```  Whenever I try to build the program I get the following error:

```

/tmp/ccpSydXz.o: In function `initializeVision':
main.c:(.text+0x8d0): undefined reference to `uvc_init'
main.c:(.text+0x90c): undefined reference to `uvc_find_device'
main.c:(.text+0x93c): undefined reference to `uvc_open'
collect2: error: ld returned 1 exit status

```

Prior to including any of the functions in my code provided by libuvc it compiled perfectly.  I am not sure if this is an issue with libuvc being buggy or if this is a problem with my code.  Any suggestions would be appreciated!

Thanks!
Luke

---

### Post by norobro on 2018-05-19
You need to link against libuvc. Try putting -luvc in your compile command.

---

### Post by Voc on 2018-05-31
Thanks, that worked!  Marking the thread as solved.

---

