---
title: "[SOLVED] C, &amp;quot;client.c:36:34: warning: multi-character character constant&amp;quot; and error c"
date: 2008-02-28
forum: Programming Talk
---

### Post by tehet on 2008-02-28
Hi,

First question:
Compiling the code below, either with or without -Wall, I get the following warning:
```
$ gcc -Wall client.c -o client
client.c:36:34: warning: multi-character character constant
```
I've marked out line 36 in the code. Apparently gcc has issues with '/0' but after looking at man memset() I don't see the problem (though it compiles and runs). Replacing with 'NULL' gives the same warning and replacing with NULL gives
```
client.c:36: warning: passing argument 2 of &#8216;memset&#8217; makes integer from pointer without a cast
```
:confused:
What's happening here? (Or) is it a harmless warning that can be ignored?

Second question:
How come the error check precedes printf("Connecting ...");? e.g. (there's no server yet so that's why it fails)
```
$ ./client
Enter server IP:
10.1.1.1
Enter port number:
9999
Creating socket ... succeeded.
failed. : Connection refused
Connecting to remote socket ...
```
Thanks.

```
/*
	client.c
	Socket exercise - Stream client
	Mostly lifted from
http://beej.us/guide/bgnet/output/html/multipage/index.html
*/

#include <stdio.h> /* printf, scanf, etc */
#include <stdlib.h> /* ? */
#include <string.h> /* memset() */
#include <sys/types.h> /* socket(), connect(), etc */
#include <sys/socket.h> /* socket(), connect(), etc */
#include <netinet/in.h> /* inet_addr() */
#include <arpa/inet.h> /* inet_addr() */
#include <errno.h> /* perror() */

int main()
{
	int sockfd;
	struct sockaddr_in server_address;
	char *server_ip;
	unsigned short int server_port;

	printf("Enter server IP:\n");
	scanf("%s", server_ip);
	printf("Enter port number:\n");
	scanf("%hu", &server_port);

	printf("Creating socket ... ");
	if ((sockfd = socket(PF_INET, SOCK_STREAM, 0)) == -1) {
	perror("failed. ");
	exit(1);
	}
	else printf("succeeded.\n");

	server_address.sin_family = AF_INET;
	server_address.sin_port = htons(server_port);
	server_address.sin_addr.s_addr = inet_addr(server_ip);
	memset(server_address.sin_zero, '/0', sizeof server_address.sin_zero); /* = line 36 = */

	printf("Connecting to remote socket ... ");
	if ((connect(sockfd, (struct sockaddr *)&server_address, sizeof server_address)) == -1) {
	perror("failed. ");
	exit(1);
	}
	else printf("succeeded.\n");

	return 0;
}
```

---

### Post by the_unforgiven on 2008-02-28
It should be '\0' (or simply 0) - and not '/0' in memset() call.
You could use [bzero()]("http://linux.die.net/man/3/bzero") as well; however it's marked as deprecated.

---

### Post by tehet on 2008-02-28
> **the_unforgiven said:**
> It should be '\0'
DOH! :lolflag:
Thanks!
> (or simply 0)
I'm still a bit confused as to when 0 is zero and when it's NULL.

---

### Post by the_unforgiven on 2008-02-28
> **tehet said:**
> DOH! :lolflag:
Thanks!

I'm still a bit confused as to when 0 is zero and when it's NULL.
Well, generally, NULL is treated more like (void*)0

In fact, this is what I have on my system (Kubuntu Gutsy) in /usr/include/linux/stddef.h:
```

#undef NULL
#if defined(__cplusplus)
#define NULL 0
#else
#define NULL ((void *)0)
#endif

```
So, you generally use NULL wherever you need pointer arithmetic (read pointer comparison), you use 0 in normal integer/char accesses.

HTH ;)

---

### Post by tehet on 2008-02-28
If I put fflush in there it works as expected:
```
        printf("Connecting to remote socket ... ");
        fflush('\0');
        if ((connect(sockfd, (struct sockaddr *)&server_address, sizeof server_address)) == -1) {
        perror("failed. ");
```
Standard out must be slower than standard error or something like that.

---

### Post by the_unforgiven on 2008-02-29
> **tehet said:**
> If I put fflush in there it works as expected:
```
        printf("Connecting to remote socket ... ");
        fflush('\0');
        if ((connect(sockfd, (struct sockaddr *)&server_address, sizeof server_address)) == -1) {
        perror("failed. ");
```
Standard out must be slower than standard error or something like that.
fflush('\0') is confusing - if not incorrect.
If you want to flush stdin, you should use fflush(stdin) - not '\0'.

Check up [fflush(3)]("http://linux.die.net/man/3/fflush") man page.

As far as slowness of stdout is concerned (wrt stderr), stdout is a buffered stream whereas stderr is unbuffered.
Translation: you won't get output on stdout unless explicitly flushed either with '\n', or fflush(stdout) call - till then, it's stored in a buffer in the process address space.

The reason for keeping stderr unbuffered is stderr is generally used to display error messages which should reach the user ASAP and should not be held back due to buffering issues. However, that's suboptimal because that means every single call to fprintf() will directly result in a write() system call invoking the kernel - which is an expensive operation.

I hope this makes it a bit clearer to you now :)

---

### Post by tehet on 2008-02-29
> **the_unforgiven said:**
> I hope this makes it a bit clearer to you now :)
Yes it does :D I thought \n was just newline, but it also flushes all the stuff you've been printf-ing to a stdout buffer.
Though I think you meant to say fflush(stdout), which works. fflush(stdin) doesn't. Anywho, thanks for your support, it's much appreciated!
I think I'll try to make the server now.

---

