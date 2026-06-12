---
title: "[SOLVED] Something's gone wrong with the c standard library..."
date: 2008-06-25
forum: Programming Talk
---

### Post by ByKeLaO on 2008-06-25
I'm trying to port a TCP-based server software that I wrote in Windows into Linux code. However, all of the Linux socket tutorials suggets that my copy of netinet/in.h is wrong. Specifically, my in.h contains:

```
struct sockaddr_in
  {
    __SOCKADDR_COMMON (sin_);
    in_port_t sin_port;			/* Port number.  */
    struct in_addr sin_addr;		/* Internet address.  */

    /* Pad to size of `struct sockaddr'.  */
    unsigned char sin_zero[sizeof (struct sockaddr) -
			   __SOCKADDR_COMMON_SIZE -
			   sizeof (in_port_t) -
			   sizeof (struct in_addr)];
  };
```

Whereas the tutorials suggest it should be:

```
struct sockaddr_in {
    u_char  sin_len;
    u_short sin_family;            // Address family
    u_short sin_port;               // Port number
    struct  in_addr sin_addr;  // Internet or IP address
    char    sin_zero[8];            // Same size as struct sockaddr
};
```

Why on earth are they different? Do I have the wrong version of the c library installed?

---

### Post by ByKeLaO on 2008-06-25
Turns out my auto completion was up the creek, not my c std library installation. Sorry folks :(

---

