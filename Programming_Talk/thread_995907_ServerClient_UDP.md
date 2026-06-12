---
title: "Server/Client UDP"
date: 2008-11-28
forum: Programming Talk
---

### Post by FaresH on 2008-11-28
Hi, 

We have a exercise to hand over in the few days to come. I tried to do it, I done most of the job but I am kind of stuck.

ftclient <host> <port> <filename> <save as>
ftserver <port> <size of each package> <delay between sent package>

The client sends a filename to the server.
If the server has the file, it sends 4 bytes to the client, which are size of the file (Using the stat() function on the server side). Else it sends one byte of 0xff, and the client closes the socket and unlink the file. 
If the file exist, the client gets ready to receive the packages. 
If in 10 seconds no pack arrives (I used select() ), the client aborts.
If a package arrives, it has 1 byte of success, 4 bytes of offset, and the rest is the content of the message.

What I am not able to understand is how the client receives the message in a buffer full of bytes and translate it. I know I must use the ntohl (network to host long) function. 

These are my question:

What is the size I should use for the buffer ?
How to copy the content of the message into another char * [] ?
How to translate from the buffer full of bytes into something I can use ?

Any code example would more then appreciated...

This is what I wrote in the core so far:

Loop in main

```

// Get ready to receive the content of the file
while(received < fileSize ){
	// Wait 10 seconds for the next package from the server
	if( select(sd+1, &readfd, NULL, NULL, &timeout) != 0 ){
		if( read(sd, &buffer, sizeof(buffer)) < 0 ){
			perror("Error in reading the package\n")
			exit(1);
		}
		// If first byte is -1 abort
		if( atoi(ntohl(buffer[0]) != -1 ){
			perror("Error sent from server\n");
			exit(1);
		}
		offset = getOffset(buffer);
		lseek(fd, offset, SEEK_SET);
		copyMsg(buffer, &temp);
		write(fd, temp, sizeof(temp), 0);
	 }else{
	        perror("Timeout\n");
	        exit(1);
        }
}

```

getOffset function

```

int getOffset( char * buffer[] ){
	static int place=1, i=1, size=0 ;
	if( i == 4 ){
		return(place);
	}
	if( (size = atoi(ntohl(buffer[i]))) > 0 ){
		place *=  size ;
	}
	i++;
	return(getOffset(buffer));
}

```

---

### Post by dwhitney67 on 2008-11-28
This seems like an interesting problem; I wish I could provide immediate help, but I need to leave the house.

You did not indicate in your OP if the "package" is of fixed-length or not.  It would be helpful if it were.  Then you could define your data in a structure, with the "content" being declared to be a fixed-length array.

P.S.  You also did not state if your server and client will be on distinct systems employing different architectures.  Endianess of the data will matter if so.

---

### Post by FaresH on 2008-11-28
No it is not a fixed length. 

It depends on the argument uses to start the ftserver.

ftserver <port> <size of each package> <delay between sent packages>

Both will have the same architectures.

---

### Post by dwhitney67 on 2008-11-28
> **FaresH said:**
> ...
These are my question:

What is the size I should use for the buffer ?
How to copy the content of the message into another char * [] ?
How to translate from the buffer full of bytes into something I can use ?

The buffer size, IMO, should be equivalent to the maximum number of bytes that your client can expect to receive from the server.  From your requirements, this is the package size.

Because you have decided to pack your data (success, offset, and content) into one buffer, I suggest that you do so in a binary format.  Thus the server will define a buffer (of the size of the package), and then use memcpy() to fill in the values.

When the client receives a buffer (once again, the same size as a package), perform the opposite, using memcpy().

For example, from the server's perspective:
[php]
#include <string.h>

...
const size_t PKG_SIZE     = 1024;
const size_t CONTENT_SIZE = PKG_SIZE - sizeof(char) - sizeof(int);

char  success = 1;
int   offset  = 0;
char* content = calloc(CONTENT_SIZE+1, sizeof(char));

// read content from the file (e.g. using fgets())
while (fgets(content, CONTENT_SIZE, fp))
{
  // fill in buffer to send to client
  char* buf = calloc(PKG_SIZE, sizeof(char));

  memcpy(buf, &success, sizeof(char));
  memcpy(buf + sizeof(char), &offset, sizeof(int));
  memcpy(buf + sizeof(success) + sizeof(offset), content, strlen(content));

  // send buffer to client
  ...

  // free memory
  free(buf);

  ...
}
[/php]

From the client's perspective:
[php]
...
// receive buffer from server
...

// copy buffer fields into something useful
memcpy(&success, buf, sizeof(char));
memcpy(&offset, buf + sizeof(char), sizeof(int));
memcpy(content, buf + sizeof(success) + sizeof(offset), CONTENT_SIZE-1);
[/php]

The "line" is allocated one more character than needed so that it has room for the null-termination character.  There is no need to send this character via the UDP socket; in fact, you should specify the PKG_SIZE in the send() call.

Upon copying the data to "line", ensure to leave the last character space for the null-termination character.

The rest of the processing of your application is pretty straightforward; let me know if you have any further questions.

---

### Post by FaresH on 2008-11-29
No the server doesn't tell the client the size of the packs he is about to send. He just gives him the file size. And then start sending the packages like this : 1 success byte + 4 offset bytes + content ( which is unknown ).

---

### Post by dwhitney67 on 2008-11-29
With the file-size information provided by the server, you should be able to dynamically allocate space for the content buffer.

Each time the server sends a chunk of that content, it provides an offset.  For the first package, that offset will (should) be zero.  Subsequent packages will have an incremented offset value.  So if the server sends 512 bytes (of content) with the first package, the second package's offset value will be 512.

Use this offset value to adjust the insert position of your content buffer when copying data.  For example:
[php]
memcpy(content + offset, serverData + sizeof(success) + sizeof(offset), pkgSize - sizeof(success) - sizeof(offset));
[/php]

Now the code above assumes the client is aware of the package size.  You state that it is not.  The client has to know this information, or alternatively be made aware of the size of the content field in the buffer received from the server.  Another alternative, if you know that the content data is null-terminated is to use strlen() to get the length.  In either case, adjust the memcpy() call above to meet your needs.

---

### Post by FaresH on 2008-11-30
Thanks a lot but I found another solution, UDP protocol can not send more then 65,507 bytes peer package. And I have 5 bytes ( offeset and -1 or 0 ).
So I set the max to 65500 cells. :D

But I have another question:

How do I take the filesize and put it in an char array of 4 cells ?

---

### Post by dwhitney67 on 2008-11-30
> **FaresH said:**
> ...

But I have another question:

How do I take the filesize and put it in an char array of 4 cells ?

You can use memcpy() to place filesize into a buffer, or you may want to just try sending the filesize directly.

For the first option:
[php]
memcpy(buf, &filesize, sizeof(filesize));
sendto(sd, buf, sizeof(buf), ...);
[/php]

or try this:
[php]
sendto(sd, (const char*) &filesize, sizeof(filesize), ...);
[/php]

---

### Post by FaresH on 2008-11-30
I forgot to tell you that filesize in a long.

```

	struct stat fileStat ;
	long fileSize, i; 

	printf("Getting file size\n");
	if( stat(fname, &fileStat) < 0 ){
		printf("Error in getting file status\n");
	}
	fileSize = fileStat.st_size ;
	printf("File size : %i\n", fileSize);
	i=fileSize;
	if( (fd = open(fname, O_RDONLY)) < 0 ){
		printf("Error in opening the requested file\n");
		return(1);
	}

	memcpy(buf, &fileSize, sizeof(fileSize)); 
	printf("Buf: %s\n", buf);
	sendto(ssd, buf , strlen(buf) , 0,(struct sockaddr*)&client, sizeof(client));


```

When I run it the fileSize is good, but the buf is empty.

---

### Post by dwhitney67 on 2008-11-30
Don't expect to be able to printf() the buffer; it contains non-printable data in it.

Also, don't rely on strlen() to get the length of the buffer.  Regardless of how big your buffer is, you only want to send the 4-bytes representing the file size.  Use sizeof(filesize) to accomplish that.

Btw, I just referenced the manpage for recv() and recvfrom().  These functions return the size of the data package received (or -1 if it fails).  You can use this size to determine the length of the content portion of the package.  Just subtract the size of the success flag and the size of the offset.

P.S.  You are also missing the logic in your code to send a single-byte containing 0xFF if the file does not exist.

---

### Post by FaresH on 2008-12-02
the communication between the client and server works fine.

```


//loop 
	if( (i= read(fd, &buf, packSize, 0)) > 0 ){
		printf("\nBytes from file read: %i\n", i);
		memmove(buf+5, buf, sizeof(buf));
		buf[0] = '0' ;	
		memcpy(buf+1, &offset, sizeof(offset)); 
		i = sendto(ssd, buf, packSize+5, 0, (struct sockaddr*)&client, clen);
		printf("Bytes sent to client: %i\n", i);
	} 

```

File exist getting file size: 688  

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 60
Bytes sent to client: -1

Bytes from file read: 28
Bytes sent to client: -1

Why doesn't it send anything ?
If I read from the file and send directly without manipulating the buffer, the client receives everything.
The moment I use memcpy and memmove, the server sends nothing.

---

### Post by dwhitney67 on 2008-12-02
> **FaresH said:**
> the communication between the client and server works fine.

```

//loop 
	if( (i= read(fd, &buf, packSize, 0)) > 0 ){
		printf("\nBytes from file read: %i\n", i);
		memmove(buf+5, buf, sizeof(buf));
		buf[0] = '0' ;	
		memcpy(buf+1, &offset, sizeof(offset)); 
		i = sendto(ssd, buf, packSize+5, 0, (struct sockaddr*)&client, clen);
		printf("Bytes sent to client: %i\n", i);
	} 

```
...


Your memmove() call seems to be the suspect.  It appears that you are overwriting data in buf.  Also, after reading from the file, you should use the value 'i' in lieu of sizeof(buf) when performing the memmove().

Below may be a simpler, more straightforward approach:
[php]
char success = '1';   // or whatever this field requires
int  offset  = 0;

int bufSize  = sizeof(success) + sizeof(offset) + pkgSize;
int pkgStart = sizeof(success) + sizeof(offset);

char* buf = calloc(bufSize, sizeof(char));

while (!feof(fd))
{
  // read data from file; place data into the buffer starting at position pkgStart
  int bytesRead = read(fd, buf + pkgStart, pkgSize);

  if (bytesRead > 0)
  {
    // place 'success' and 'offset' values into the buffer
    memcpy(buf, &success, sizeof(success));
    memcpy(buf + sizeof(success), &offset, sizeof(offset));

    // send the buffer contents to the client; note the buffer may be smaller than the
    // size of buffer.
    int bytesSent = sendTo(ssd, buf, sizeof(success) + sizeof(offset) + bytesRead, 0, (struct sockaddr*) &client, clen);

    assert(bytesSent > 0);

    // increment the offset based on the amount of data read
    offset += bytesRead;

    // per requirements, delay N (pkgSendDelay) seconds before sending next package
    struct timeval timeout = {pkgSendDelay, 0};
    select(0, 0, 0, 0, &timeout);
  }
}

free(buf);
[/php]

Edit 1:  I just noticed (and I have corrected it above), that I was missing one of the parameters (i.e. the fourth one) to sendto().

Edit 2:  I simplified the code to use only one buffer.

---

### Post by FaresH on 2009-01-26
I am now working on a Reliable UDP. Its not the right therm since UDP can not be reliable. But the program is a combination of UDP and TCP. So all data will arrive at the end and fast. 

Anyway, I have a small problem:

The server will take 60k bytes of data from a file and send them to the client.

The packet will look like this:

[size of packet number] [packet number] [data] 

<size of packet number> will be the value ( in integer ) of how much does <packet number> take cells in the array.

How do I know the size of <packet number> so I can copy it to the char array, so I can copy the data right after the <packet number> ?

And its not sizeof, because if I do:

[PHP]

int a = 1 ;
printf("%i", sizeof(a));

a = 260 ;

printf("%i", sizeof(a));

[/PHP]

This code will give me 4 on both outputs, although in fact the first <a> takes in byte and the second <a> takes two bytes. 

Oh and I need to covert the < size of packet number> and <packet number> into host to network byte order on the server side, and to network to host byte order on the client side.

Can anyone help me out ?

---

### Post by dwhitney67 on 2009-01-27
> **FaresH said:**
> ...
This code will give me 4 on both outputs, although in fact the first <a> takes in byte and the second <a> takes two bytes. 

Oh and I need to covert the < size of packet number> and <packet number> into host to network byte order on the server side, and to network to host byte order on the client side.

Can anyone help me out ?

May I suggest that you dispense with the packet-number size, and just send the packet-number as a four-byte value; then include your data.  Together these will make up the "payload" of your UDP message.  The smaller the message, the more likely it will be delivered.  But since you are designing an app to counter the effects of data loss, maybe this doesn't matter.

So with:
```

+------------------+---------------+
|  packet number   |     data      |
+------------------+---------------+

```

you could write code such as:
```

unsigned int packetNumber = 0;
char buf[256] = {0};
char payload[4+256] = {0};
...
memcpy(payload, &packetNumber, sizeof(packetNumber));
memcpy(payload+4, buf, sizeof(buf));   // or use strlen() if data in buf is a string.
++packetNumber;
...

```
Concerning the host-to-network data arrangement, the function(s) you require is htons() or htonl().  Conversely, on the receiving end (the client side), ntohs() and ntohl().  The 's' and the 'l' stand for "short" and "long" respectively.

I've never thought much about these functions, but I suppose to organize the "payload" buffer, you would go through each long-word.  Consider the following:
```

#include <arpa/inet.h>
#include <string.h>
#include <stdio.h>

void prepareForSending(char* buf, const size_t bufSize)
{
  for (unsigned int i = 0; i < bufSize; i += sizeof(unsigned int))
  {
    const unsigned int tmp = htonl(*((unsigned int*)(buf+i)));
    memcpy(buf+i, &tmp, sizeof(tmp));
  }
}

void prepareForReceiving(char* buf, const size_t bufSize)
{
  for (unsigned int i = 0; i < bufSize; i += sizeof(unsigned int))
  {
    const unsigned int tmp = ntohl(*((unsigned int*)(buf+i)));
    memcpy(buf+i, &tmp, sizeof(tmp));
  }
}

void displayData(const char* msg, const char* buf, const size_t bufSize)
{
  printf("%s: ", msg);
  for (unsigned int i = 0; i < bufSize; ++i)
  {
    printf("%02x ", buf[i]);
  }
  printf("\n");
}

int main()
{
  char package[8] = {0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38};

  displayData("original   ", package, sizeof(package));

  prepareForSending(package, sizeof(package));

  displayData("after htonl", package, sizeof(package));

  prepareForReceiving(package, sizeof(package));

  displayData("after ntohl", package, sizeof(package));
}

```
P.S.  I do not know if the code above is fulfilling the proper requirements; I've never done this sort of stuff at all, and I do not have dissimilar systems (e.g. CPUs) to test with.

---

