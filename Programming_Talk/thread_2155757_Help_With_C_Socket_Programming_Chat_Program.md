---
title: "Help With C Socket Programming Chat Program"
date: 2013-06-19
forum: Programming Talk
---

### Post by mu2we35 on 2013-06-19
I just started learning socket programming in c. I have problems in getting my chat program to work. There seems to be a connection but there is no message passing from the server to the client or viceversa. I hope you can help me by pointing out what is wrong or lacking in my code. Thanks.

---

### Post by ziekfiguur on 2013-06-19
the problem is with this code at line 81 in your client:
```
    if ((numbytes = recv(sockfd, buf, MAXDATASIZE-1, 0)) == -1) {
        perror("recv");
        exit(1);
    }
```
when you connect to the server you call recv, which means you wait for the server to say someting. Meanwhile the server is waiting for the client to say something. They are both waiting for each other, so nothing is ever going to happen. If you remove that code it will work.

Another thing I noticed is your definition of client_message ```
char client_message[2000];
```
with which you do this:
```
memset(client_message, 0, 2000);
while( (read_size = recv(new_fd, client_message , 2000 , 0)) > 0 )
{
    //Send the message back to client
    printf("Message of Server:\n");
    write(new_fd , client_message , strlen(client_message));
}
```
If you receive a message of more than 2000 characters there will be no '\0' character at the end of client_message and you will have no idea what strlen(client_message) would return, which means you'll get a buffer overflow.
A better way to do this is by using strnlen(client_message, 2000)

---

### Post by zobayer1 on 2013-06-19
As  		ziekfiguur has mentioned, removing those 4 lines will let the program run, but it still has problems like, first send "hello" from client, you get back "hello", then send "hi", you will get back "hillo", so basically it is  not replacing the content of the buffer. You need to take care for that from your clients, i.e. send some sentinnel character which can effectively mark an end of message. Also, I don't think mixing up send / recv with read / write is a good idea.

---

### Post by mu2we35 on 2013-06-19
Thank you [ 						 							 						 					]("http://ubuntuforums.org/member.php?u=960698") 				 				 					 						 	[**[COLOR=#000000]ziekfiguur[/COLOR]**[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=960698") for your help. it did work but I have problems like what [ 						 							 						 					]("http://ubuntuforums.org/member.php?u=1028511") 				 				 					 						 	[**[COLOR=#000000]zobayer1[/COLOR]**]("http://ubuntuforums.org/member.php?u=1028511") stated. Sorry for being spoonfed but how can I implement that? I actually have known that there are going to be issues like that but I dont know a good way to do it. Thank you again for both of your help and I'm looking forward to your replies.

---

### Post by mu2we35 on 2013-06-19
Hi again,

I tried using this
```
while( (read_size = recv(new_fd , client_message , 2000 , 0)) > 0 ){
                
                        *(client_message + read_size) = '\0';
                        //Send the message back to client
                        write(new_fd , client_message , strlen(client_message));
}
```

but still to no avail. Could you advise what to do? Thanks

---

### Post by zobayer1 on 2013-06-20
> **mu2we35 said:**
> Hi again,

I tried using this
```
while( (read_size = recv(new_fd , client_message , 2000 , 0)) > 0 ){
                
                        *(client_message + read_size) = '\0';
                        //Send the message back to client
                        write(new_fd , client_message , strlen(client_message));
}
```

but still to no avail. Could you advise what to do? Thanks
1st option:
try memset-ing the buffer i.e. client_message before calling in recv
```

memset(client_message, 0, sizeof client_message);

```

that way you do not need to assign null and the positions which are not used have null already, so it should give correct size to strlen().

2nd option:
when I tried it in school project, I sent message in a way that the first few bytes contains the msg header which tells me the size and some other info, and rest of the buffer contains the payload (i.e.) message, so I know how long is the message upon arrival decoding the header bytes.

to explain a bit:
say char client_message[1024] is your message buffer, and you assign first 4 bytes as header.
so if your message is 20 bytes long, you put 20 in the first 4 bytes, and the message in the later 1020 bytes.

now when you receive, first read the first 4 bytes of the buffer to get the size, and then just do this:
```

// let msgsize contains the size of the message
client_message[4+msgsize] = 0; // set null
puts(&client_message[4]);

```
do the overflow checking as necessary.

this can be a workaround, may be there are better ways, I am not C/C++ socket expert.

---

### Post by mu2we35 on 2013-06-20
I think I got it,

I only encountering a problem:
server: bind: Address already in use
server: bind: Address already in use
server: failed to bind

I think my code binds multiple times. can you help me?

---

### Post by zobayer1 on 2013-06-20
> **mu2we35 said:**
> I think I got it,

I only encountering a problem:
server: bind: Address already in use
server: bind: Address already in use
server: failed to bind

I think my code binds multiple times. can you help me?



Did you prematurely close the programs? (i.e. the server?) just restart the terminal, and it should be fine. to avoid this problem, do not hard code your port number, take it as a command line parameter. so that if one port shows u the error, just start with a different port.

---

### Post by dwhitney67 on 2013-06-20
> **zobayer1 said:**
> Did you prematurely close the programs? (i.e. the server?) just restart the terminal, and it should be fine. to avoid this problem, do not hard code your port number, take it as a command line parameter. so that if one port shows u the error, just start with a different port.

A better solution would be to configure the socket to reuse the same port binding.  For example, before attempting to bind to the socket, the following could be done:
```

int sd = socket(...);

int enable = 1;

[B]if (setsockopt(sd, SOL_SOCKET, SO_REUSEADDR, &enable, sizeof(enable)) < 0)
{
    perror("Unable to configure socket");
}[/B]

bind(sd, ...);


```

---

### Post by mu2we35 on 2013-06-20
Thanks[**[COLOR=#000000] dwhitney67[/COLOR]**]("http://ubuntuforums.org/member.php?u=322753")  for the fast reply, I have implemented what you suggested but didn&#8217;t  work. I have ignored the bind problem because the code still works I  guess it binds one port then binds it again so the said problems arises.  I have made and extension on the programming by encrypting the sent  codes then decrypting then when received. The code without the decode  and encode will work just fine. I am having problems on how to implement  the decode and encode functions I created.

---

### Post by dwhitney67 on 2013-06-20
Try compiling your source code with the -Wall option.  You should see some warnings about unused/uninitialized variables.

Here's some notable warnings/problems in the Server that I have fixed:

```

                            ...
                            else if(FD_ISSET(new_fd,&readfds)){
                                decode(buffer,15485863);
                                memset(&buffer[0],0,sizeof(buffer));
                                **//check=recv(new_fd,buffer,len1,0);**
                                check=recv(new_fd,buffer,sizeof(buffer),0);
                                if(check==0){
                                    **//return;**
                                    break;
                                }
                                printf("Message: %s\n",buffer);
                            }

```
Also, you should consider receiving data from the client BEFORE you decode it.  :lolflag:

---

### Post by zobayer1 on 2013-06-20
> **mu2we35 said:**
> Thanks[**[COLOR=#000000] dwhitney67[/COLOR]**]("http://ubuntuforums.org/member.php?u=322753")  for the fast reply, I have implemented what you suggested but didn&#8217;t  work. I have ignored the bind problem because the code still works I  guess it binds one port then binds it again so the said problems arises.  I have made and extension on the programming by encrypting the sent  codes then decrypting then when received. The code without the decode  and encode will work just fine. I am having problems on how to implement  the decode and encode functions I created.


The block dwhitney67 mentioned is actually a logical bug, you can't decode anything before getting any message, but both of your server and client are stuck at this point, take a look at these parts of your code

Server```
FD_ZERO(&readfds);
FD_SET(0,&readfds);
FD_SET(new_fd,&readfds);
int check1=select(new_fd+1, &readfds, NULL, NULL, NULL);
```

Client ```
FD_ZERO(&readfds);
FD_SET(0,&readfds);
FD_SET(sockfd,&readfds);
select(sockfd+1, &readfds, NULL, NULL, NULL);
```

These parts force me to put key presses, otherwise they don't read input properly, also I think its very hard to implement both terminal read and asynchronous writes to terminal from socket in the same terminal.

---

### Post by dwhitney67 on 2013-06-20
Adding on to my previous reply, I also found a similar bug in the Client app; the decode() function is called before the call to recv().

As for any other anomalies, I cannot find any.  Text is entered on the client side, and it appears on the server side.  Similarly, when text is entered in server side, it appears on the client side.  Handling of a client on the server-side is single threaded, thus there's no concurrency issues with output being jumbled.

The only issue I see though is if the client (or server) send too much data such that the receive buffer is chock-full.  A null character should be inserted at the end of the buffer after each successful recv() call.  For example:
```

bytes_received = recv(sockfd, buf, sizeof(buf) - 1);

if (bytes_received > 0)
{
    buf[bytes_received] = '\0';

    decode(buf, ...);

    printf(...);
}
else if (bytes_received == 0)
{
    // client disconnected
}
else
{
    // error
}

```

---

### Post by dwhitney67 on 2013-06-20
> **zobayer1 said:**
> T
These parts force me to put key presses, otherwise they don't read input properly, also I think its very hard to implement both terminal read and asynchronous writes to terminal from socket in the same terminal.

Do you know of any chat applications that echo (i.e. send) each key as it is typed onto the peer application?  The ones I have used always require the user to terminate input with a newline (enter), thus flushing the standard-in so that recv() gets the entire buffer (up to the limit of the buffer size).

Can you please describe in better detail what anomaly you witnessed?

---

### Post by zobayer1 on 2013-06-20
> **dwhitney67 said:**
> Do you know of any chat applications that echo (i.e. send) each key as it is typed onto the peer application?  The ones I have used always require the user to terminate input with a newline (enter), thus flushing the standard-in so that recv() gets the entire buffer (up to the limit of the buffer size).

Can you please describe in better detail what anomaly you witnessed?

of course I will.

I followed the easiest way to debug, I put printfs here and there, and the code is supposed to be waiting just before the fgets call in if block or before the recv call on the else block, but it is not. I think I know how fgets and recv work as well as how chat clients should take input.

---

### Post by zobayer1 on 2013-06-20
Also I think this will probably be inappropriate, here [[http://zobayer.blogspot.com/2013/06/socket-programming-in-c-pthread.html](http://zobayer.blogspot.com/2013/06/socket-programming-in-c-pthread.html)] is how I did it, the basic functionality is almost same, except instead of fork() I used pthread. Posting it here so that the OP can take a look at my way. I hope it is OK.

---

### Post by dwhitney67 on 2013-06-20
> **zobayer1 said:**
> of course I will.

I followed the easiest way to debug, I put printfs here and there, and the code is supposed to be waiting just before the fgets call in if block or before the recv call on the else block, but it is not. I think I know how fgets and recv work as well as how chat clients should take input.

The fgets() will not be called until select() reports that there is activity on the stdin stream.  Activity is detected when the user flushes stdin with a newline ('enter' key press) or the stdin buffer is full.

While a user is entering characters into the stdin stream, there's the possibility of receiving new data from their peer that "corrupts" the output line where they are typing.  However, as far as what is entered in the stdin stream, it is still good.

The OP has to take their application to the next level to split the terminal (perhaps using ncurses) or employ a GUI (e.g. GTK, Qt, etc).  The data received and the data entered must never be outputted to the same area.

Other than this minor issue, there's nothing wrong with the application if the suggestions/bug-fixes I mentioned earlier are employed.

---

### Post by zobayer1 on 2013-06-20
> **dwhitney67 said:**
> The fgets() will not be called until select() reports that there is activity on the stdin stream.  Activity is detected when the user flushes stdin with a newline ('enter' key press) or the stdin buffer is full.

While a user is entering characters into the stdin stream, there's the possibility of receiving new data from their peer that "corrupts" the output line where they are typing.  However, as far as what is entered in the stdin stream, it is still good.

The OP has to take their application to the next level to split the terminal (perhaps using ncurses) or employ a GUI (e.g. GTK, Qt, etc).  The data received and the data entered must never be outputted to the same area.

Other than this minor issue, there's nothing wrong with the application if the suggestions/bug-fixes I mentioned earlier are employed.

Yah, I told about that (separating the IO) in one of my previous post as well, and I don't think its that hard, as he is already using fork, or he could just use pthread.

Also, I understand this is just for educational purpose. And, what is the point of using select and fgets here if he can just use gets, also isnt select blocking his recv as well ? (server and client both waiting for terminal entry)

---

### Post by dwhitney67 on 2013-06-20
> **zobayer1 said:**
> Yah, I told about that (separating the IO) in one of my previous post as well, and I don't think its that hard, as he is already using fork, or he could just use pthread.

Also, I understand this is just for educational purpose. And, what is the point of using select and fgets here if he can just use gets, also isnt select blocking his recv as well ? (server and client both waiting for terminal entry)

_Never_ use gets().  There's no way to specify the length of the destination buffer; hence it is considered a function that is prone to vulnerability if one enters more data than is anticipated.

The select() is useful because it can be used to determine a) there's activity on a particular file (socket) descriptor, and b) which file descriptor there's data waiting to be processed.

fgets() will block an application, thus negating the ability to recv() from a client in an asynchronous manner.  The opposite is also true.  By employing select(), or poll(), one can avoid these blocking calls.  The select() and poll() functions allow for the programmer to either block, or return control to the application after a specified amount of time.  The OP has chosen to block, which is fine... unless he/she needs to do something else (e.g. update a GUI).

---

### Post by mu2we35 on 2013-06-21
I have made a shorter code but it still has the problem stated  previously like when you type "hello" then "hi" it will output "hillo". I  also have used a simple encryption so that messages are sent encrypted.  Can anybody edit my code so that I could study it afterwards. I am just learning  socket programming and c so I am really having problems.

---

### Post by dwhitney67 on 2013-06-21
> **mu2we35 said:**
> I have made a shorter code but it still has the problem stated  previously like when you type "hello" then "hi" it will output "hillo". I  also have used a simple encryption so that messages are sent encrypted.  Can anybody edit my code so that I could study it afterwards.

Refer to this previous [post ]("http://ubuntuforums.org/showthread.php?t=2155757&p=12699584#post12699584")of mine to obtain clues as to why your program is not handling the message correctly.

---

### Post by mu2we35 on 2013-06-21
Thank you very much, I've implemented what you said and it did the job. There are some issues still like there are special characters appearing below is the terminal output:

Connection accepted
Enter message : dsa
encoded in server
decoded in client
Server reply :
dsa?&#65533;
Enter message : das
encoded in server
decoded in client
Server reply :
das&#65533;
    1
Enter message : fsdf
encoded in server
decoded in client
Server reply :
fsdfd&#65533;
Enter message : fsdg
encoded in server
decoded in client
Server reply :
fsdg&#65533;
Enter message : gdfgdfg
encoded in server
decoded in client
Server reply :
gdfgdfg
Enter message : dfg
encoded in server
decoded in client
Server reply :
dfg&#65533;&#65533;&#65533;
Enter message : gdfg
encoded in server
decoded in client
Server reply :
gdfg
Enter message : gdfg
encoded in server
decoded in client
Server reply :
gdfgoqr
Enter message : fsd
encoded in server
decoded in client
Server reply :
fsd&#65533;&#65533;&#65533;
Enter message : fsdgsdg
encoded in server
decoded in client
Server reply :
fsdgsdg
Enter message : gergergerg
encoded in server
decoded in client
Server reply :
gergergerg
Enter message :

---

### Post by dwhitney67 on 2013-06-21
> **mu2we35 said:**
> There are some issues ...


Post your updated client and server code.

P.S.  There's no need to send private messages.  I get notified each time you update this thread.

---

### Post by mu2we35 on 2013-06-21
Here is the updated code:

---

### Post by dwhitney67 on 2013-06-21
> **mu2we35 said:**
> Here is the updated code:

Whereas I understand your desire to get the server/client working, I'm surprised that you removed the usage of fork() and the select() that you had in your original program.  You also removed the ability for the server to accept input from the user; instead all you are doing now is echoing back to the client whatever they send.

Here's working code (albeit still a little fragile) for the server and the client.....

Server.c:
```

#include <sys/socket.h>
#include <arpa/inet.h>
#include <stdbool.h>
#include <string.h>      // strlen, memset
#include <stdio.h>
#include <unistd.h>      // close


/* decrypt function*/
void decode(char MESSAGE[], int pass)
{
    for(unsigned int i = 0; i < strlen(MESSAGE); ++i)
    {
        MESSAGE[i] = MESSAGE[i] - pass;
    }
}

/* encrypt function*/
void encode(char MESSAGE[], int pass)
{
    for(unsigned int i = 0; i < strlen(MESSAGE); ++i)
    {
        MESSAGE[i] = MESSAGE[i] + pass;
    }
}

int main(int argc, char *argv[])
{
    //Create socket
    int socket_desc = socket(AF_INET , SOCK_STREAM , 0);
    if (socket_desc == -1)
    {
        perror("Could not create socket");
        return -1;
    }
    puts("Socket created");

    //Prepare the server's sockaddr_in structure
    struct sockaddr_in sin;
    memset(&sin, sizeof(sin), 0);
    sin.sin_family      = AF_INET;
    sin.sin_addr.s_addr = INADDR_ANY;
    sin.sin_port        = htons( 8888 );

    // set socket option to reuse port
    int enable = 1;
    setsockopt(socket_desc, SOL_SOCKET, SO_REUSEADDR, &enable, sizeof(enable));

    //Bind
    if (bind(socket_desc, (struct sockaddr*) &sin, sizeof(sin)) != 0)
    {
        //print the error message
        perror("bind failed. Error");
        return -1;
    }
    puts("bind done");

    //Listen
    listen(socket_desc, 3);

    puts("Waiting for incoming connections...");

    //accept connection from an incoming client
    int client_sock = accept(socket_desc, 0, 0);
    if (client_sock < 0)
    {
        perror("accept failed");
        return -1;
    }
    puts("Connection accepted");

    bool client_connected = true;

    while (client_connected)
    {
        char client_message[1024] = {0};

        int bytes_read = recv(client_sock, client_message, sizeof(client_message) - 1, 0);

        if (bytes_read > 0)
        {
            client_message[bytes_read] = '\0';

            encode(client_message, 15485863);

            send(client_sock, client_message, strlen(client_message), 0);
        }
        else if (bytes_read == 0)
        {
            client_connected = false;
            puts("client disconnected");
        }
        else
        {
            perror("error performing recv()");
            client_connected = false;
        }
    }

    close(client_sock);

    return 0;
}

```

Client.c:
```

#include <sys/socket.h>
#include <arpa/inet.h>
#include <string.h>
#include <stdio.h>
#include <unistd.h>    // close

/* decrypt function */
void decode(char MESSAGE[],int pass)
{
    for(unsigned int i = 0; i < strlen(MESSAGE); ++i)
    {
        MESSAGE[i] = MESSAGE[i] - pass;
    }
}

/* encrypt function */
void encode(char MESSAGE[],int pass)
{
    for(unsigned int i = 0; i < strlen(MESSAGE); ++i)
    {
        MESSAGE[i] = MESSAGE[i] + pass;
    }
}

char* remove_newline(char *s)
{
    if (s)
    {
        char *nl = strchr(s, '\n');

        if (nl) *nl = '\0';
    }

    return s;
}

int main(int argc, char *argv[])
{
    //Create socket
    int sock = socket(AF_INET , SOCK_STREAM , 0);
    if (sock == -1)
    {
        perror("Could not create socket");
        return -1;
    }
    puts("Socket created");

    struct sockaddr_in server;
    memset(&server, sizeof(server), 0);
    server.sin_addr.s_addr = inet_addr("127.0.0.1");
    server.sin_family      = AF_INET;
    server.sin_port        = htons( 8888 );

    //Connect to remote server
    if (connect(sock, (struct sockaddr*) &server , sizeof(server)) < 0)
    {
        perror("connect failed. Error");
        return -1;
    }

    puts("Connected\n\n---Chat Start---\n");

    while(1)
    {
        char message[1024] = {0};
        char reply[1024]   = {0};

        printf("Enter message : ");
        fgets(message, sizeof(message), stdin);     // never use scanf()!

        (void) remove_newline(message);

        //Send some data
        int bytes_sent = 0;
        size_t msg_len = strlen(message);

        while (bytes_sent != msg_len)
        {
            int bytes = send(sock, message + bytes_sent, msg_len - bytes_sent, 0);

            if (bytes > 0)
            {
                bytes_sent += bytes;
            }
            else if (bytes < 0)
            {
                perror("cannot send message");
                return -1;
            }
        }

        // await server reply
        int bytes_read = recv(sock, reply, sizeof(reply) - 1, 0);

        if (bytes_read > 0)
        {
            reply[bytes_read] = '\0';

            decode(reply, 15485863);

            puts(reply);
        }
        else if (bytes_read == 0)
        {
            puts("received no data; this is unusual so I'm bailing out");
            break;
        }
        else
        {
            perror("error performing recv()");
            break;
        }
    }

    close(sock);
    return 0;
}

```

P.S.  I noticed from your original code that you are compiling with the C99 standard; thus I have modified the code above to employ as much as that as possible.  I despise C89 style.

---

### Post by mu2we35 on 2013-06-21
Thank you very much for the correct code. I just want to know what you did with the code and where did the problem came from.
As to the previous code, I was a little frustrated when I got to run the code and it did not run. I have "cleaned" the code with your suggestions and with the help of -Wall. Now it doesn't even display the message. Could you help me ease my frustration. Thanks.

---

### Post by zobayer1 on 2013-06-22
> **mu2we35 said:**
> Thank you very much for the correct code. I just want to know what you did with the code and where did the problem came from.
As to the previous code, I was a little frustrated when I got to run the code and it did not run. I have "cleaned" the code with your suggestions and with the help of -Wall. Now it doesn't even display the message. Could you help me ease my frustration. Thanks.


Hi, your code is working fine as expected, When I write something, from client, it goes to server and when I write something in server, it goes to client. The program is not echoing anymore because you didn't send it back. I don't see any problem here, now you need check whether your encoding and decoding methods are working or not..

---

### Post by dwhitney67 on 2013-06-22
> **mu2we35 said:**
> I just want to know what you did with the code and where did the problem came from.


It is obvious (to me) from your previous postings that you have not carefully read the man-pages for recv() and send() [and btw, there's no need to use write()].

These functions do not guarantee that all the data will be received or sent with one call.  You, as the programmer, have to check to make sure that the recv() and send() have processed all the data.  That's is where checking the return value is of utmost importance.  Again with your latest code posting, you have not bothered to do this.

In layman's terms, never expect entire message from the client to be sent to the server, and vice versa.  A message may arrive in one or more packets.  So far with your testing, all messages have arrived in one packet, but don't bet on that for larger messages.  You need to continue calling recv(), when select() advises you to, until either one of the following conditions have been met:  1) you have received a complete message and 2) you have not exhausted the length of your receive buffer.

A good way to know that you have received a complete message (for a chat application) is to leave the newline character within the message that is transmitted.  You can check for the newline as the message is received.  If you want to remove the newline after the message is received, that is fine... but don't do it before the message is sent.  [Note, including the newline is merely one style of protocol; there are others... for example, you could preface the message with a value representing the string length, thus obviating the need to use an end-marker for the message.]

Critical to all of what I have described above is the control loops for receiving and sending data.  Use the select() to discern when it is appropriate to receive data; and use the results from the recv() to determine if you have received data or if the client has disconnected.  Similarly for the client, it will need to check if there server is available; if the server is gone, then usually after two send() calls an error is returned.

As for other advice, have you noticed how much similar code you have between your server and client?  Consider placing common code into another module that both the server and client can share.

P.S.  In the "corrected" code I provided earlier, the most notable fix I made was to append a null-character at the end of a received buffer.  I also demonstrated how to ensure that an entire message is transmitted via send().  I also revamped the remove_newline() function, and zeroed out the sockaddr_in objects before initializing them with values.  As an exercise left for you, I did not put any effort into the usage of recv() to check that a complete message had been received.

IMHO, take the code I gave to you earlier, sprinkle in the usage of fork() and select(), and then try to see if you can take common code from the server and client to form a third module.  Once you have done this and you have everything working, then consider developing a "get-next-message" utility that stores received data, and then returns a complete message if one is available.

---

### Post by mu2we35 on 2013-06-22
Thank you very much for your reply and help! I was able to finish the first code, with simple encryption on it and it communicated with server and client perfectly. I thank you dwhitney67, zobayer1 for your invaluable comments. I hope you are not irritated by my noobness in this matter. I have read the man pages and will read them. More power to all of you. I hope you will still help me in future c socket problems. Again, thank you. :)

---

