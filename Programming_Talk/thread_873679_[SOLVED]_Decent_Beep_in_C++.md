---
title: "[SOLVED] Decent Beep in C++"
date: 2008-07-29
forum: Programming Talk
---

### Post by schmendrick on 2008-07-29
Is there any other way than putting a '\a' to console to make the PC speakers beep? 

i would like the speakers to beep a defined length at a defined pitch. is there any header/library that gives me that functionality in linux? 

{this is maybe a classic question, but i still did not find a useful response on the net or topic in this forum.
i did find some references on the net to some strange beep.h but i dont find any on my harddrive  }

cheers, schmendrick

---

### Post by Zugzwang on 2008-07-29
Not in a portable way - What happens for example if you are running the program remotely via a ssh session? It's not a classic question either. People are easily annoyed by such system beeps. :-)

You might want to try using ALSA/OSS/whatever. Don't know if you could just write to /dev/audio. If that still works, it might be the simplest solution.

EDIT: You could use [SoX]("http://sox.sourceforge.net/Main/HomePage") as an external program to generate and play the sounds.

---

### Post by tomchuk on 2008-07-29
Shamelessly ripped from the source of beep (apt-get install beep):
```

#include <fcntl.h>
#include <linux/kd.h>

int main(int argc, char** argv){
  int freq = 2000; // freq in hz
  int len = 1000; // len in ms

  int fd = open("/dev/console", O_WRONLY);
  ioctl(fd, KIOCSOUND, (int)(1193180/freq));
  usleep(1000*len);
  ioctl(fd, KIOCSOUND, 0);
  close(fd);
}

```

---

### Post by schmendrick on 2008-07-30
thanks guys. 

zugzwang: yes i am aware it is not portable, but if so i would have requested something like that. after all in windows i would have the C-Beep() method in windows.h and i could write me a wrapper or something. 

Conclusion:

here is what i did: i first made the code compiling with two small changes, here the complete code.


[PHP]#include <iostream>
#include <sys/ioctl.h>
#include <fcntl.h>
#include <linux/kd.h>

int main(int argc, char** argv){
  int freq = 2000; // freq in hz
  int len = 1000; // len in ms

  int fd = open("/dev/console", O_WRONLY);
  ioctl(fd, KIOCSOUND, (int)(1193180/freq));
  usleep(1000*len);
  ioctl(fd, KIOCSOUND, 0);
  close(fd);
}
[/PHP]


Then, after wondering why i did not head any sound, fetched me the source of this beep package. I then found out the program would need sudo so that i would be able to hear a sound. which is not appropriate in my case. 

well, so i now changed my program to use the external program (system installed) "beep" instead, overgiving it the length and pitch on commandline.

question solved, case closed ;)

---

### Post by tomchuk on 2008-07-30
yeah, should have mentioned that this requires write access to the /dev/console device (owned by root). Beep acomplishes this by being suid root.

---

