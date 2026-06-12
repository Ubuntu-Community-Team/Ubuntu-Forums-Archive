---
title: "Named pipes in C,  tricky problem"
date: 2009-11-23
forum: Programming Talk
---

### Post by madpig on 2009-11-23
Hi to all!

I have a little problem with inter process communication over pipes. There are 2 different processes that work in client-server style. The server receives some strings on a named pipe from a client and do things. The problem is that what server receives is little different from that the client sends. 

First i'm sending the size of the string that will be sent on the pipe, then i'm sending the string itself. For the first time it's ok, but going further, if second message is smaller than first, the read() is not aware of that, even if I tell it to read **messageSize **characters, that is different from first. Whem program prints on the screen the second string, it is the new one with appendix of what rest from last one. Example:

**Initially**

StringNumber1 *//the first string*
NewString *//the second string*

**Result**

StringNumber1 *//first iteration*
NewStringber1 *//second iteration*

In fact, that I try to do is:

```

//client
...
write(fifo, &messageSize, sizeof(int));
write(fifo, message, messageSize);
...

//server
...
read(fifo, &messageSize, sizeof(int));
read(fifo, message, messageSize);  //here is the problem
fprintf(stderr, "message: %s\n", messge); 
...

```Full code here:

Server
```


# include <stdio.h>
# include <stdlib.h>
# include <string.h>
# include <fcntl.h>

# define MSG_MAX_SIZE 100


int main(int argc, char **argv)
{
    int fifoPipe = -1;
    int messageSize = 0;
    char message[MSG_MAX_SIZE];  //standard 100
    
    fprintf(stderr, "SERVER\n");
    
    //(1.)---Making fifo---
    fprintf(stderr, "Making fifo... ");
    fifoPipe = mkfifo("csfifo", 0666);
    if(fifoPipe == 0)
    {
        fprintf(stderr, "[OK]\n");
    }
    else
    {
        fprintf(stderr, "[FAILED]\n");
        exit(1);
    }
    
    
    //(2.)---Openning fifo---
    fprintf(stderr, "Openning fifo(waiting for client to connect)... ");
    fifoPipe = open("csfifo", O_RDONLY);
    if(fifoPipe >= 0)
    {
        fprintf(stderr, "[OK]\n");
    }
    else
    {
        fprintf(stderr, "[FAILED]\n");
        exit(2);
    }
    
    //(3.)---Read cycle---
    fprintf(stderr, "Server in waiting for message mode:\n\n");
    while(1)
    {
        //(3.1)---Reading from fifo pipe and printing on the screen---
        read(fifoPipe, &messageSize, sizeof(int));
        read(fifoPipe, message, messageSize);
        //message[messageSize] = '\0'; //CORRECTION wich seems to work
        fprintf(stderr, "Size of message: [%d]\n", messageSize);
        fprintf(stderr, "Received message: %s\n", message);
        fprintf(stderr, "\n");
        
        //(3.2)---Checking message---
        if(strcmp(message, "stop") == 0)
        {
            break;
        }
    }
    
    //(4.)---Closing fifo pipe---
    fprintf(stderr, "Closing fifo pipe... ");
    if(close(fifoPipe) == 0)
    {
        fprintf(stderr, "[OK]\n");
    }
    else
    {
        fprintf(stderr, "[FAILED]\n");
        exit(4);
    }
    
    //(5.)---Unlinking fifo---
    fprintf(stderr, "Unlinking fifo... ");
    if(unlink("csfifo") == 0)
    {
        fprintf(stderr, "[OK]\n");
    }
    else
    {
        fprintf(stderr, "[FAILED]\n");
        exit(5);
    }
    
    //(.)---End of program---
    fprintf(stderr, "Server terminated.\n");
    return 0;
}


```Client
```


# include <stdio.h>
# include <stdlib.h>
# include <string.h>
# include <fcntl.h>

# define MSG_MAX_SIZE 100


int main(int argc, char **argv)
{
    int fifoPipe = -1;
    int messageSize = 0;
    char message[MSG_MAX_SIZE];  //standard 100
    
    fprintf(stderr, "CLIENT\n");
    
    //(1.)---Openning fifo---
    fprintf(stderr, "Openning fifo... ");
    fifoPipe = open("csfifo", O_WRONLY);
    if(fifoPipe >= 0)
    {
        fprintf(stderr, "[OK]\n");
    }
    else
    {
        fprintf(stderr, "[FAILED]\n");
        exit(1);
    }
    
    while(1)
    {
        //(2.)---Reading message from console---
        fprintf(stderr, "\n");
        fprintf(stderr, "Send: ");
        scanf("%s", message);
        messageSize = strlen(message); //calculating the size to send over fifo
        fprintf(stderr, "Message size: [%d]\n", messageSize);
        fprintf(stderr, "\n");
    
        //(3.)---Writing to the fifo pipe---
        write(fifoPipe, &messageSize, sizeof(int));
        write(fifoPipe, message, messageSize);
        
        //(3.1.)---Checking command---
        if(strcmp(message, "stop") == 0)
        {
            fprintf(stderr, "Received [stop] command!\n");
            break;
        }
        
    }
    
    //(4.)---Closing fifo pipe---
    fprintf(stderr, "Closing fifo pipe... ");
    if(close(fifoPipe) == 0)
    {
        fprintf(stderr, "[OK]\n");
    }
    else
    {
        fprintf(stderr, "[FAILED]\n");
        exit(4);
    }
    
    //(5.)---End of program---
    fprintf(stderr, "Client terminated.\n");
    return 0;
}

```I made a correction that in this example is commented. With that, code works but I am very curios to understand what is going on. Can someone help me? Thanks!

---

### Post by PmDematagoda on 2009-11-23
The problem is that strlen counts the number of characters of a string, *excluding* the nul character. So the nul character is not sent which printf requires in order to know when the end of the string has been reached, that also explains why your fix works. So if you want to be sending the nul character too, just add 1 to the MessageSize being sent, if not, you could also just zero the buffer after every iteration or you could use your own fix which would be appropriate as well.

---

### Post by madpig on 2009-11-23
Thanks [[COLOR=#D40000]**PmDematagoda**[/COLOR]]("http://ubuntuforums.org/member.php?u=361835") that works very well. :)

Still, what seemed strange to me is that first time, read function puts termination character by itself and not just reads messageSize number of characters. Like pseudocode:

read **messageSize** number of charaters;
put characters in the message[];
append '\0' to messageSize+1 position;  //counted from 1 to n 

Second time does not do that append if the messageSize is smaller but does if is bigger. Strange... the mechanism is not very clear.

---

### Post by dwhitney67 on 2009-11-23
Perhaps you were lucky that there was a NULL at the appropriate location in your array, 'message', thus giving you the illusion all was well.

The best thing to do it to place a NULL at the end of the received string, using 'messageSize' as an index.

One thing your server code is *currently* not doing, but should, is verify that the 'messageSize' is *not greater than* the size of 'message' minus 1 byte.

If you do not place this check in your code, it would be easy for the client app to overrun your receive buffer.  Thus, something like this might be warranted:
```

...
read(fifoPipe, &messageSize, sizeof(int));
int bytesToRead = (messageSize > (sizeof(message) - 1 ? sizeof(message) - 1 : messageSize);
read(fifoPipe, message, bytesToRead);
message[bytesToRead] = '\0';
...

```
This code is not perfect, because the client could still send a large message, thus corrupting the processing of the message on the next iteration.

The best thing to do it to use a dynamically allocated 'message' array, that is of messageSize+1 bytes.  Then you are able to read the complete message at every pass.  Just make sure you do not forget to de-allocate the 'message' array when you are done with it; otherwise your app will have a memory leak.

---

### Post by madpig on 2009-11-23
> **dwhitney67 said:**
> Perhaps you were lucky that there was a NULL at the appropriate location in your array, 'message', thus giving you the illusion all was well.

No, there wasn't. I tested the code with some modifications, like putting the '\0' in various places in the array or initialize all with same character such 'a'. This behavior persists.


> The best thing to do it to place a NULL at the end of the received string, using 'messageSize' as an index.You're right, this is a good solution. In fact I've done that but the main reason of this post isn't only practical solution. I try to code in more elegant way but I do not know very well why read() behaves like this and how it will do in different situatios, and if there is some realtion to the fifos.



> One thing your server code is *currently* not doing, but should, is verify that the 'messageSize' is *not greater than* the size of 'message' minus 1 byte.For my app it is not very important, for now I am just studying named pipes but it's a good idea, better code, thanks.

---

### Post by dwhitney67 on 2009-11-23
> **madpig said:**
> 
You're right, this is a good solution. In fact I've done that but the main reason of this post isn't only practical solution. I try to code in more elegant way but I do not know very well why read() behaves like this and how it will do in different situatios, and if there is some realtion to the fifos.


A FIFO behaves as a stream, with the obvious first-in, first-out behavior.  The read() function removes up to the N-bytes you request.  If there is more data than N-bytes in the FIFO, then it remains there until another read() is called.

As for the behavior of read(), it is quite predictable and is well documented in the manpage.  I suggest you read this information before drawing any incorrect assumptions.

---

### Post by madpig on 2009-11-23
> **dwhitney67 said:**
> A FIFO behaves as a stream, with the obvious first-in, first-out behavior.  The read() function removes up to the N-bytes you request.  If there is more data than N-bytes in the FIFO, then it remains there until another read() is called.

As for the behavior of read(), it is quite predictable and is well documented in the manpage.  I suggest you read this information before drawing any incorrect assumptions.

Already done. There is no info about the misterious '\0' so I'am almost convinced by what you said about luck. Still searching some info on the web but I think this thread could be closed or marked as solved.

Thanks for help to both.

---

