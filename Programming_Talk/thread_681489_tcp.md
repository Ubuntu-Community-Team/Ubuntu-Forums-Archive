---
title: "tcp"
date: 2008-01-29
forum: Programming Talk
---

### Post by yxrkt on 2008-01-29
i'm writing a program to send files back and forth. i got stuck for hours, trying to figure out why the header on the messages received were wrong, and i now i'm pretty sure it has something to do with the reading and sending being much faster than the writing (i'm writing on the socket fd while it's being read on the other end?). is this even a possible problem?

---

### Post by Zugzwang on 2008-01-29
> **yxrkt said:**
> [...], and i now i'm pretty sure it has something to do with the reading and sending being much faster than the writing (i'm writing on the socket fd while it's being read on the other end?). is this even a possible problem?

Writing usually isn't faster than sending. However, TCP uses flow control and if you use blocking communication, writing to the socket will cause the sending thread to wait until the receiver has processed enough information such that the buffer for the incoming data is not full. 

However, it should not make a difference if you are writing to the socket at the same time it is read at the other end. The effect is the same and, by the way, this is what happens nearly all the time when using blocking communication.

Did I understand your question correctly? If not, please try to rewrite it and give more details.

---

### Post by yxrkt on 2008-01-29
hm, well the socket is set to non-blocking. thx for the replay btw

---

### Post by Zugzwang on 2008-01-30
Did you really made sure that you don't discard any error messages or values when writing/reading to/from the socket?

---

### Post by yxrkt on 2008-01-31
i'm discarding wouldblocks

---

### Post by supirman on 2008-01-31
You'll need to provide more information if you want more responses.  You said the headers aren't correct when you receive them.  Which headers are you speaking of?  How are they not correct?  Are these 'application level' headers that you're encapsulating into the TCP packet?  Show us what the header is supposed to look like and then what you actually receive.

We can offer more help if you provide us with ample information.

---

### Post by Zugzwang on 2008-01-31
> **yxrkt said:**
> i'm discarding wouldblocks

Is it possible that the receiver doesn't get some parts of the overall message? Note that it may be the case (I'm afraid that I'm no expert in this, so please look it up) that if writing to a socket causes an error message (saying that this call would block), it might be the case that this piece of information is *not* transmitted and you have to repeat trying to write until the error does not occur any longer.

---

### Post by yxrkt on 2008-01-31
@ supirman: yes, application headers. i set them to be 0xababcdcd. my test was to send a text message full of 1's (about one message's worth) then mass 2's. when i check the header on the packets (after the first one) i see 32323232 (32 hex is ascii for '2'), so...

@zugzwang: i believe the wouldblock error only occurs when the socket has nothing to do (it would block if the socket wasn't set to non-blocking)

---

### Post by supirman on 2008-01-31
Care to post the code so I can take a look?  

Also, you may want to look at Beej's Guide to Network Programming if you haven't already.  More specifically, he has a section on encapsulating data. 

Link: [Beej's Guide]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html#sonofdataencap")

---

### Post by Zugzwang on 2008-02-01
> **yxrkt said:**
> @zugzwang: i believe the wouldblock error only occurs when the socket has nothing to do (it would block if the socket wasn't set to non-blocking)

Certainly. But I am talking about sending messages. If you send a message, you make the socket non-idle. According to 
[http://linux.about.com/library/cmd/blcmdl2_send.htm]("http://linux.about.com/library/cmd/blcmdl2_send.htm") (note that I am simply guessing what commands you are using since you didn't tell us)  the signals "EAGAIN" or "EWOULDBLOCK" can occur when sending messages. And in this case you have to try that again later (as "EAGAIN" tells us from its name).

Maybe you don't know, but TCP has some built-in feature that makes sure that the receiver isn't flooded with messages. Therefore if you send too quickly, the send command would block if the receiver hasn't acknowledged enough bytes of data so far. So the "EWOULDBLOCK" error can occur when sending as well. In this case you have to repeat the sending later. And if you don't, some data will be missing, which is the problem you have.

---

### Post by yxrkt on 2008-02-01
sorry for late reply, was forced to divert my attention somewhere else for a bit.

here is some of the code i'm using from the sender:

```

  while ( !feof( inFile ) )
  {
    msg.size = (unsigned short) fread( (char *) msg.buffer, 1, MAX_BUFFER_SIZE, inFile );
    if ( msg.size < MAX_BUFFER_SIZE ) msg.id = MESSAGE_DONE;
    err = send( sTCP, (char *) &msg, (int) msg.size + HEADER_SIZE, 0 );
    ErrCheck( err, 315 );
    do {
      fd_set fdWrite;
      FD_ZERO( &fdWrite );
      FD_SET( sTCP, &fdWrite );
      TIMEVAL tv;
      memset( &tv, 0, sizeof( tv ) );
      err = select( 0, NULL, &fdWrite, NULL, &tv );
      ErrCheck( err, 317 );
    } while ( !FD_ISSET( sTCP, &fdWrite ) );
  }

```

edit: message is given a default header before this code, and the receiver accepts MESSAGE_HEADER or MESSAGE_DONE messages. ErrCheck terminates the process if error is not a wouldblock. HEADER_SIZE is the size of the message w/o the byte array.

---

### Post by yxrkt on 2008-02-02
bump

---

### Post by supirman on 2008-02-03
Is ErrCheck checking to see if the parameter 'err' is EWOULDBLOCK?  If I'm not mistaken, send will return -1 on error with the variable errno (see 'man errno') set to the appropriate error condition.  

Also, may I ask, is there any particular reason you're doing this with nonblocking sockets?  Additionally, with your select timeout set to zero, you'll likely suck up a lot of CPU

I can't reproduce the issue you're having with just the snippet, so perhaps you could post the whole source so I can build it and see the error.

---

### Post by Zugzwang on 2008-02-04
Where is the part in your code in which you repeat sending if you get a EWOULDBLOCK error? It appears that you don't have that, so that may be your problem.

Note that calling select to assure that send would not send a EWOULDBLOCK error is not the way to go since:
- 1. What you are doing in your code is simulating blocking I/O, so why not use that instead?
- 2. Depending on the actual implementation in the OS, select may return even though there is not enough space in write buffer to hold your whole message.
- 3. The write buffer may not be ready immediately after the socket has been opened. Since you check if you are ready *after* the write, you may miss the first packet.

Blocking communication is usually easier to handle and if you need your program to be non-blocking or deal with several requests at the same time you may use multi-threading to deal with the issue. In best "programming talk" manner I'm recommending a different programming language, i.e. Java for this. :-) But don't of course C is fine for that too although you need to read tutorials on multi-threading *carefully*.

---

### Post by The Cog on 2008-02-04
Another thing: If you send several message blocks, don't expect that they will come out divided up in successive read calls to the socket at the other end. It is possible for two messages to come out in a single read call, or even for half a message or one-and-a-half messages. It will all arrive at the receiver eventually, in the right order but you need to insert some way of demarcating messages into the stream just like you would if reaqding a series of messages from a file.

---

### Post by fyplinux on 2008-02-05
I just solved such a problem by 

1. dividing the data into fixed-size packet, just using read(x,y,PACK_LEN);
2. send out the packet by write(x,y,PACK_LEN), then **fsync(x)**
3. receive the data by read(x,y,PACK_LEN), then save to file, write(x,y,PACK_LEN);fsync(x);


you may also like to see the man page of **sendfile**, **send** and the buffering concepts:[http://www.gnu.org/software/libc/manual/html_node/Buffering-Concepts.html#Buffering-Concepts](http://www.gnu.org/software/libc/manual/html_node/Buffering-Concepts.html#Buffering-Concepts)

---

### Post by The Cog on 2008-02-06
If you're just transferring a single file contents, all that fixed block length stuff is not necessary - it doesn't matter what sized globs the data is received in, you just write it tp file. 

The problem comes when you are expecting discrete messages. Using fixed length messages is one solution (keep reading until you heve received the correct amount and make sure any extra is retained because it's the start ot the next message). The other solution is to use variable length messages with either a length indicator at the front, or a unique end sequence.

Interestingly, HTTP uses two techniques: The header itself uses a unique ending sequence - a blank line of text, but in that header is a length indicator that tells you the length of the response body that's going to follow.

---

