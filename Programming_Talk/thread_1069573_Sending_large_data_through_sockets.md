---
title: "Sending large data through sockets"
date: 2009-02-14
forum: Programming Talk
---

### Post by napsy on 2009-02-14
Hello.

I've programmed in network sockets for some time now but never figured it out an efficient way to send large data through sockets.

For example, I have a 2 MB data that I want to send to a client. The data contains multiple small data that I later parse and separate. Because recv() must have a fixed length and the receiver buffer is limited, there's no guarantee that all data is sent with one single send() call. There's a trick to create a loop but the data is so dynamic and the server has threads that send different data to s single socket connection. I solved this by fragmenting every data buffer to 1kb smaller fragments and always sending them together with a header attached that tells what data is it and what's the data's total length.

Now I'm asking is there another way to send large dynamic data that needs to be separated

---

### Post by dwhitney67 on 2009-02-14
From what I understand in your post, you are breaking your 2MB of data into small packets, prefacing each packet with a header indicating perhaps packet-size and perhaps with a packet-sequence-number or some other identifying ID.  You are then sending these packets through a TCP socket to another application.

This is typically the way it is done.  If the recipient of the data is on the same host system, then perhaps there are alternatives to providing the data.  Otherwise, what you have described is fine.

What compelled you to post a query here on the forum?  Is something not working as expected?


P.S.  If you have development control over the application that is receiving the data, perhaps you can use the following C++ code on it and on your application.  If you are programming in a different language, look for the equivalent library calls.  Btw, I do not know if these setting will work; I've never had a need to test it.

```

////////////////////////////////////////////////////////////////////////////////
//
// Method:  SetSendBufferSize
//
////////////////////////////////////////////////////////////////////////////////
void
Socket::SetSendBufferSize(unsigned int size)
{
  if (setsockopt(m_Socket, SOL_SOCKET, SO_SNDBUF, (void *) &size, sizeof(size)) < 0)
  {
    throw std::runtime_error("Could not set SendBufferSize for socket!");
  }
}


////////////////////////////////////////////////////////////////////////////////
//
// Method:  SetRecvBufferSize
//
////////////////////////////////////////////////////////////////////////////////
void
Socket::SetRecvBufferSize(unsigned int size)
{
  if (setsockopt(m_Socket, SOL_SOCKET, SO_RCVBUF, (void *) &size, sizeof(size)) < 0)
  {
    throw std::runtime_error("Could not set RecvBufferSize for socket!");
  }
}

```

---

### Post by napsy on 2009-02-14
Thanks for your answer. I thought there was a different method but ok if that's the way then let it be.

---

### Post by pp. on 2009-02-15
What language are you using? 

What you describe is nicely covered by TCP. I can't believe that there are languages which support sockets but lack a basic implementation of the TCP protocol.

---

