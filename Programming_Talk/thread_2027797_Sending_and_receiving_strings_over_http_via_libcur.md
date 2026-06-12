---
title: "Sending and receiving strings over http via libcurl"
date: 2012-07-17
forum: Programming Talk
---

### Post by solidsplint on 2012-07-17
I have a situation where my program on a server (windows machine) outputs some strings. I need to send those strings from the server to the client (Linux machine) via HTTP using curl. Once sent I am to receive the data on the client side as string, decode it and perform subsequent actions. I already achieved this functionality using C Sockets using berkely API as I had familiarity with that. But for some reason I am not allowed to use a program of my own using sockets. I poked around and seems CURL can be my solution. However I am very new to curl and cant seem to figure out how to achieve this functionality. On the Client side I found this from the ubuntu forums to be useful may be: [HTML]http://ubuntuforums.org/archive/index.php/t-1435926.html[/HTML]

```
#include <curl/curl.h>
#include <cstdio>
#include <string>

std::string buffer;

size_t curl_write( void *ptr, size_t size, size_t nmemb, void *stream)
{
buffer.append((char*)ptr, size*nmemb);
return size*nmemb;
}

int main(int argc, char **argv)
{
CURL *curl = curl_easy_init();
curl_easy_setopt(curl, CURLOPT_URL, "http://ubuntuforums.org"); 
curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, curl_write);
curl_easy_perform(curl);
curl_easy_cleanup(curl);
fwrite( buffer.c_str(), buffer.length(), sizeof(char), stdout);
return 0;
}
```
I understand that you have to use the write back functions to receive data ? Also on the client side I need to develop a program using curl that whenever the server sends over a string, it should receive it and decode it. Any pointers to tutorials related to the specific problems will be highly appreciated. Or if someone has already tried this I'll highly appreciate any help here. Thanks.

---

### Post by the_unforgiven on 2012-07-17
Can you be a bit more specific?
Or post the code that you've tried for your problem?

Does it need to be done using C/C++?
Why not just write a perl/php/python script on your linux machine and run it using a standard webserver if your windows app needs to just call an HTTP url from your linux machine?

---

### Post by solidsplint on 2012-07-17
Hi unforgiven,
Yes I have to implement this using C/C++.
The problem here is that I need to send a string from a windows machine to a linux machine (on the same subnet at the moment). I want to "post" the string in http query and receive and decode it on the other hand.

---

### Post by the_unforgiven on 2012-07-17
> **solidsplint said:**
> Hi unforgiven,
Yes I have to implement this using C/C++.
The problem here is that I need to send a string from a windows machine to a linux machine (on the same subnet at the moment). I want to "post" the string in http query and receive and decode it on the other hand.

In that case, does it have to follow HTTP?
Or, simple custom message passing between the two entities will suffice?

Is it that you're trying to open a socket from windows machine to the linux machine manually and then composing the HTTP request by hand?

Will it be possible for you to share the code for both the sides (windows as well as linux)? so that it's easier to pin-point the actual problem.

Besides, libcurl is a *client-only* library:
[http://stackoverflow.com/questions/6226068/how-to-use-libcurl-as-server](http://stackoverflow.com/questions/6226068/how-to-use-libcurl-as-server)

---

### Post by solidsplint on 2012-07-17
I have achieved the functionality using berkely socket API. That is I created a client program on windows and a server on linux. The client sent the string using standard send() methods and I received it fine on the server.
However I am not allowed to use the socket programs. I just have to figure out a way to use some standard http (or an alternative ?) method to send the string from a windows machine to the other machine on the same network using any method whatsoever which does not involve creating your own program on windows.
I used libcurl as it as a standard utility that can be used to post strings to http servers. If there is some alternative method I will be very happy to try it.
I havent actually written much code that can be shared as I am still looking for a starting point here :(

---

