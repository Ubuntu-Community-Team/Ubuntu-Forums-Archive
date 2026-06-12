---
title: "Problem reverse lookup code"
date: 2010-08-27
forum: Programming Talk
---

### Post by piyush.neo on 2010-08-27
i have recently started socket programming.
Can't figure out why it is not working..
```
#include   <stdio.h>
#include   <string.h>
#include   <sys/types.h>
#include   <sys/socket.h>
#include   <netdb.h>
#include   <arpa/inet.h>
int main()
{
    struct sockaddr_in sa;
    memset(&sa,0,sizeof(sa));
    inet_pton(AF_INET,"172.31.100.29",&sa.sin_addr);
    char hname[NI_MAXHOST],sname[NI_MAXSERV];
    if(getnameinfo((struct sockaddr *)&sa,sizeof(sa),hname,sizeof(hname),NULL,0,0))
    printf("could not reslove");
    else
    printf("%s",hname);
}

``````
piyush@piyush-laptop:~/codes/networkcode$ cc try.c
piyush@piyush-laptop:~/codes/networkcode$ ./a.out
could not reslove
```
Althoughthe command** host 172.31.100.29** is returning the hostname .

---

### Post by Bachstelze on 2010-08-27
1) The Space Bar. Use it.

2) Error codes. Use them. This will tell you what's wrong:

```
#include <stdio.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>
#include <arpa/inet.h>

int main(void)
{
    struct sockaddr_in sa;
    char hname[NI_MAXHOST], sname[NI_MAXSERV];
    int ret;

    memset(&sa, 0, sizeof(sa));
    inet_pton(AF_INET, "172.31.100.29", &sa.sin_addr);
    if(ret = getnameinfo((struct sockaddr *) &sa, sizeof(sa), hname, sizeof(hname), NULL, 0, 0))
        fprintf(stderr, "Error: %s\n", gai_strerror(ret));
    else
        printf("%s\n", hname);
}

```

---

### Post by piyush.neo on 2010-08-27
piyush@piyush-laptop:~/codes/networkcode$ ./a.out
Error: ai_family not supported

i changed AF_INET to PF_INET  but still....
though ai_family was working fine for other codes as namelookup...

---

### Post by Bachstelze on 2010-08-27
Your problem is that you are not specifying in your sockaddr which ai_family you use. You need something like

```
sa.sin_family = AF_INET;
```

---

### Post by piyush.neo on 2010-08-27
Thanks..working fine now....:)

---

