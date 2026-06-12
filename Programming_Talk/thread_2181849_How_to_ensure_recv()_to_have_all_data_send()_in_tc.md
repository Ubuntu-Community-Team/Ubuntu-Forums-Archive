---
title: "How to ensure recv() to have all data send() in tcp"
date: 2013-10-19
forum: Programming Talk
---

### Post by Javed_iqbal on 2013-10-19
[COLOR=#000000][FONT=Arial]I  am implementing the recvall() function to be sure that the data is completely sent. Also I modified the send() function to sendall() like this:

     [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]int sendall (int consocket, char* buf, int* len)[/FONT][/COLOR]      {
                                                                            int total = 0;
                                                                            int bytesleft = *len; // how many we have left to send
                                                                            int n;
                                                                            while(total < *len) {
                                                                                                           n = send(consocket, buf+total, bytesleft, 0);
                                                                                                           if (n == -1) { break; }
                                                                                                           total += n;
                                                                                                           bytesleft -= n;
                                                                                                         *len = total; // return number actually sent here
                                                                                                           return n==-1?-1:0; // return -1 on failure, 0 on success
                                                                                                        }
                                                                       }

[FONT=Arial]How can I implement recvall()? Say I sent from the server a struct of 14 bytes and I check in the client and get 12 bytes.. now in an unreliable situation how should I manage to get the other two bytes... I have spent time trying... any help welcomed[/FONT]

---

### Post by The Cog on 2013-10-19
You absolutely **have** to impose some extra structure on the data you send to do this. TCP offers just a byte stream - guaranteed to be in order, but no timing guarantees. There are two common methods for doing this. 

The first is to send a message at the start of the structure you are sending telling the recipient how big the following payload is. HTTP uses this for instance, by sending a Content-Length line in its header. The disadvantage of this is that the sender has to know the payload size in advance. Streaming an unknown-length payload can be achieved by sending "chunks" and indicating in the header whether or not each chunk is the final one. I have read about an implementation that simply sends the number of bytes in decimal followed by an end-of-line character as the header, and this may well be the easiest thing for you to do, e.g. send "14\n" followed by your 14-byte structure.

The second method is to put a recognisable end-of-message marker on the end of the transmission. The disadvantage of this is that the payload must not be able to contain this marker, so either you have to know the payload structure, or you have to encode and decode the payload during transfer using a scheme designed to alter any occurrences of the marker in the payload. UUCP does this by encoding binary data into ASCII and using extra characters to then indicate the end. HTTP headers do it by using a blank line as the end of header marker, but requiring that the header cannot contain blank lines.

Since you are writing your own sendall and receiveall routines, it might make sense to do the header or trailer handling inside them, hiding the ugly details from the caller.

P.S. I just found this nice description of the problem:
[http://brunov.info/blog/2013/02/09/tcpip-client-server-application-exchange-with-string-messages/](http://brunov.info/blog/2013/02/09/tcpip-client-server-application-exchange-with-string-messages/)

---

### Post by Javed_iqbal on 2013-10-19
will select() serve the same?

---

### Post by Javed_iqbal on 2013-10-19
will using select in an indefinite loop serve the purpose?

---

### Post by dwhitney67 on 2013-10-19
> **Javed_iqbal said:**
> will using select in an indefinite loop serve the purpose?

IMHO, you should avoid blocking on a recv() call unless you know that there is data ready to be read.  Thus, yes, select() would help to notify you that there is activity (data to be read, a disconnect, etc) on the socket.  It is also helpful in cases where multiple sockets need to be handled.

Your sendall() function could probably be simplified to the following:
```

int sendall(int sock, const char* data, int data_length)
{
    int bytes_sent = 0;

    while (bytes_sent < data_length)
    {
        int result = send(sock, data + bytes_sent, data_length - bytes_sent, 0);

        if (result == -1)
        {
            if (errno == EAGAIN) continue;   // optionally, you may also want to check if errno == EINTR

            bytes_sent = -1;
        }
        bytes_sent += result;
    }

    return bytes_sent;
}

```

---

### Post by The Cog on 2013-10-19
Using select() will help you know when there is some data to recieve, but it will not help you know when a complete message has been received. TCP delivers a byte stream - it does not and cannot convey any structure or indication of separate records etc. If you need that structure then it **must** be embedded into the stream somehow. There is no point wriggling and looking for other answers. That's what has to be done. With the examples you posted, I would suggest doing as my earlier post, send a \n terminated record length string before the payload itself.

---

