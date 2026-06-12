---
title: "Need help with sockets"
date: 2005-04-29
forum: Programming Talk
---

### Post by verbena1 on 2005-04-29
I didn't know who to ask since my instructor isn't much help so here goes.  

I need some C/Unix networking help,

I'm working on a assignment in a unix environment that has two parts.
Part one implement a simple "shell" that parses a command and its arguments and then executes it, or if a pipe character is used ("|") parse the left side, parse the right side, and then manually pipe (using close() and dup()) and return this to a command line of my making (in my case my prompt is myShell> )

I have that done but now I need to implement it using networking. I have a client and a server and my setup is that the client connects to the server and the client prints out the prompt "myShell: " I can send a command and it works on the server end but I would like to know how to send the servers output of the command back to the client. I've looked around the internet and through my books (Richard Stevens Unix Networking book) and I can't find a way to do this unless I'm just missing something. I thought about maybe using dup() to make a copy of the input-send to the server-run my parse and execute functions-copy the output and send to to the client but I don't know how to do this. If I can send out this output is there a way to send my "myShell:" prompt directly from the server and save my client the trouble?

I'm not sure on the syntax though,

I know that in client its called sockfd, and in server newsockfd.
and this is where my server executes code after a connection:
```

for (;;) {

		/* accept a connection */

		if ( (newsockfd = accept(sockfd, NULL, NULL)) == -1) {

			perror("accept call failed");

			continue;

		}



		/* spawn a child to deal with the connection */

		if (fork() == 0) {

			while (recv(newsockfd, buf, MAXLINE, 0) > 0) {

				parse(buf, args1, args2);

				execute(args1, args2);

				send(newsockfd, buf, MAXLINE, 0);

			}

			/* when client is no longer sending information

			the socket can be closed and the child process

			terminated */

			close(newsockfd);

			exit (0);

		}



		/* parent doesn't need the newsockfd */

		close (newsockfd) ;

	}
```

Any help would be appreciated

---

### Post by Xerampelinae on 2005-04-29
It's been a couple of years since I've written a program like this, so I may be rusty but...

You have | working right?  So you can say

```

command1 | command2

```

And the above re-directs the output of command1 into the input of command2.  So why not do something similar with the networking... read the output from command1, and send it over the socket.

In fact, the design I would have considered first would be using a dumb client and building everything on the server.  I would probably code the server up first, based upon a modified version of the local shell, and just test it using standard telnet.  Then, once the server works it's easy to implement your own telnet client.

---

### Post by verbena1 on 2005-04-29
I thought about that, I have pipe implemented in my shell but I don't know how to send it back and forth.  
right now I can send and recieve text using these funtions:

(on the server)
recv(newsockfd, buf, MAXLINE, 0);
send(newsockfd, buf, MAXLINE, 0);

(on the client)
send (sockfd, buf, MAXLINE, 0);
recv(sockfd, buf, MAXLINE, 0);

This is what my pipe section looks like: (0 is standard input, 1 is standard out)

```
/* function joins argument array's to handle pipes */
int join(char **args1, char **args2)
{
    int p[2], status;
    switch (fork()) {
    case -1:
	perror( "fork" );
    case 0:
	break; //Child
    default:
	wait(&status);
	return (status);
    };

    if (pipe(p) < 0)
	perror( "pipe" );

    switch (fork()) {
    case -1:
	perror( "fork" );
    case 0:
	close(1);
	dup(p[1]);
	close(p[0]);
	signal(SIGALRM, catch);
	alarm(SECONDS);
	execvp(*args1, args1);
	perror(*args1);
	break;
    default:
	close(0);
	dup(p[0]);
	close(p[1]);
	signal(SIGALRM, catch);
	alarm(SECONDS);
	execvp(*args2, args2);
	perror(*args2);
    };
}
```

I have no idea how to send this output back and forth.

---

### Post by Xerampelinae on 2005-04-29
I'm sorry, but I think this code has a lot of problems...  I'll point out the things that struck me as odd.  On the other hand, maybe it makes sense and I've just been away from this stuff for too long...

```

/* function joins argument array's to handle pipes */
int join(char **args1, char **args2)
{
    int p[2], status;

// What's the point of forking here?  Why do you need to fork twice?
    switch (fork()) {
    case -1:
	perror( "fork" );
    case 0:
	break; //Child
    default:
	wait(&status); // does status even have a meaningful value?
	return (status);
    };

    if (pipe(p) < 0)
	perror( "pipe" );

// maybe I'm wrong, but don't you use dup() here, before you fork() ?

    switch (fork()) {
    case -1:
	perror( "fork" );
    case 0:
	close(1);
	dup(p[1]); // wait, what is the point of this..?
	close(p[0]);
	signal(SIGALRM, catch);
	alarm(SECONDS);
	execvp(*args1, args1);
	perror(*args1);
	break;
    default:
	close(0);
	dup(p[0]); // ?
	close(p[1]);
	signal(SIGALRM, catch);
	alarm(SECONDS);
	execvp(*args2, args2);
	perror(*args2);
    };
}

```

Anyway, I think the thing you're missing for sockets is the read() function, which can read from a file descriptor into an array.  Then you can send that array of data.

man read

---

