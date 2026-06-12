---
title: "socket programming--how to implement ftp server client"
date: 2010-02-15
forum: Programming Talk
---

### Post by rejuvenate on 2010-02-15
hi,
i am new to socket programming and i need to implement ftp server but the code for sending and recieving is not working in my PC but the same code is working on other PC...
both have same ubuntu...what is problem
thnx in advance

---

### Post by rejuvenate on 2010-02-15
i have attached the code in the following link
[http://ubuntuforums.org/showthread.php?t=1404552](http://ubuntuforums.org/showthread.php?t=1404552)

---

### Post by dwhitney67 on 2010-02-15
On your server side, you make a bad assumption here:
```

send(new,data,sizeof(data), 0);

```
How do you know that the data has a size of 256 bytes?  It could be less!  Read the man-page for fread().

On your client side, you cannot use recv() by itself.  You need call recv() _only_ if there is data to be received.  Otherwise your client will block on the recv().  Investigate the usage of select() to assist you in determining when there is data to be received (or alternatively use a non-blocking socket).

Also, if recv() returns 0 bytes, then it is a sure-bet that the server has closed the socket, and presumably is done with sending it's data.  Nowhere do you check for this.

Lastly, you may want to consider calling fflush() after fprintf() to the output file.

---

### Post by rejuvenate on 2010-02-16
the code is working fine when i am server and client on the same computer but the client is not receiving the complete text when server is running on different computers. also when i am reading any other file to read like mp3 or pdf file to read and send to the server it is not working
the change done is file i am reading
server```
 FILE *rfile;
                   rfile = fopen("trial.mp3", "r");
``` 
client```
FILE *wfile;        
        wfile=fopen("ctrial.mp3","w");
```

---

### Post by Zugzwang on 2010-02-16
> **rejuvenate said:**
> the code is working fine when i am server and client on the same computer but the client is not receiving the complete text when server is running on different computers. also when i am reading any other file to read like mp3 or pdf file to read and send to the server it is not working
the change done is file i am reading


First of all, it is not nice to completely ignore dwhitney's comments. As he is pointing out problems with your code, you should fix them first and try again.

Also note that "fprintf" is *not* the correct function for writing a binary file as it will only write data up to the first occurrence of a '\0' value, which are common in binary data. Also, you might receive data which does not end with a '\0', for example when the data is split into two packets. Examine what your program does in this case.

---

### Post by dwhitney67 on 2010-02-16
> **Zugzwang said:**
> 
Also note that "fprintf" is *not* the correct function for writing a binary file as it will only write data up to the first occurrence of a '\0' value, which are common in binary data. Also, you might receive data which does not end with a '\0', for example when the data is split into two packets. Examine what your program does in this case.

Thanks for the correction.  The OP should be using fwrite().

Also, the OP should ensure that there are no firewalls in place preventing one system from communicating with the other.

---

