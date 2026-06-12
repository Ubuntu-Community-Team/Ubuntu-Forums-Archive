---
title: "Sockets in C"
date: 2011-09-29
forum: Programming Talk
---

### Post by Barrucadu on 2011-09-29
I'm failing to understand sockets in C. Basically, I am writing a P2P file transfer program, I have got the server part working, but the client part eludes me.

Here is the code in question:
```
/**                                                                                                                                                                                                                                                                               
 * Send a message and get the response                                                                                                                                                                                                                                            
 */
message_t *
protocol_dialogue (peer_t *peer, message_t *message)
{
  int sock;
  struct sockaddr_in *address = xalloc (struct sockaddr_in);
  message_t *out;

  /* Open connection */
  sock = socket (AF_INET, SOCK_STREAM, 0);
  if (sock < 0)
    {
      printf ("Sockfail\n");
      return NULL;
    }

  address->sin_family      = AF_INET;
  address->sin_addr.s_addr = inet_addr (peer->ip);                                                                                                                                                                                                                            
  address->sin_port        = htons (peer->port);

  if (connect (sock, (struct sockaddr *) address, sizeof(address)) < 0)
    {
      printf ("Connectfail\n");
      return NULL;
    }

  /* Send message */
  protocol_send_message (sock, message);

  /* Get response */
  out = protocol_recv_message (sock);

  /* Tidy and return */
  close (sock);
  xfree (address);

  return out;
}

```

It always fails with "Connectfail" - even if I hard-code the IP address and port in, so it's not my peer_t struct that's failing.
The server part is definitely working, as I can telnet in and interact with it.

In case it may be relevant, xalloc is a macro+function which allocates and zeroes some memory with calloc, and then asserts that it has been allocated. xfree, similarly frees a pointer and sets it to NULL.

---

### Post by karlson on 2011-09-29
> **Barrucadu said:**
> IHere is the code in question:
```
/**                                                                                                                                                                                                                                                                               
 * Send a message and get the response                                                                                                                                                                                                                                            
 */
message_t *
protocol_dialogue (peer_t *peer, message_t *message)
{
  struct sockaddr_in *address = xalloc (struct sockaddr_in);
  message_t *out;
<yada yada yada>

  if (connect (sock, (struct sockaddr *) address, sizeof(address)) < 0)
<blah blah blah>
}

```


First off.  When you take 
```

sizeof(address)

```

it is a size of the pointer not the size of memory allocated for the struct.

Second.  Why use xalloc and xfree at all?  Just do:
```

struct sockaddr_in address;
memset(&address, 0, sizeof(address));

```
if you so desire to initialize it to 0s.  Makes code simpler and makes the compiler do the lifting in allocation of memory and cleanup.

---

### Post by Bachstelze on 2011-09-29
Also...

> **Barrucadu said:**
> 
It always fails with "Connectfail"


Use errno to get a more informative error message (see for example the function perror()).

---

### Post by karlson on 2011-09-29
> **Bachstelze said:**
> Also...



Use errno to get a more informative error message (see for example the function perror()).

+1.:p

---

### Post by Barrucadu on 2011-09-29
Indeed, it was my use of pointers that caused the problem. I'm not sure I was even using a pointer there, working code:

```
/**                                                                                                                                                                                                                                                                               
 * Send a message and get the response                                                                                                                                                                                                                                            
 */
message_t *
protocol_dialogue (peer_t *peer, message_t *message)
{
  int sock;
  struct sockaddr_in address;
  message_t *out;

  assert (peer    != NULL);
  assert (message != NULL);

  /* Open connection */
  sock = socket (AF_INET, SOCK_STREAM, 0);
  if (sock < 0)
    return NULL;

  memset (&address, 0, sizeof (address));
  address.sin_family      = AF_INET;
  address.sin_addr.s_addr = inet_addr (peer->ip);
  address.sin_port        = htons (peer->port);

  if (connect (sock, (struct sockaddr *) &address, sizeof(address)) < 0)
    return NULL;

  /* Send message */
  protocol_send_message (sock, message);

  /* Get response */
  out = protocol_recv_message (sock);

  /* Tidy and return */
  close (sock);

  return out;
}

```

---

