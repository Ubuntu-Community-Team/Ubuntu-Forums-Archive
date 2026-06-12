---
title: "Overwriting in Named Pipes (C)"
date: 2009-06-28
forum: Programming Talk
---

### Post by sauronnikko on 2009-06-28
Hello. I wish to have two processes communicating with each other by named pipes. I create the named piped in process 1 using mkfifo(), and then I open it in process 1 and process 2. Process 1 shall only read from the pipe and process 2 writes in it but does so within a while. For every write() operation executed by process 2, whatever was in the named pipe before is overwritten in the new write(). Obviously I just want process 1 to read every single line process 2 writes in the pipe, but as this moment, it only reads some of process 2 lines because when process 2 is running it keeps overwriting information. What should I do? Must I always stop process 2 everytime it writes something in the pipe and unstop it when it has confirmation that its line was read (If I put a sleep() everytime that p2 writes, all works but that's not the point)? Thank you.

---

### Post by soltanis on 2009-06-28
It's being overwritten? That's strange. I guess you'll need to synchronize (using signals, most likely) reading and writing to the pipe.

I've never heard of this thing happening before, I've certainly never encountered it, but I use fread/fwrite from stdio, instead of read/write from unistd. I have no idea why this would make a difference, though.

---

### Post by sauronnikko on 2009-06-28
I'm not exactly sure if there's some overwriting involved but here is what's happening exactly:

This is the reader program:

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <string.h>
#include <sys/stat.h>
#include <sys/types.h>

int main ()    {
    int fd;
    char message[100];
    unlink("pipe");                                 
    mkfifo ("pipe", S_IRWXG);                                  
    chmod("pipe", 0660);
    fd = open("pipe", O_RDONLY);
    while (1)    {
        if (read (fd, message, 100) > 10)
            printf ("%s\n", message);
    }
}

```And this is the writer program:

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <string.h>
#include <sys/stat.h>
#include <sys/types.h>

int main ()    {
    int fd, i = 0;
    char message[100];
    strcpy (message, "Hello 123 567");
    fd = open("pipe", O_WRONLY | O_APPEND);
    while (i != 3)    {
        write (fd, message, strlen (message) + 1);
        i++;
    }
}

```If one runs this programs (running first the reader) one will notice that the reader just prints one "Hello 123 567" when my intention is that it should print it 4 times (because of the while in the writer program). Any thoughts?

---

### Post by lloyd_b on 2009-06-28
I don't see the problem.  Using your code, the reader program produces the following output:```
lloyd@dell:~/stuff$ ./reader
Hello 123 567
Hello 123 567
Hello 123 567
```
Which exactly what I would expect - your loop will only iterate 3 times (0, 1, and 2, terminating with 3).

Lloyd B.

---

### Post by sauronnikko on 2009-06-28
lloyd_b, you're absolutely right. It prints 3 times but it does not always print 3 times. Sometimes it prints once or twice. It's kind of a mistery. Perhaps you tried once and got that result, but if you run these programs more times, you can get this anomaly:

```

nikko@nikko-laptop:~/Desktop/Operativos/Proyecto 2/Pruebas/PipesNominales$ ./reader
Hello 123 567
^Z
[14]+  Stopped                 ./reader
nikko@nikko-laptop:~/Desktop/Operativos/Proyecto 2/Pruebas/PipesNominales$ ./reader
Hello 123 567
^Z
[15]+  Stopped                 ./reader
nikko@nikko-laptop:~/Desktop/Operativos/Proyecto 2/Pruebas/PipesNominales$ ./reader
Hello 123 567
Hello 123 567
Hello 123 567
^Z
[16]+  Stopped                 ./reader
nikko@nikko-laptop:~/Desktop/Operativos/Proyecto 2/Pruebas/PipesNominales$ 
nikko@nikko-laptop:~/Desktop/Operativos/Proyecto 2/Pruebas/PipesNominales$ ./reader
Hello 123 567

```

Notice how weird is this, sometimes it does it right and sometimes it does not

---

### Post by lloyd_b on 2009-06-28
You are assuming that each time you call read(), you will get the results of a single write() from the writer program.  This is NOT guaranteed behavior.

So what's happening is that the read() may only be reading 8 bytes from the pipe before being interrupted, but these bytes are thrown away (because it got less than 10).  The next read cycle, there may still be bytes in the buffer, but it's still less than 10, so these are thrown away as well.

Here are some variants of your code, with two changes.  First, the reader code reads a byte at a time, displaying it if anything is received.  Second, the writer code appends a newline onto the data being sent (because we have no reliable way to tell where one message ends and another starts, we need to newline in the sent data).

reader:```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <string.h>
#include <sys/stat.h>
#include <sys/types.h>

int main ()    {
    int fd;
    char message[100];
    unlink("pipe");
    mkfifo ("pipe", S_IRWXG);
    chmod("pipe", 0660);
    fd = open("pipe", O_RDONLY);
    while (1)    {
        if (read (fd, message, 1) > 0)
            printf ("%c", *message);
    }
}
```
writer```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <string.h>
#include <sys/stat.h>
#include <sys/types.h>

int main ()    {
    int fd, i = 0;
    char message[100];
    strcpy (message, "Hello 123 567\n");
    fd = open("pipe", O_WRONLY | O_APPEND);
    while (i != 3)    {
        write (fd, message, strlen (message) + 1);
        i++;
    }
}
```

For "real world" code, you should have a buffer (such as message) that you append data from the read onto, and when you have a complete message (either a fixed number of bytes or terminated by something like newline or '\0') you can take those bytes, and then output them.

Lloyd B.

---

### Post by sauronnikko on 2009-06-28
I wrote the programs as you did and everything worked fine. Thank you!

---

### Post by soltanis on 2009-06-29
fread and fwrite do this kind of buffering for you (fread reads until it has an error or has read all the bytes you told it to, fwrite writes until it has an error or has written all the bytes you told it to). So yeah. That would explain it.

---

