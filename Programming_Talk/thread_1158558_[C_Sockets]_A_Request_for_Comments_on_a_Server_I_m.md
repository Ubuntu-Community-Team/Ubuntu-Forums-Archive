---
title: "[C Sockets] A Request for Comments on a Server I made"
date: 2009-05-13
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-05-13
Well I was board the other day, and thought it was worth it to learn the C Socket API

I hacked up a quick little server that basically grabs the output of the fortune program and sends it to the connected client.  It then terminates the connection.

simpley run the program and telnet to it.

any comments on it, socket wise?

[php]
/*
      This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

 */

#include <stdio.h>
#include <sys/types.h> 
#include <sys/socket.h>
#include <netinet/in.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>

char* getFortune()
{
  char* content;
  FILE* f;

  content = malloc(1024*sizeof(char)*2);
  f = popen("fortune -n 2047 -s", "r");
  fread(content, sizeof(char), 2047, f);
  pclose(f);

  return content;
}

void die(const char* msg, int exitCode)
{
  fputs(msg, stderr);
  exit(exitCode);
}

int main(int argc, char** argv)
{
  int sockfd, newfd, portnum, clientlen;
  struct sockaddr_in servaddr,cliaddr;
  unsigned long fortunes;

  if (argc < 2)
  {
    die("Usage: fortuneserv <port>", 1);
  }

  portnum = atoi(argv[1]);
  sockfd = socket(AF_INET, SOCK_STREAM, 0);

  if (sockfd < 2)
    die("Error opening socket!", 2);

  servaddr.sin_family = AF_INET;
  servaddr.sin_addr.s_addr = INADDR_ANY;
  servaddr.sin_port = htons(portnum);

  if (bind(sockfd, (struct sockaddr *) &servaddr,
       sizeof(servaddr)) < 0)
    die("Error binding to the socket", 3);
  
  listen(sockfd, 5);
  clientlen = sizeof(cliaddr);

  while (1)
  {
    char* fortune;
    int n, totalSent;

    totalSent = 0;
    
    newfd = accept(sockfd,
           (struct sockaddr*) &cliaddr,
           &clientlen);

    fortune = getFortune();

    while (totalSent < strlen(fortune)*sizeof(char))
    {
      n = write(newfd, fortune, strlen(fortune));
      if (n < 0)
    die("Error writting to socket", 4);
      fsync(newfd);
      totalSent += sizeof(char)*n;
    }
    
    close(newfd);
    fortunes++;
    printf("Told %ld successful fortunes\n", fortunes);
  }
  
  return 0;
}
[/php]

i put it under AGPL because i am a paranoid little coder

thanks

---

### Post by dwhitney67 on 2009-05-13
The contents of this loop are incorrect:
```

while (totalSent < strlen(fortune)*sizeof(char))
{
  n = write(newfd, fortune, strlen(fortune));
  if (n < 0)
    die("Error writting to socket", 4);
  fsync(newfd);
  totalSent += sizeof(char)*n;
}

```
Also, fsync() is not required (ie not applicable to sockets).  Did you know that sizeof(char) is 1; what's the point of multiplying by one at every opportunity you get?  Anyhow, the issue with the loop is that you do not update the pointer position of 'fortune' with each successive write, nor do you reduce the number of characters to be sent.

Try
```

n = write(newfd, fortune + totalSent, strlen(fortune) - totalSent);

```

This variable is never initialized prior to this operation:
```

unsigned long fortunes;
...
fortunes++;

```

Avoid hard-coding numbers in your code:
```

content = malloc(1024*sizeof(char)*2);
f = popen("fortune -n 2047 -s", "r");
fread(content, sizeof(char), 2047, f);

```

---

### Post by dwhitney67 on 2009-05-13
> **jimi_hendrix said:**
> ...
i put it under AGPL because i am a paranoid little coder


The license is great for full projects that are "worth" something or for examples that belong to a package.  Little demo exercises, such as you provided, do not need the AGPL.  I really do not think anyone is going to steal your idea for any commercial application.

---

### Post by jimi_hendrix on 2009-05-14
ok ty

---

### Post by dsterry on 2009-08-05
In reference to the reasons to use AGPL, the purpose of this license is not to protect the developer but to protect users' freedoms. It's a great license if you want to encourage other developers who also value the user's freedom to study, modify, and share the network-enabled program you are creating. It's true, it might not be necessary for small programs but every program starts small so good on ya.

---

### Post by Can+~ on 2009-08-05
> **dsterry said:**
> In reference to the reasons to use AGPL, the purpose of this license is not to protect the developer but to protect users' freedoms. It's a great license if you want to encourage other developers who also value the user's freedom to study, modify, and share the network-enabled program you are creating. It's true, it might not be necessary for small programs but every program starts small so good on ya.

Why can't people look at the dates before posting?

---

