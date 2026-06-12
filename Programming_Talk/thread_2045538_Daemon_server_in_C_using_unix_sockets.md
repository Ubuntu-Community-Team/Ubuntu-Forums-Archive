---
title: "Daemon server in C using unix sockets"
date: 2012-08-21
forum: Programming Talk
---

### Post by IAMTubby on 2012-08-21
Hi, 
I am trying to implement a daemon server in c. I'm almost there and get the correct output when I execute the server and client.

But when I execute the same client again, it says. connect : connection refused.

I tried using both daemon(0,0) as well as the daemonize() function(check code) for daemonizing.

Thanks.

Below is the source code of the daemon server. I think I'm missing out on some routine to get it work the next time. Why else would the same client, not give the output second time ?

```

#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <string.h>
#include <stdlib.h>
#include <errno.h>
#include <unistd.h>

#define MYPORT 			atoi(argv[1])
#define MESSAGE_SIZE 		50
#define BACKLOG			1 // No. of pending connections you are willing to handle.

#define EXIT_SUCCESS 0
#define EXIT_FAILURE 1

FILE* fpLog;
FILE* fpDate;

int sockfd, newfd, ret_bind, theiraddr_size, recv_bytes, send_bytes, yes = 1, i = 0;
struct sockaddr_in myaddr, theiraddr;
char* msg;
char c;

static void daemonize(void)
{
    pid_t pid, sid;

    /* already a daemon */
    if ( getppid() == 1 ) return;

    /* Fork off the parent process */
    pid = fork();
    if (pid < 0) {
        exit(EXIT_FAILURE);
    }
    /* If we got a good PID, then we can exit the parent process. */
    if (pid > 0) {
        exit(EXIT_SUCCESS);
    }

    /* At this point we are executing as the child process */

    /* Change the file mode mask */
    umask(0);

    /* Create a new SID for the child process */
    sid = setsid();
    if (sid < 0) {
        exit(EXIT_FAILURE);
    }

    /* Change the current working directory.  This prevents the current
       directory from being locked; hence not being able to remove it. */
    if ((chdir("/")) < 0) {
        exit(EXIT_FAILURE);
    }

    /* Redirect standard files to /dev/null */
    freopen( "/dev/null", "r", stdin);
    freopen( "/dev/null", "w", stdout);
    freopen( "/dev/null", "w", stderr);
}

int main(int argc, char *argv[])
{
        //daemon(0,0); 
        daemonize();
    	//while(1) sleep(1);

	/* Allocating memory */
	msg = malloc(200 * sizeof(char));

        fpLog = fopen("/home/DebugLog.txt","a");
       
	if(argc != 2) 
        {
		fprintf(fpLog,"\nUsage: <executable> <server_port_number>\n");
		exit(1);
	}


/* ------------------- Initialize connection ------------------*/

	/* Get a socket file descriptor */
        sockfd = socket(PF_INET, SOCK_STREAM, 0);

	if(sockfd == -1)
		perror("socket");

	/* Enable reuse of the port number immediately after program
	 * termination.
	*/
	if(setsockopt(sockfd, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int)) == -1)
		perror("setsockopt");

	
	myaddr.sin_family = AF_INET; 				/* Host byte order */
	myaddr.sin_port = htons(MYPORT);			/* Network byte order */
	myaddr.sin_addr.s_addr = htonl(INADDR_ANY); 		/* Get my IP address */
	memset(&(myaddr.sin_zero), '\0', 8); 			/* Zero it out */
		
	/* Bind it to your IP address and a suitable port number. */
	ret_bind = bind(sockfd, (struct sockaddr *)&myaddr, sizeof(struct sockaddr));
	
	if(ret_bind == -1)
		perror("bind");
        else fprintf(fpLog,"\nbind() worked fine "); 
		
		
		
	/* Try listening to incoming connection requests.
	 * And set a limit on the size of the connection queue.
	 */
	if(listen(sockfd, BACKLOG) == -1)
		perror("listen");
	
	
	theiraddr_size = sizeof(struct sockaddr_in);
	
		
	/* Accept the incoming connection request. */
	newfd = accept(sockfd, (struct sockaddr *)&theiraddr, &theiraddr_size);

	if(newfd == -1)
		perror("accept");
        else
         fprintf(fpLog,"\nThe connection has been accepted ");	
	
	
	
	/* If you want only one connection, close sockfd. */
	close(sockfd);
	
/* ------------ End of connection initialization ------------- */


/* --------------------- Start communicating ------------------ */
	
	/* You expect the client to send you something first. */
	recv_bytes = recv(newfd, (void *)msg, sizeof(msg), 0);
	
        fprintf(fpLog,"\nUnfortunately, this might be the last fprintf ");
	if(recv_bytes != -1) 
        {
		if(recv_bytes > 0) 
                {
			msg[recv_bytes] = '\0';
			fprintf(fpLog,"\nThe message received from the client is: %s\n", msg);
			fprintf(fpLog,"recv_bytes = %d",recv_bytes);
		} 
                else if (recv_bytes == 0)
                {
			fprintf(fpLog,"\nThe client closed the connection!\n");	
			fclose(fpLog);
 			fprintf(fpLog,"recv_bytes = %d",recv_bytes);
		}
	} 
	else 
		perror("recv");	
        /* THIS WAS THE END OF THE RECEIVING PART */




	/* SENDING PART */
	fprintf(fpLog,"\n\n\nBeginning of the code - simple send of string");
        msg = malloc(200 * sizeof(char));
	system("date > /home/aftab_hassan/AllExperiments/Daemon/DateOutput.txt");
        
	fpDate = fopen("/home/DateOutput.txt","r");
        while(1)
        {
         c = getc(fpDate);

         if(c == EOF)
	 {
           *(msg + i) = '\0';
	   break;	
	 }

         *(msg + i++) = c;
        }
	fclose(fpDate);

        send_bytes = send(newfd, (void*)msg, strlen(msg), 0);
        fprintf(fpLog,"\nMessage sent to client : [%s]",msg);
        fprintf(fpLog,"\nNumber of bytes sent = %d",send_bytes);

	

	
/* ---------------- Release all resources ----------------- */
	
	close(newfd);		
        fclose(fpLog);	
	return 0;
}

```

---

### Post by matt_symes on 2012-08-21
Thread move to "Programming Talk"

---

### Post by dwhitney67 on 2012-08-21
> **IAMTubby said:**
> Why else would the same client, not give the output second time ?


Because of this:
```

...

	/* If you want only one connection, close sockfd. */
	close(sockfd);

...

```
Once the initial client connects, the socket is closed, thus denying other clients the opportunity to connect.

---

### Post by IAMTubby on 2012-08-22
Thanks for that. I'm still having problems. 
I made the code simpler and removed the business logic.

Server Code - On commenting out the daemon(0,0) everything works fine on both client side as well as server side. But with daemon(0,0) it gives me a connect error on client side.
```
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/un.h>

#define SOCK_PATH "echo_socket"

int main(void)
{
    /* This is the line causing all the problem. Commenting out this makes the code run fine */
    daemon(0,0);

    int s, s2, t, len;
    struct sockaddr_un local, remote;
    char str[100];

    if ((s = socket(AF_UNIX, SOCK_STREAM, 0)) == -1) {
        perror("socket");
        exit(1);
    }

    local.sun_family = AF_UNIX;
    strcpy(local.sun_path, SOCK_PATH);
    unlink(local.sun_path);
    len = strlen(local.sun_path) + sizeof(local.sun_family);
    if (bind(s, (struct sockaddr *)&local, len) == -1) {
        perror("bind");
        exit(1);
    }

    if (listen(s, 5) == -1) {
        perror("listen");
        exit(1);
    }

    for(;;) {
        int done, n;
        printf("Waiting for a connection...\n");
        t = sizeof(remote);
        if ((s2 = accept(s, (struct sockaddr *)&remote, &t)) == -1) {
            perror("accept");
            exit(1);
        }

        printf("Connected.\n");

        done = 0;
        do {
            n = recv(s2, str, 100, 0);
            if (n <= 0) {
                if (n < 0) perror("recv");
                done = 1;
            }

            if (!done) 
                if (send(s2, str, n, 0) < 0) {
                    perror("send");
                    done = 1;
                }
        } while (!done);

        close(s2);
    }

    return 0;
}
```


Client side
```

#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/un.h>

#define SOCK_PATH "echo_socket"

int main(void)
{
    int s, t, len;
    struct sockaddr_un remote;
    char str[100];

    if ((s = socket(AF_UNIX, SOCK_STREAM, 0)) == -1) {
        perror("socket");
        exit(1);
    }

    printf("Trying to connect...\n");

    remote.sun_family = AF_UNIX;
    strcpy(remote.sun_path, SOCK_PATH);
    len = strlen(remote.sun_path) + sizeof(remote.sun_family);
    if (connect(s, (struct sockaddr *)&remote, len) == -1) {
        perror("connect");
        exit(1);
    }

    printf("Connected.\n");

    while(printf("> "), fgets(str, 100, stdin), !feof(stdin)) {
        if (send(s, str, strlen(str), 0) == -1) {
            perror("send");
            exit(1);
        }

        if ((t=recv(s, str, 100, 0)) > 0) {
            str[t] = '\0';
            printf("echo> %s", str);
        } else {
            if (t < 0) perror("recv");
            else printf("Server closed connection\n");
            exit(1);
        }
    }

    close(s);

    return 0;
}

```

---

### Post by IAMTubby on 2012-08-23
I got it to work. :)
My daemonizing function had some problem. Instead of using daemon(0,0), I copy pasted the steps for daemonizing a process into a function. It now works correctly.


Thanks for the replies.
Please mark the thread as solved.

---

### Post by IAMTubby on 2012-08-23
However, I have a couple of doubts regarding daemons

1)What advantage does a daemon provide over a normal server program running on the terminal. (Asking cuz I had to break my head for some time for this).

2)How long does a daemon run ? Does a daemon server run forever ?

3)After running the daemon server, when I do a ps, why doesn't it show me the daemon running ? I still get only bash and ps.

Thanks

---

### Post by Wim Sturkenboom on 2012-08-23
> **IAMTubby said:**
> Please mark the thread as solved.
You can do that yourself using the thread tools just above the first post on a page :)

---

### Post by IAMTubby on 2012-08-23
Sorry Wim, didn't notice that . Have marked as solved.

---

### Post by Wim Sturkenboom on 2012-08-23
No apology needed.

---

