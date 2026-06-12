---
title: "problems understanding Ubuntu socket API"
date: 2011-05-08
forum: Programming Talk
---

### Post by tjwilson1973 on 2011-05-08
I am experimenting with C socket programming on Ubuntu 10.04. I have modified the client example given in the man pages for getaddrinfo to emulate a script I wrote in perl which downloads the flight information for the Philadelphia International airport. Here is the perl script:

use Socket;

my $dest = 'www.phl.org';
my $port = 80;
my $freq = '/cgi-bin/fidsarrival.pl';

my $proto = getprotobyname('tcp');

if(!defined socket(FS, PF_INET, SOCK_STREAM, $proto))
{
    print "Error initializing socket...\n";
}
my $sin = sockaddr_in($port,inet_aton($dest));

if(!defined connect(FS,$sin))
{
    print "Error connecting to remost host...\n";
}

# request the path of the document to get
$data = "GET $freq HTTP/1.0\nAccept: */*\nUser-Agent: getFlightInfo/1.0\n\n";

send(FS,$data,length($data));

@filein = <FS>;
foreach my $html_line (@filein)
{
    print $html_line;
}

The above perl script works when run from the command line like this:
sobukwe@sobukwe-desktop:~/networkapps$ perl getFlightInfo.pl
AMERICAN       2296    TUCSON            1615    1615    A7     ON TIME  
AMERICAN       408     SAN ANTONIO       2040    2040    A6     ON TIME  
AMERICAN       1086    BURBANK           2115    2115    A7     ON TIME  
AMERICAN       2530    ST. KITTS         2305    2305           ON TIME  
SOUTHWEST      514     NASHVILLE         1300    1320    E9     ARRIVED  
SOUTHWEST      580     CHICAGO-MDW       1335    1350    E15      135P   
SOUTHWEST      1512    CHICAGO-MDW       1420    1420    E12    ON TIME  
SOUTHWEST      1178    ST. LOUIS         1430    1430    E9     ON TIME  
SOUTHWEST      960     RALEIGH/DURHAM    1535    1535    E16    ON TIME  
SOUTHWEST      256     BALTIMORE         1610    1610    E9     ON TIME 

But the modifications I have made to the client example in getaddrinfo man pages hang with no response when I attempt to retrieve the same file from the server. Here is the code:

#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>

#define BUF_SIZE 500

int
main(int argc, char *argv[])
{
    struct addrinfo hints;
    struct addrinfo *result, *rp;
    int sfd, s, j, send;
    size_t len;
    ssize_t nread;
    char buf[BUF_SIZE];


    char req[] = "GET /cgi-bin/fidsarrival.pl HTTP/1.0\nACCEPT: */*\nUser-Agent: client/1.0\n";

    if (argc < 2) {
        fprintf(stderr, "Usage: %s host port...\n", argv[0]);
        exit(EXIT_FAILURE);
    }

    /* Obtain address(es) matching host/port */

    memset(&hints, 0, sizeof(struct addrinfo));
    hints.ai_family = AF_UNSPEC;    /* Allow IPv4 or IPv6 */
    hints.ai_socktype = SOCK_DGRAM; /* Datagram socket */
    hints.ai_flags = 0;
    hints.ai_protocol = 0;          /* Any protocol */

    s = getaddrinfo(argv[1], argv[2], &hints, &result);
    if (s != 0) {
        fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(s));
        exit(EXIT_FAILURE);
    }

    /* getaddrinfo() returns a list of address structures.
       Try each address until we successfully connect(2).
       If socket(2) (or connect(2)) fails, we (close the socket
       and) try the next address. */

    for (rp = result; rp != NULL; rp = rp->ai_next) {
        sfd = socket(rp->ai_family, rp->ai_socktype,
                     rp->ai_protocol);
        if (sfd == -1)
            continue;
        if (connect(sfd, rp->ai_addr, rp->ai_addrlen) != -1)

            break;                  /* Success */

        close(sfd);
     }

     if (rp == NULL) {               /* No address succeeded */
        fprintf(stderr, "Could not connect\n");
        exit(EXIT_FAILURE);
    }


    freeaddrinfo(result);           /* No longer needed */

    /* Send remaining command-line arguments as separate
        datagrams, and read responses from server */

    if ((send=write(sfd, req, strlen(req))) != strlen(req)) {
        fprintf(stderr, "partial/failed write\n");
        exit(EXIT_FAILURE);
    }

    printf("\nhttp request: \n%s\n%d bytes sent to server...\n",req,send);
    nread = read(sfd, buf, BUF_SIZE);

    if (nread == -1) {
        perror("read");
        exit(EXIT_FAILURE);
    }

    printf("Received %ld bytes: %s\n", (long) nread, buf);

    exit(EXIT_SUCCESS);
}

I am assuming that I am getting the syntax for writing to/reading from the server. The program just hangs after the call to 
read(sfd, buf, BUF_SIZE) near the end. I am running the program from the command line like this:

user@mybox-desktop:~/networkapps/src$ ./client 151.204.51.5 80

http request: 
GET /cgi-bin/fidsarrival.pl HTTP/1.0
ACCEPT: */*
User-Agent: client/1.0

72 bytes sent to server...

(program hangs here)

Could anyone give some clues about where I may be going wrong with my C program?

---

### Post by tjwilson1973 on 2011-05-08
One more thing: 151.204.51.5 is the ip address for [www.phl.org](www.phl.org).

---

### Post by johnl on 2011-05-08
Since you are contacting a web server, I suggest you set **hints.ai_socktype** to **SOCK_STREAM** (tcp) instead of **SOCK_DGRAM** (udp).

Secondly, I think you need an additional **\n** terminating your http request.

```

    char req[] = "GET /cgi-bin/fidsarrival.pl HTTP/1.0\nACCEPT: */*\nUser-Agent: client/1.0\n\n";

```

With these two changes, plus the following, it works for me.


To read all the data, you need to loop and read data until the socket is closed:

```

    printf("\nhttp request: \n%s\n%d bytes sent to server...\n",req,send);

    
    while((nread = recv(sfd, buf, BUF_SIZE - 1, 0)) > 0) {
        buf[nread] = '\0';
        printf("%s", buf);
    }
    
    close(sfd);
    exit(EXIT_SUCCESS);

```

---

### Post by SledgeHammer_999 on 2011-05-08
And also learn to put your code inside [code][/ code] tags. It makes it easiear for us to read.

I don't mean to be disrespectful, but is this the first time you use a forum in general?

---

### Post by tjwilson1973 on 2011-05-08
Thanks alot, Johnl and Sledgehammer. The code you posted did the trick. And yes, this is my first time posting in this forum, and I don't have much experience on forums in general. Thanks alot for the tip.

---

