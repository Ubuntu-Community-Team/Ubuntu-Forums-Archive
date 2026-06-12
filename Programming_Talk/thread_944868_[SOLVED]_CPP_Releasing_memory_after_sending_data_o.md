---
title: "[SOLVED] CPP: Releasing memory after sending data over socket"
date: 2008-10-11
forum: Programming Talk
---

### Post by sillv0r on 2008-10-11
Howdy,

I have a quick question about memory management when sending data over a socket.  (I'm using blocking sockets in cpp. If any additional information is needed please ask.)

I think I merely lack an understanding of the way this kind of thing is supposed to work.  So any constructive criticism is welcome.

Consider the following statement:

```
send(sockfd, buffer, length, 0);
```

My problem is that **buffer** is a dynamically allocated array.

I'm not sure about how to release the memory taken up by **buffer** at the completion of the **send** call.

* At the completion of the call to **send**, has all the data in **buffer** been "placed on the line?"

- If it has, then I figure memory used by **buffer** can be safely released--or can it?

- If it hasn't, I don't believe that the socket library will release the memory for me--or does it?

Thoughts? Questions?

---

### Post by PandaGoat on 2008-10-11
uh
[PHP]free buffer;[/PHP]

If your using c++ though:
[PHP]delete[] buffer;[/PHP]

Yes it can be safely released if you're done with it after sending it.

---

### Post by sillv0r on 2008-10-11
Thanks for the reply PandaGoat.

<snip>For clarity, my post was not a question of "how" to release memory. It was more towards if releasing **buffer** after calling **send** was okay, or bad practice, or etc..

* I assume, by your reply, that at the completion of **send** the memory used by **buffer** is okay to be released.</snip>

Thanks again.

[EDIT]
I didn't see the following line when I first read your post.  > Yes it can be safely released if you're done with it after sending it.(Ignore the snipped text and thanks a bunch.)
[/EDIT]

---

### Post by dwhitney67 on 2008-10-12
> **sillv0r said:**
> Howdy,

I have a quick question about memory management when sending data over a socket.  (I'm using blocking sockets in cpp. If any additional information is needed please ask.)

I think I merely lack an understanding of the way this kind of thing is supposed to work.  So any constructive criticism is welcome.

Consider the following statement:

```
send(sockfd, buffer, length, 0);
```

My problem is that **buffer** is a dynamically allocated array.

I'm not sure about how to release the memory taken up by **buffer** at the completion of the **send** call.

* At the completion of the call to **send**, has all the data in **buffer** been "placed on the line?"

- If it has, then I figure memory used by **buffer** can be safely released--or can it?

- If it hasn't, I don't believe that the socket library will release the memory for me--or does it?

Thoughts? Questions?

One thought to ponder about... what will you do if send() returns prematurely before sending the entire buffer?

Consider implementing your own method for sending data, maybe something like:
[php]
void Send( int socket, const char *buf, const size_t len )
{
  size_t bytesSent = 0;

  while (bytesSent != len)
  {
    int rtn = send(socket, buf + bytesSent, len - bytesSent, 0);

    if (rtn < 0 && errno == EAGAIN)
    {
      continue;
    }
    if (rtn < 0)
    {
      throw runtime_error("Error occurred while attempting to send data!");
    }

    bytesSent += rtn;
  }
}
[/php]

---

