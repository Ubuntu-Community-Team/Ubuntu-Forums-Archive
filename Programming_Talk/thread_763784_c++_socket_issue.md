---
title: "c++ socket issue"
date: 2008-04-23
forum: Programming Talk
---

### Post by sileacan on 2008-04-23
I am sure there are a few things in this code that are not done as well as it could be, this is my first c++ application. I am looking to get help on an issue I am having.

Application: http proxy server
OS: Linux (fedora)
Code Language: c++
IDE: code blocks

My problem is that when I call recv on the socket that is connected to the http server (sending the browsers (client) request to the http server, and then getting the response back) it hangs.. to get around this i've tried using select.. but select always states that the socket is never ready to read. 

One way around this is to parse the response header to find out the content length.. and keep track of how much data has come back from recv and while currentlen<contentlen call recv again..

If someone could please help me figure out why it's hanging on the recv (should it not return 0 ????) or why select is always coming back saying that the socket is not ready to read..

I've stripped my application down to the bare bones for this.. no threading etc .. hopefully this helps to figure out the problem.

```

#include <iostream>

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <arpa/inet.h>
#include <errno.h>
#include <pthread.h>

#define INVALID_SOCKET -1

using namespace std;

int main()
{
    int ret = 0;

    cout<<"proxy server: 0.1b"<<endl;

    cout<<"setting up listening socket"<<endl;

    int _listen, _browser, _server;

    if((_listen=socket(AF_INET, SOCK_STREAM, 0))!=(signed int)INVALID_SOCKET)
    {
        cout<<"listening socket created"<<endl;
        cout<<"setting up listening socket address information"<<endl;

        sockaddr_in _listen_addr;
        bzero((char *) &_listen_addr, sizeof(_listen_addr));
        _listen_addr.sin_family = AF_INET;
        _listen_addr.sin_port = htons(8100);
        _listen_addr.sin_addr.s_addr = INADDR_ANY;

        char msg[100]; sprintf(msg, "attemping to bind listening socket to port %i", 8100);
        cout<<msg<<endl;

        if((bind(_listen, (sockaddr*)&_listen_addr, sizeof(_listen_addr)))!=(signed int)INVALID_SOCKET)
        {
            cout<<"bind successful!"<<endl;
            cout<<"attemping to listen"<<endl;

            while(1)
            {
                if((listen(_listen, 10))!=(signed int)INVALID_SOCKET)
                {
                    cout<<"server is now listening"<<endl;

                    sockaddr_in _browser_addr;

                    socklen_t browsersize = sizeof(_browser_addr);
                    if((_browser=accept(_listen, (sockaddr*)&_browser_addr, &browsersize))!=(signed int)INVALID_SOCKET)
                    {
                        char *ip = inet_ntoa(_browser_addr.sin_addr);
                        sprintf(msg, "received connection from ip: %s", ip);
                        cout<<msg<<endl;

                        char buffer[1024];
                        int _browser_len, _server_len;

                        cout<<"creating socket to communicate to http server"<<endl;
                        if((_server = socket(AF_INET, SOCK_STREAM, 0))!=(signed int)INVALID_SOCKET)
                        {
                            sockaddr_in _server_addr;
                            hostent *hostInfo;
                            hostInfo = gethostbyname("www.google.ca");

                            bzero((char *) &_server_addr, sizeof(_server_addr));
                            _server_addr.sin_family = AF_INET;
                            _server_addr.sin_port = htons(80);
                            bcopy((char *)hostInfo->h_addr, (char *)&_server_addr.sin_addr.s_addr, hostInfo->h_length);

                            fd_set fread, fwrite, fex;

                            FD_ZERO(&fread);
                            FD_ZERO(&fwrite);
                            FD_ZERO(&fex);
                            FD_SET(_server, &fread);
                            FD_SET(_server, &fwrite);
                            FD_SET(_server, &fex);

                            cout<<"connecting http server socket to the http server"<<endl;
                            if((connect(_server, (sockaddr*)&_server_addr, sizeof(_server_addr)))!=(signed int)INVALID_SOCKET)
                            {
                                cout<<"connected to http server"<<endl;
                                cout<<"attempting to receive request from browser"<<endl;
                                while((_browser_len = recv(_browser, buffer, sizeof(buffer), 0))>0)
                                {
                                    buffer[_browser_len] = '\0';
                                    cout<<"received request from browser: "<<endl<<"*******************************"<<endl<<buffer<<endl<<"*******************************"<<endl;

                                    cout<<"sending request to http server"<<endl;
                                    send(_server, buffer, _browser_len, 0);
                                    cout<<"attemping to receive response from server"<<endl;

                                    select(_server + 1, &fread, &fwrite, &fex, NULL);
//this if condition is always false even though i know the socket has data in it's buffer to read
//removing this if block will result in the code hanging on recv
//this is what i need help on
                                    if(FD_ISSET(_server, &fread))
                                    {
                                        cout<<"select = server sent data back!"<<endl;
                                        while((_server_len = recv(_server, buffer, sizeof(buffer), 0))>0)
                                        {
                                            buffer[_server_len] = '\0';
                                            cout<<"received response from server: "<<endl<<"*******************************"<<endl<<buffer<<endl<<"*******************************"<<endl;
                                            cout<<"sending response back to browser"<<endl;
                                            send(_browser, buffer, _server_len, 0);
                                        }
                                    }
                                    else
                                    {
                                        cout<<"select = server did not send data back!"<<endl;
                                    }
                                    cout<<"attempting to receive request from browser"<<endl;
                                }
                                close(_server);
                                close(_browser);
                            }
                            else
                            {
                                cout<<"failed to connect to http server: terminating server"<<endl;
                                break;
                            }
                        }
                        else
                        {
                            cout<<"failed to create http server socket: terminating server"<<endl;
                            break;
                        }
                    }
                }
                else
                {
                    cout<<"failed to listen: terminating server"<<endl;
                    break;
                }
            }

        }
        else
        {
            cout<<"bind failed: terminating server"<<endl;
        }

        cout<<"closing server"<<endl;
        close(_listen);
    }
    else
    {
        cout<<"failed to setup listening socket"<<endl;
    }

    return ret;
}

```

---

### Post by bite on 2008-04-23
you accept the _browser, but then you select on the _server... don't understand why.

---

### Post by sileacan on 2008-04-24
I select on the _server so that I can check to see if the _server socket is ready to have it's buffer read. 

Why wouldn't that make sense? I need to read and write to both sockets, why not check their availability?

I am not checking on the _browser socket, as I don't have an issue with it, select works.. I cut most of my code out in hopes that it would be easier for everyone to read so that I could get a quick response. I am only having trouble with my _server socket, so I left the problematic code in place.

---

### Post by bite on 2008-04-24
I have a limited experience with tcp/ip, but browsing my code that I know to work I find the following standard sequence in the servers:

- loop forever
-- select on all open fd's
-- if can read from the listening socket
--- accept
--- add the new fd (as returned by accept) to the set of fd's to be selected on
-- if can read from any other (already opened) socket
--- do what appropriate
- end loop

While instead what you are doing is opening a new socket after accepting. What is it for?

---

### Post by heikaman on 2008-04-24
I've just tried your code after removing the 
[PHP]
if(FD_ISSET(_server, &fread))
...
[/PHP]

and it works fine, I mean the browser received the page and this is the output from running the server and connecting with firefox to [http://localhost:8100](http://localhost:8100)

```

proxy server: 0.1b
setting up listening socket
listening socket created
setting up listening socket address information
attemping to bind listening socket to port 8100
bind successful!
attemping to listen
server is now listening
received connection from ip: 127.0.0.1
creating socket to communicate to http server
connecting http server socket to the http server
connected to http server
attempting to receive request from browser
received request from browser: 
*******************************
GET / HTTP/1.1

Host: localhost:8100

User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept-Language: en-us,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Keep-Alive: 300

Connection: keep-alive




*******************************
sending request to http server
attemping to receive response from server
received response from server: 
HTTP/1.1 200 OK

Cache-Control: private

Content-Type: text/html; charset=UTF-8

Content-Encoding: gzip

Date: Thu, 24 Apr 2008 13:26:21 GMT

Server: gws

Content-Length: 1720



&#8249;
sending response back to browser
received response from server: 
µ&#8230;&#353;LÂðM:2Sé$ZÑ"ñ¬Pë(V«&#376;\ÇDÎLpÁèà£&#8222;<®¬h3ÑÐÄN&#8225;Ù @&#732;WR&#8250;*5&#381;*%ä¥7 bb`&#8364;ÚÅ	 ótæ&#8364;W&#710;p&#352;U&#8218;9·kàeï/ÎJX¿&#8364;'&#8226;&#8249;&#352;[&#8250;^¡&#8230;ï*&#8222;&#8240;Cáê8:&#8482;&#8222;[&#353;N/Î-íi&#8217;xîpñ\p!W
×}àNrÏÏÏã¬&#8220;s«³¶¹r®3ÉóØæMCÆx«<&#352;rÐï%*h^À&#8212;&#376;%gºêÀpON!Õá&#8211;©À+
ÀÊCÏiRôÞk&#8249;Ñº×~{&ª
ÊiaÁýj4ÚéÄB(o)ßÉÂO&#381;|_uÍ/ï&#381;
sending response back to browser
received response from server: 
:YìQ8ájr&#338;¥t&#8221;U}%©»Ö8&#381;A&#382;É&#352;y &#8222;3r&#8212;xÝ&#353;`¿LÅôÐK[±Ð&#8211;C¿7Ë&#8211;z?&#402;RÕÏdP&#376;&#8221;Á&#8225;ÖÏÉ
sending response back to browser

```

Edit: There's definitely an issue with style and unnecessary code, but other than that it works fine.

---

### Post by sileacan on 2008-04-24
Yes I get that far too.. but the problem is that it loops back around to the recv function for the _server socket.. when there isn't any data left to read, but as the server didn't close the connection, recv doesn't return 0.. thus my ever lasting hang issue.

To get around this I used the setsockopt on the RCVTIMEO. This works but I hate having to rely on the socket to timeout in order to have recv return. 

Actually the best way that I've avoided this issue is to parse the content-length out of the header and then keep track of how much data is still coming from the server. This is the best approach, but still leaves me wondering why FD_ISSET returns false when you yourself have tried and seen that there is data present in the _server buffer!?

Any tips on how to improve the code? what should I clean up? The actual application is quite a bit larger so anything I can do to help eliminate code bloat the better.

Thanks!!

---

### Post by heikaman on 2008-04-25
> **sileacan said:**
>  but as the server didn't close the connection, recv doesn't return 0.. thus my ever lasting hang issue.


It doesn't "hang", the server closes the connection and recv returns 0 after a minute or so.

This **delay** is completely normal, because if you actually read the http request you'll find at the beginning:
[PHP]
GET / HTTP/1.1
[/PHP]

and at the end:
[PHP]
Keep-Alive: 300
Connection: keep-alive
[/PHP]

In HTTP/0.9 and 1.0, the connection is closed after a single request/response pair. In HTTP/1.1 a keep-alive-mechanism was introduced, where a connection could be reused for more than one request.
see:
[http://en.wikipedia.org/wiki/HTTP#Persistent_Connections]("http://en.wikipedia.org/wiki/HTTP#Persistent_Connections")

So if you really want the server to close the connection immediately after one request/response pair you have to implicitly specify that, by replacing the:
[PHP]
Connection: keep-alive
[/PHP] 
with:
[PHP]
Connection: close
[/PHP]
like this:
[PHP]
const char* tag="Connection: close\r\n\r\n";

//receive request from browser:
...

strcpy(strstr(buffer, "Connection:"), tag);

//send request to server
...
[/PHP]

EDIT: or by closing your side of the connection after receiving the complete response (using the content-length like you did).

Normally I wouldn't do/recommend this (I just wanted to explain why the connection wasn't closed immediately) instead I would **fork** a process/thread to handle the browser request.

---

### Post by sileacan on 2008-04-25
I create a thread to handle each new request. It's omitted from this code to help limit the amount of code people would have to go through in order to help me.

I see that in the request, and I thought that should happen, but unfortunately for me at least it isn't the case. Recv sits there.. infact I left it for a number of hours by accident when I went out one evening.. and to my surprise the code was still stuck waiting for recv to return. I thought for sure the connection would close on the servers side, thus sending me a 0 and then I'd be able to exit from the loop..

Right now using setsockopt on the recieve timeout and keeping track of the content length seems to be doing the trick.. but it still puzzles me why select/recv doesn't seem to be working the way I thought. Maybe they work diffferently from what I understood.

Anyway, thanks for taking the time to post a few responses, it's appreciated.

---

### Post by heikaman on 2008-04-25
> **sileacan said:**
> the code was still stuck waiting for recv to return...

Are you sure that recv was blocking on _server fd (i.e. waiting for the server) not on _browser fd (i.e. waiting for the browser)? 

because if recv blocks on the _browser fd it will wait for ever for the browser to send a request again.

---

