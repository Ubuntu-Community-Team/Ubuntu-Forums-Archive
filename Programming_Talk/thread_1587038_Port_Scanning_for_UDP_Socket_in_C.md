---
title: "Port Scanning for UDP Socket in C"
date: 2010-10-02
forum: Programming Talk
---

### Post by PirateMcplunder on 2010-10-02
Hello!

Could someone more knowledgeable than myself please help me to understand how I can modify the code posted below (sourced from: [http://beej.us/guide/bgnet/output/html/multipage/clientserver.html#datagram]("http://beej.us/guide/bgnet/output/html/multipage/clientserver.html#datagram") ) to allow for a dynamic port scan.  I would like to start from 65535 and decrement downwards to 49152.  

The code below works great for communicating but I am having trouble altering it to allow for a non-hard-coded port.  MYPORT is defined as "4950" so my attempts to replace MYPORT with an int variable result in a problem with [getaddrinfo()]("http://en.wikipedia.org/wiki/Getaddrinfo").  I have already learned a great deal from my short time as a reader of these forums and I would be grateful for any help provided.

```
/*
** listener.c -- a datagram sockets "server" demo
*/

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>

#define MYPORT "4950"    // the port users will be connecting to

#define MAXBUFLEN 100

// get sockaddr, IPv4 or IPv6:
void *get_in_addr(struct sockaddr *sa)
{
    if (sa->sa_family == AF_INET) {
        return &(((struct sockaddr_in*)sa)->sin_addr);
    }

    return &(((struct sockaddr_in6*)sa)->sin6_addr);
}

int main(void)
{
    int sockfd;
    struct addrinfo hints, *servinfo, *p;
    int rv;
    int numbytes;
    struct sockaddr_storage their_addr;
    char buf[MAXBUFLEN];
    socklen_t addr_len;
    char s[INET6_ADDRSTRLEN];

    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC; // set to AF_INET to force IPv4
    hints.ai_socktype = SOCK_DGRAM;
    hints.ai_flags = AI_PASSIVE; // use my IP

    if ((rv = getaddrinfo(NULL, MYPORT, &hints, &servinfo)) != 0) {
        fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(rv));
        return 1;
    }

    // loop through all the results and bind to the first we can
    for(p = servinfo; p != NULL; p = p->ai_next) {
        if ((sockfd = socket(p->ai_family, p->ai_socktype,
                p->ai_protocol)) == -1) {
            perror("listener: socket");
            continue;
        }

        if (bind(sockfd, p->ai_addr, p->ai_addrlen) == -1) {
            close(sockfd);
            perror("listener: bind");
            continue;
        }

        break;
    }

    if (p == NULL) {
        fprintf(stderr, "listener: failed to bind socket\n");
        return 2;
    }

    freeaddrinfo(servinfo);

    printf("listener: waiting to recvfrom...\n");

    addr_len = sizeof their_addr;
    if ((numbytes = recvfrom(sockfd, buf, MAXBUFLEN-1 , 0,
        (struct sockaddr *)&their_addr, &addr_len)) == -1) {
        perror("recvfrom");
        exit(1);
    }

    printf("listener: got packet from %s\n",
        inet_ntop(their_addr.ss_family,
            get_in_addr((struct sockaddr *)&their_addr),
            s, sizeof s));
    printf("listener: packet is %d bytes long\n", numbytes);
    buf[numbytes] = '\0';
    printf("listener: packet contains \"%s\"\n", buf);

    close(sockfd);

    return 0;
}
```

Thanks in advance!

---

### Post by dwhitney67 on 2010-10-02
I would remove the following:
```

#define MYPORT "4950"    // the port users will be connecting to

```
Then, add a loop to your code, for each port of interest, then formulate a string (with the port number) before each call to getaddrinfo().
```

...

for (int port = 65535; port >= 49152; --port)
{
   ...

   char portstr[6] = {0};

   snprintf(portstr, sizeof(portstr), "%d", port);

   if ((rv = getaddrinfo(NULL, portstr, &hints, &servinfo)) != 0) {
       fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(rv));
       return 1;
   }

    ...
}

```

---

### Post by PirateMcplunder on 2010-10-02
Thank you! This use of snprintf is exactly what was eluding me all afternoon.

The only other thing I had to do was to change the declaration of int to occur before the for loop (I'm not sure how to specify C99 standards for the compiler I am using).

Working perfectly! Many thanks!

final code is posted below for reference:
```
/*
** listener.c -- a datagram sockets "server" demo
*/

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>

#define MAXBUFLEN 100

// get sockaddr, IPv4 or IPv6:
void *get_in_addr(struct sockaddr *sa)
{
    if (sa->sa_family == AF_INET) {
        return &(((struct sockaddr_in*)sa)->sin_addr);
    }

    return &(((struct sockaddr_in6*)sa)->sin6_addr);
}

int main(void)
{
    int sockfd;
    struct addrinfo hints, *servinfo, *p;
    int rv;
    int numbytes;
    struct sockaddr_storage their_addr;
    char buf[MAXBUFLEN];
    socklen_t addr_len;
    char s[INET6_ADDRSTRLEN];
	char portstr[6] = {0};
	unsigned int port;
	
    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC; // set to AF_INET to force IPv4
    hints.ai_socktype = SOCK_DGRAM;
    hints.ai_flags = AI_PASSIVE; // use my IP

	for (port = 65535; port >= 49152; --port)
	 {
		snprintf(portstr, sizeof(portstr), "%d", port);
		
		if ((rv = getaddrinfo(NULL, portstr, &hints, &servinfo)) != 0) 
		 {
			fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(rv));
			return 1;
		 }
	 }

    // loop through all the results and bind to the first we can
    for(p = servinfo; p != NULL; p = p->ai_next) {
        if ((sockfd = socket(p->ai_family, p->ai_socktype,
                p->ai_protocol)) == -1) {
            perror("listener: socket");
            continue;
        }

        if (bind(sockfd, p->ai_addr, p->ai_addrlen) == -1) {
            close(sockfd);
            perror("listener: bind");
            continue;
        }

        break;
    }

    if (p == NULL) {
        fprintf(stderr, "listener: failed to bind socket\n");
        return 2;
    }

    freeaddrinfo(servinfo);

    printf("listener: waiting to recvfrom...\n");

    addr_len = sizeof their_addr;
    if ((numbytes = recvfrom(sockfd, buf, MAXBUFLEN-1 , 0,
        (struct sockaddr *)&their_addr, &addr_len)) == -1) {
        perror("recvfrom");
        exit(1);
    }

    printf("listener: got packet from %s\n",
        inet_ntop(their_addr.ss_family,
            get_in_addr((struct sockaddr *)&their_addr),
            s, sizeof s));
    printf("listener: packet is %d bytes long\n", numbytes);
    buf[numbytes] = '\0';
    printf("listener: packet contains \"%s\"\n", buf);

    close(sockfd);

    return 0;
}

```

---

### Post by PirateMcplunder on 2010-10-02
hmm.  seems like I lied.  Can't get this to work now.  program appears to hang at runtime. any thoughts?

---

### Post by PirateMcplunder on 2010-10-02
getting the following errors spammed quickly: 
listener: socket: Address family not supported by protocol
listener: socket: Too many open files

going to try to put in a wait timer between requests to see if that helps but I think there is a formatting issue with the port field.

---

### Post by dwhitney67 on 2010-10-02
The scope of your newly added for-loop seems wrong; for each port, if getaddrinfo() is successful, then you should attempt to bind() to the port.  If the bind() operation fails, then this implies that some other application has the port in use.

```

for (port = 65535; port >= 49152; --port)
{
   snprintf(...);

   getaddrinfo(...);

   if (bind(...) != 0)
   {
      port is in use.
   }

   close(socket);
}

```

---

