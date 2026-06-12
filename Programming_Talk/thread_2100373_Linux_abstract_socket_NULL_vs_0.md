---
title: "Linux abstract socket: NULL vs \0"
date: 2013-01-01
forum: Programming Talk
---

### Post by bird1500 on 2013-01-01
Hi,

I create a Linux abstract socket this way:
[PHP]
static const char *UFBIO_LISTEN_PATH = "/ufbio/port";
...
struct sockaddr_un addr;
memset(&addr, 0, sizeof(struct sockaddr_un));
addr.sun_family = AF_UNIX;
strncpy(&addr.sun_path[1], UFBIO_LISTEN_PATH, sizeof(addr.sun_path)-2);
int sockfd = socket(AF_UNIX, SOCK_STREAM, 0);
...
//bind(socket...) works fine
[/PHP]and bind() works fine (doesn't collide with sockets from other apps, read below).
But when I make the path start with zero directly:
[PHP]
static const char *UFBIO_LISTEN_PATH = "\0/ufbio/port";
...
strncpy(addr.sun_path, UFBIO_LISTEN_PATH, sizeof(addr.sun_path)-1);

...//bind(socket...)
[/PHP]I get an error "address already in use" during bind() if any other app is running with a socket created this way (even with a different path like "\0another/app/port").

What am I doing wrong with this second approach? Is it the path? - Doesn't the first byte result in zero in both cases? - '\0' and memset(.., 0, ..)

---

### Post by Bachstelze on 2013-01-01
This

```
 static const char *UFBIO_LISTEN_PATH = "\0/ufbio/port";
```

is the empty string. When you do strncpy(), only the leading 0 byte is written, nothing else.

---

### Post by bird1500 on 2013-01-01
That's a neat subtle catch, thanks!

---

