---
title: "Ubuntu 12.04.4 LTS and recv() doesn't block in a loop?!"
date: 2014-03-31
forum: Programming Talk
---

### Post by luke17 on 2014-03-31
Hello!
I'm writing a simple tcp server in C as a part of a school project. It's multithreaded server which has to parse few commands send from users, communicate with MySQL server etc. However I noticed that when client thread enters in the infinite loop with recv() it consumes 100% of my CPU time. The client socket is in default blocking mode, so recv() should wait until client actually will send some data, unfortunately it doesn't when it's called in a loop - before loop I use recv() to get a string with login & password - recv() blocking works just fine there. Here are parts of my code:

This is how I create client thread in main():
```

while(1)
    {
        pthread_mutex_lock(&mut);
        for(i = 0; i < MAX_CLIENTS; i++)
        {
            if(cd[i].used == 0)
            {
                free_id = i;
                cd[free_id].used = 1;
                break;
            }
        }
        pthread_mutex_unlock(&mut);
        if((cd[free_id].socket = accept(s_socket,(struct sockaddr *) &cli_addr, (socklen_t *) &cli_len)) < 0)
        {
            pthread_mutex_lock(&mut);
            sprintf(logtxt,"ERROR: accept() ID: %i Sock: %i ERRNO: %s\n",free_id,cd[free_id].socket,strerror(errno));
            wlog(logtxt);
            pthread_mutex_unlock(&mut);
            exit(1);
        }
        int tid;
        tid  = free_id;
        pthread_create(&thread[tid], NULL, ClientHandler, &tid);


        free_id = -1;
    }
```

Here is the part of ClientHandler function:
```

void *ClientHandler(void *par)
{
[...]
    pthread_mutex_lock(&mut);
    sprintf(buf,"Hello! Identify yourself, please.\r\n");
    send(cd[id].socket,buf,strlen(buf),0);
    pthread_mutex_unlock(&mut);
    
    bzero(buf,BUF_SIZE);
    recv(cd[id].socket,buf,BUF_SIZE,0); // <- HERE BLOCKING WORKS
[...]

for(;;)
    {
        bzero(buf,BUF_SIZE);
        recv(cd[id].socket,buf,BUF_SIZE,0); // <- HERE IT DOESN'T BLOCK and consumes 100% of the CPU time...
                
        if(strlen(buf) > 0 && strcmp(buf,"\n") != 0 && strcmp(buf,"\r\n") != 0)
        {
        [do some stuff]
        }
    }

}
```

cd[] - is a global table of a structure of data I need for each client, includes the socket.

I have no idea, why recv() works like that in loop. I'm 100% sure it should block this loop... I have set up a virtual machine and compiled the very same code on CentOS 6.5 - it works fine - the client thread is in sleep mode and awaits for data from a client (I checked it in htop) when enters into this infinite loop, while on Ubuntu the client thread is always running and consumes CPU. Since it works on CentOS, if you have any clue how to fix my Ubuntu, please reply and help me. I'd like to keep Ubuntu on my machine... Thank you in advance!

PS. If any of you is interested I can send full code to test it on your system.

---

### Post by spjackson on 2014-03-31
Welcome to the forums.

If a system call such as recv isn't doing what you expect, then check its return code (and errno for more information).

---

### Post by luke17 on 2014-03-31
Thank you! :)
When it's in the loop it returns 0, but the socket (client or server one) is not closed - the sockets are being closed only when I kill my program. It behaves like that only on my Ubuntu... :(

EDIT: it returns -1, 0 is the buffer size.

ERRNO: Transport endpoint is not connected - but how is it possible?!

EDIT2: I haven't found the reason why it's not working. This error is really strange in my case, because usually it comes up when someone is trying to receive data straight from server socket instead of client socket - I'm trying to receive data from client socket, so really I don't know... My workaround is that I run this program under virtual machine with CentOS 6.5 and redirect ports to Ubuntu. It sucks, but it works :) so I can move forward with my project. Anyway if any of you will have some idea, please post it. I will check it. ;)

---

