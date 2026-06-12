---
title: "Problem with reading and writing to FIFO pipe"
date: 2011-02-21
forum: Programming Talk
---

### Post by Tcressy on 2011-02-21
I'm trying to setup two simple processes (separate c files), where one writes to the respective pipe, and the other reads and displays the message in standard out. Problem is I keep on getting extra gibberish on the receiving end. 
Here is my code:

Receiving end
```
#include "npipe.h"

int main(int argc, char** argv) {
    char line[MAX_LINE];
    int pipe;
    
    // open a named pipe
    pipe = open("/tmp/myFIFO", O_RDONLY);
    
    // set the mode to blocking
    int flags;
    //flags &= ~O_NONBLOCK;    //Default
    //flags |= O_NONBLOCK;
    //fcntl(pipe, F_SETFL, flags); /*Tried with and without changing the flags*/
   
    // read the data from the pipe
    read(pipe, line, MAX_LINE);
    
    printf("Received line: %s\n", line);
    
    // close the pipe
    close(pipe);
    return 0;
}
```Writing end
```
#include "npipe.h"

int main(int argc, char** argv) {
    char line[MAX_LINE];
    int pipe;
    
    int stat;
    if (stat = mkfifo("/tmp/myFIFO", 0600) < 0)
        oops("Cannot make FIFO", stat);
    
    // open a named pipe
    pipe = open("/tmp/myFIFO", O_WRONLY);
    
    while(1)
    {
        // get a line to send
        printf("Enter line: ");
        int i=0;
        fgets(line, MAX_LINE, stdin);
        
        if (strcmp(line, "quit\n") == 0)
            break;
        
        // actually write out the data and close the pipe
        write(pipe, line, strlen(line));
    }
    // close the pipe
    close(pipe);
    return 0;
} 
```This is the mutual header file.
```

#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include    <string.h>

#define MAX_LINE 80
#define oops(m,x)    { perror(m); exit(x); }

```My input to send is
> ~/Dev/npipe$ ./send 
Enter line: hi
My output from receive is
> ~/Dev/npipe$ ./receive 
Received line: hi
&#65533;Mp&#65533;&#65533;&#65533;b&#65533;&#65533;f&#319;&#65533;ia&#65533;&#65533;_u&#65533;&#65533;&#65533;f&#319;&#65533;0@x&#65533;&#65533;&#65533;f&#319;&#65533;$cu&#65533;&#65533;_u&#65533;p&#65533;f&#319;&#65533;&#65533;b&#65533;0@x&#65533;{&#65533;I don't know how to get rid of the gibberish at the end. I don't want to use string manipulation to get rid of it, I would prefer to just have a "clean" string if you will. Any help would be appreciated.

---

### Post by Arndt on 2011-02-21
> **Tcressy said:**
> I'm trying to setup two simple processes (separate c files), where one writes to the respective pipe, and the other reads and displays the message in standard out. Problem is I keep on getting extra gibberish on the receiving end. 
Here is my code:

Receiving end
```
#include "npipe.h"

int main(int argc, char** argv) {
    char line[MAX_LINE];
    int pipe;
    
    // open a named pipe
    pipe = open("/tmp/myFIFO", O_RDONLY);
    
    // set the mode to blocking
    int flags;
    //flags &= ~O_NONBLOCK;    //Default
    //flags |= O_NONBLOCK;
    //fcntl(pipe, F_SETFL, flags); /*Tried with and without changing the flags*/
   
    // read the data from the pipe
    read(pipe, line, MAX_LINE);
    
    printf("Received line: %s\n", line);
    
    // close the pipe
    close(pipe);
    return 0;
}
```Writing end
```
#include "npipe.h"

int main(int argc, char** argv) {
    char line[MAX_LINE];
    int pipe;
    
    int stat;
    if (stat = mkfifo("/tmp/myFIFO", 0600) < 0)
        oops("Cannot make FIFO", stat);
    
    // open a named pipe
    pipe = open("/tmp/myFIFO", O_WRONLY);
    
    while(1)
    {
        // get a line to send
        printf("Enter line: ");
        int i=0;
        fgets(line, MAX_LINE, stdin);
        
        if (strcmp(line, "quit\n") == 0)
            break;
        
        // actually write out the data and close the pipe
        write(pipe, line, strlen(line));
    }
    // close the pipe
    close(pipe);
    return 0;
} 
```This is the mutual header file.
```

#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include    <string.h>

#define MAX_LINE 80
#define oops(m,x)    { perror(m); exit(x); }

```My input to send is
My output from receive is
I don't know how to get rid of the gibberish at the end. I don't want to use string manipulation to get rid of it, I would prefer to just have a "clean" string if you will. Any help would be appreciated.

With 'read', you read arbitrary data, possibly including Nul characters. That means it does not write a Nul to the end in order to produce a C string. Instead it returns how many bytes were received, as the return value of 'read'.

From the manual page:

```
RETURN VALUE
       On success, the number of bytes read is returned (zero indicates end of
       file), and the file position is advanced by this number. 

```

---

### Post by greenmonkeey on 2011-02-21
i can run it..

---

### Post by slavik on 2011-02-21
use fopen/fgets in reader and fopen/fprintf in writer.

---

### Post by Tony Flury on 2011-02-21
> **Arndt said:**
> With 'read', you read arbitrary data, possibly including Nul characters. That means it does not write a Nul to the end in order to produce a C string. Instead it returns how many bytes were received, as the return value of 'read'.

From the manual page:

```
RETURN VALUE
       On success, the number of bytes read is returned (zero indicates end of
       file), and the file position is advanced by this number. 

```

@Tcressy
In other words - you need to use the return value of the read function call to re-insert the NUL character into your received string.

Using Slaviks suggestion using fprintf, fgets will handle the Nul characters etc for you, and give you all the formatting power too - should you need it.

@greenmonkeey : The reason your run may work "properly" as it all depends on the data in the receiving buffer - if when you run your code the memory for your buffer happens to be filled with zeros (or even just have a zero in the right place) then the code will appear to work correctly, however arrays are not initialised to all zeros in C, and therefore you should not rely on it always working.

---

### Post by Tcressy on 2011-02-21
> **Tony Flury said:**
> @Tcressy
In other words - you need to use the return value of the read function call to re-insert the NUL character into your received string.

Using Slaviks suggestion using fprintf, fgets will handle the Nul characters etc for you, and give you all the formatting power too - should you need it.

@greenmonkeey : The reason your run may work "properly" as it all depends on the data in the receiving buffer - if when you run your code the memory for your buffer happens to be filled with zeros (or even just have a zero in the right place) then the code will appear to work correctly, however arrays are not initialised to all zeros in C, and therefore you should not rely on it always working.

Thanks a bunch, works...and better yet I understand it.

I know i could have used fprintf and family, but I needed to use the bare system calls for academic purposes.

THANKS!

---

