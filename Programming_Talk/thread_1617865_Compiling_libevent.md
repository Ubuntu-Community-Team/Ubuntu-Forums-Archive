---
title: "Compiling libevent"
date: 2010-11-09
forum: Programming Talk
---

### Post by MechWarrior001 on 2010-11-09
Hello, long time no see (again)

I need to compile a libevent *.lib for a custom Minecraft server executable, but I'm not sure how to do it under MS VC++ 2010 Express. I have tried creating a empty project and adding in all the source files to it but regardless I still get a slew of errors. Perhaps I'm missing a dependency or two?

---

### Post by DangerOnTheRanger on 2010-11-10
It would help if you specified the actual errors. Nobody likes playing Twenty Questions! :)
Also, you're *probably* not going to get a response(except from me), seeing as how MSVC++ is Windows-only, and this is a Linux forum...

Still, you never know...

---

### Post by MechWarrior001 on 2010-11-11
Well, I decided to start from scratch and reload the project & code from the archive, and so far it compiles pretty cleanly except for a couple errors in http.c and ws2def.h.

```

f:\documents and settings\<user>\my documents\visual studio 2010\projects\libevent\http.c(102): warning C4005: 'NI_NUMERICHOST' : macro redefinition
          
f:\program files\microsoft sdks\windows\v7.0a\include\ws2def.h(953) : see previous definition of 'NI_NUMERICHOST'

f:\documents and settings\<user>\my documents\visual studio 2010\projects\libevent\http.c(103): warning C4005: 'NI_NUMERICSERV' : macro redefinition
        
f:\program files\microsoft sdks\windows\v7.0a\include\ws2def.h(955) : see previous definition of 'NI_NUMERICSERV'

f:\documents and settings\<user>\my documents\visual studio 2010\projects\libevent\http.c(145): error C2011: 'addrinfo' : 'struct' type redefinition
        
f:\program files\microsoft sdks\windows\v7.0a\include\ws2def.h(841) : see declaration of 'addrinfo'
```

http.c:
```

#define NI_NUMERICHOST 1
#define NI_NUMERICSERV 2

```

```

struct addrinfo {
    int ai_family;
    int ai_socktype;
    int ai_protocol;
    size_t ai_addrlen;
    struct sockaddr *ai_addr;
    struct addrinfo *ai_next;
};
```

ws2def.h:
```

#define NI_NUMERICHOST  0x02  /* Return numeric form of the host's address */
#define NI_NUMERICSERV  0x08  /* Return numeric form of the service (port #) */

```

```

{
    int                 ai_flags;       // AI_PASSIVE, AI_CANONNAME, AI_NUMERICHOST
    int                 ai_family;      // PF_xxx
    int                 ai_socktype;    // SOCK_xxx
    int                 ai_protocol;    // 0 or IPPROTO_xxx for IPv4 and IPv6
    size_t              ai_addrlen;     // Length of ai_addr
    char *              ai_canonname;   // Canonical name for nodename
    __field_bcount(ai_addrlen) struct sockaddr *   ai_addr;        // Binary address
    struct addrinfo *   ai_next;        // Next structure in linked list
}

```

Perhaps I'm missing some dependencies?

---

