---
title: "gethostbyname problem"
date: 2006-05-04
forum: Programming Talk
---

### Post by Grampa on 2006-05-04
Hi, 

I've been having a problem with the gethostbyname function, it always returns NULL even when the IP is given directly, i'm gcc to compile it and runing it in the terminal.
If i use it in a procces directly it works, but when it's in a fuction it returns NULL

    int sockfd, portno, n;
    struct sockaddr_in serv_addr;
    struct hostent *server;
    
	portno = Snd->Port;
    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    if (sockfd < 0) 
        error("ERROR opening socket");
    //server = gethostbyname("127.0.0.1");
    if ((server = gethostbyname("127.0.0.1")) == NULL) {
    	fprintf(stderr,"ERROR, no such host\n");
       	return -1;
    }
....................

it continues but the problem must be there.

Thanks for any help you can spare

Gramps

---

### Post by lnostdal on 2006-05-04
i'm not sure here .. maybe you should check what `h_errno' contains, because it might tell you more about what is going wrong .. (see `man 3 gethostbyname')

---

### Post by RavenOfOdin on 2006-05-05
[QUOTE=Grampa]Hi, 

I've been having a problem with the gethostbyname function, it always returns NULL even when the IP is given directly, i'm gcc to compile it and runing it in the terminal.
If i use it in a procces directly it works, but when it's in a fuction it returns NULL

    int sockfd, portno, n;
    struct sockaddr_in serv_addr;
    struct hostent *server;
    
	portno = Snd->Port;
    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    if (sockfd < 0) 
        error("ERROR opening socket");
    //server = gethostbyname("127.0.0.1");
    if ((server = gethostbyname("127.0.0.1")) == NULL) {
    	fprintf(stderr,"ERROR, no such host\n");
       	return -1;
    }
....................

it continues but the problem must be there.

Thanks for any help you can spare

Gramps[/QUOTE]

1. Put INADDR_LOOPBACK (127.0.0.1) into a variable of char[32]
2. Use:

```

herror("gethostbyname");

```

for the error checking. It should do a better job of telling you what is happening - sort of like a Linux version of WSAGetLastError(), for host resolution.

3. Declare your *serv_addr.sin_family* and *serv_addr.sin_port* variables if you haven't already. *portno*, which I assume is a reference to the port that you want to listen/send on, is not going to do it all by itself.

---

