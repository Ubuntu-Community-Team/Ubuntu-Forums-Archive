---
title: "network programming"
date: 2013-05-25
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-25
i want to write a sever application.my sever have some service to client. some of the answer of my server is long(transfer file) and some of them is short(list of online client).
 when server transferring file to a client , other client request to get online client list. i want first job pause and answer the second then return first job.

and my server code is below:
what should i do?!


```

int runServer(char* pathDir, int portNum)
{
    int tcp_socket,maxSelect,activity,newSocket;
    struct sockaddr_in server_addr;
    int server_addr_length;

    tcp_socket = socket(AF_INET,SOCK_STREAM,0); // IPV4 , TCP , IP
    if ( tcp_socket==-1 )
    {
        char handle_error[] = "socket not created so application terminate, please run again.";
        write(1,handle_error,strlen(handle_error));
        return -1;
    }
    int opt=TRUE;
    if(setsockopt(tcp_socket,SOL_SOCKET,SO_REUSEADDR,(char*)&opt,sizeof(opt))<0)
    {
        char handle_error ="ERROR: problem in set socket option occurred\n";
        write(1,handle_error,strlen(handle_error));
    }
    server_addr.sin_family = AF_INET;                // family address ipv4
    server_addr.sin_port= htons(portNum);                    // port number
    server_addr.sin_addr.s_addr = INADDR_ANY;        // recieve message from all address

    int mybind = bind(tcp_socket,(struct  sockaddr*)&server_addr,sizeof(server_addr));
    if(mybind==-1)
    {
        char handle_error[] = " ERROR in binding\n";
        write(1,handle_error,strlen(handle_error));
        return 0;
    }
    listen(tcp_socket,MAX_USER);
    while(TRUE)
    {
        FD_ZERO(&readfd);//clear the socket set
        FD_SET(tcp_socket,&readfd);//add socket
        maxSelect=tcp_socket;

        // add child socket
        int k;
        for(k=0;k<MAX_USER;k++)
        {

            if(clientList[k].isThere==1)
            {
                FD_SET(clientList[k].userIdNumber,&readfd);
                if(clientList[k].userIdNumber>maxSelect)
                    maxSelect=clientList[k].userIdNumber;
            }
        }
        activity= select(maxSelect+1,&readfd,NULL,NULL,NULL);

        if(FD_ISSET(tcp_socket,&readfd))                                //request for connecting
        {
            function that answer conection request;
        }
        int y;
        for(y=0;y<MAX_USER;y++)
        {
            find who request and answer to him
        }
    }
}

```

---

### Post by dwhitney67 on 2013-05-25
If your server is going to service multiple clients, you can consider one of the following approaches:

1.  Handle one socket at a time (this seems to be what you are doing).
2.  Create a separate process to handle each client (i.e. consider using fork())
3.  Create a separate thread to handle each client (i.e. consider pthreads).

Most advanced servers employ choices 2 or 3, with 3 being the most used strategy.

---

### Post by ferizhandi on 2013-05-25
yeah, my purpose is first approach. my problem is implementation of this approach.
how can i listen to all client when transfer a file to one client?!

---

### Post by dwhitney67 on 2013-05-25
> **ferizhandi said:**
> yeah, my purpose is first approach. my problem is implementation of this approach.
how can i listen to all client when transfer a file to one client?!

You could accomplish your approach, however with much more difficulty that I personally would endeavor, or recommend, to do.  Use a separate thread to handle each client, and your life (err, application) will be much simpler.

---

