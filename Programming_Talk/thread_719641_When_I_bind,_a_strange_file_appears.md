---
title: "When I bind, a strange file appears"
date: 2008-03-09
forum: Programming Talk
---

### Post by Fixman on 2008-03-09
I got the following code (in C)

```

#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/un.h>
#include <assert.h>
#include <unistd.h>
#include <netinet/in.h>
#include <arpa/inet.h>

#define try(n) if ((n) == -1) kill (#n"\n") ;
#define kill(n) {perror (n) ; exit(1) ;}

int s, l ;

void die()
{
	getchar() ;
}

int main()
{
	struct sockaddr_in loc, rem ;
	int len ;
	
	atexit (die) ;
	
	s = socket (AF_UNIX, SOCK_STREAM, 0) ;
	
	loc.sin_family = AF_UNIX ;
	loc.sin_port = 0 ;
	loc.sin_addr.s_addr = INADDR_ANY ;
	memset (loc.sin_zero, 0, sizeof loc.sin_zero) ;
	
	const int yes = 1 ;
	
	try (setsockopt(s, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int)) == -1) ;
	
	try (bind (s, (struct sockaddr *) &loc, sizeof loc.sin_zero)) ;
	try (listen(s, 5)) ;
	
	puts ("Waiting for connection...") ;
	
	len = sizeof (struct sockaddr_un) ;
	try ( l = accept (s, (struct sockaddr *)&rem, (socklen_t *)&len) ); 
	puts ("hola") ;
	
	printf ("Connection received from %s", inet_ntoa (rem.sin_addr) ) ;
	
	while (1) 
	{
		char str[100] ;
		if (recv (l, str, 100, 0) == 0) break ;
		puts (str) ;
	}
	
	close (l) ;
	close (s) ;
	
	puts ("All OK!") ;
	return 0 ;
}


```

However, when I run the code, a strange file appears on the same folder. Does someone know what is the problem?

I post you the screenshot of the image.

[[IMG]http://img139.imageshack.us/img139/4237/holapu2.jpg[/IMG]](http://imageshack.us)

---

### Post by ruy_lopez on 2008-03-09
I usually pass the sizeof the struct sockaddr_in, as  the third argument to bind().

```

bind(listenfd, (struct sockaddr *) &servaddr, sizeof(servaddr));

```

No idea if this'll fix it.

---

### Post by Fixman on 2008-03-09
> **ruy_lopez said:**
> I usually pass the sizeof the struct sockaddr_in, as  the third argument to bind().

```

bind(listenfd, (struct sockaddr *) &servaddr, sizeof(servaddr));

```

No idea if this'll fix it.

Yes it does, so thanks a lot.

---

