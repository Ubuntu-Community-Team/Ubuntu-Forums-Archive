---
title: "C++ and Internet"
date: 2007-06-06
forum: Programming Talk
---

### Post by Redscare on 2007-06-06
I am trying to write a program that would search multiple search engines at once in a certain way. Can anyone tell me how to access a website/download a webpage (for example, download the source of [http://www.ubuntuforums.org](http://www.ubuntuforums.org)) using purely C++? Thank you.

---

### Post by treak007 on 2007-06-06
There are no means to allow for internet access from the standard  C++ libraries. One thought would be to use the system function in stdlib.h to use something like wget perhaps. Something like


```
#include<stdlib.h>

int main(void)
{ 
      system("wget www.google.com");
}

```


that would download the index.html file from google. You could then parse this file to access the data within.

Hope that helps.

---

### Post by PandaGoat on 2007-06-06
It is quite complicated so I will only tell your the theory and not show code.  HTTP is a protocol, hypertext transfer protocol.  You use sockets to connect to servers, ip addresses, and "talk" to them.  You send a message, it sends one back.  The messages that you send are in a specific format based on what protocol the server uses.  In this case, HTTP.  

1.  Connect to some web site's ip
2. Request a byte transfer of w/e .html file [or w/e]
3.  Receive the data the server sends to your socket

In HTTP's case you would use a TCP client to connect to a server on usually port 80.

[ Wikipedia has good explanation of sending requests to a server ](http://en.wikipedia.org/wiki/HTTP)

[Good tutorial for sockets](http://beej.us/guide/bgnet/output/html/multipage/index.html)
I wrote some code for a socket client a while back:

[client.h](http://pandagoat.googlepages.com/client.h)
[client.cpp](http://pandagoat.googlepages.com/client.cpp)

---

### Post by neo.patrix on 2007-06-07
Hi 

What exactly you want to do? Create a search portal....

As far as I know, C++ is not very good choice of language for playing around internet. 

But I would suggest using Webservices (WSDL)s, normally there are many libraries in Java
to handle webservices, I am not sure about C++, but there should be because , ulimately java works on JNI for performace reasons. 

Google provides webservices and also APIs to use that services, I thin k you can download all that and lot more from [http://labs.google.com/?tab=wz](http://labs.google.com/?tab=wz)

rgds,
Patrix.

---

### Post by Redscare on 2007-06-07
Thank you for the quick replies, and I will do the reading, but I have a very specific humble request now after doing some reading; could someone please post source code that downloads the source of 
```
http://www.google.com/search?hl=en&q=redscare&btnG=Google+Search
```
and prints it to the command line?
Thanks again.

---

### Post by WW on 2007-06-07
What do you mean when you say "the source of..."?

EDIT: Nevermind, I'm slow... :)

---

### Post by pmasiar on 2007-06-07
check ie this Python examples:
[http://www.voidspace.org.uk/python/articles/urllib2.shtml](http://www.voidspace.org.uk/python/articles/urllib2.shtml)
[http://docs.python.org/lib/module-urllib.html](http://docs.python.org/lib/module-urllib.html)

---

### Post by winch on 2007-06-07
Check out libcurl
[http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/)

Simple C example.

```
#include <stdio.h>
#include <curl/curl.h>

int main()
{
    CURL *handle;
    handle = curl_easy_init();
    if (handle == NULL)
    {
        printf("curl init failed!");
        return 1;
    }
    curl_easy_setopt(handle, CURLOPT_FOLLOWLOCATION, 1);
    curl_easy_setopt(handle, CURLOPT_URL, "http://www.google.com/search?hl=en&q=redscare&btnG=Google+Search");
    curl_easy_perform(handle);
    curl_easy_cleanup(handle);
    return 0;
}

```

Save as main.c then compile and run with with

```
gcc -Wall `curl-config --cflags --libs` main.c -o curl_test
./curl_test
```

---

### Post by jfinkels on 2007-06-07
Do it in python, it's simple.

---

### Post by rich.bradshaw on 2007-06-07
or just in a terminal

curl [www.somesitehere.com](www.somesitehere.com)

---

### Post by Redscare on 2007-06-07
So is there no way to do this purely with the files provided in advance with the compiler (C++)? Also, how could I obtain the text off of a webpage? (for example, the results of [http://www.google.com/search?hl=en&q=redscare&btnG=Google+Search](http://www.google.com/search?hl=en&q=redscare&btnG=Google+Search)) Thanks again for the quick responses.

---

### Post by WW on 2007-06-07
Follow the link provided by winch, and read the libcurl documentation.

Here is a C++ variation of the program that winch provided.  This version saves the entire web page in a string:

**ctest.cpp**
```

#include <iostream>
#include <string>
#include <curl/curl.h>

using namespace std;

string html;

size_t write_data_callback(char *ptr, size_t size, size_t nmemb, void *stream)
{
    if (size*nmemb > 0)
    {
        char tmp = *(ptr+size*nmemb-1);
        *(ptr+size*nmemb) = '\0';
        html.append(ptr);
        html.append(1,tmp);
    }
    return size*nmemb;
}

int main()
{
    CURL *handle;
    handle = curl_easy_init();
    if (handle == NULL)
    {
        printf("curl init failed!");
        return 1;
    }
    curl_easy_setopt(handle, CURLOPT_FOLLOWLOCATION, 1);
    curl_easy_setopt(handle, CURLOPT_WRITEFUNCTION, write_data_callback);
    curl_easy_setopt(handle, CURLOPT_URL, "http://www.google.com/search?hl=en&q=redscare&btnG=Google+Search");
    html = "";
    curl_easy_perform(handle);
    curl_easy_cleanup(handle);
    cout << "The first 25 characters: " << html.substr(0,25) << endl;
    cout << "The 25 characters starting from the first occurrence of \"<body\": " << html.substr(html.find("<body",0),25) << endl;
    return 0;
}

```

Compile and run:
```

$ g++ -Wall `curl-config --cflags --libs` ctest.cpp -o ctest
$ ./ctest
The first 25 characters: <html><head><meta http-eq
The 25 characters starting from the first occurrence of "<body": <body bgcolor=#ffffff onl
$

```

---

### Post by WW on 2007-06-07
> **Redscare said:**
> So is there no way to do this purely with the files provided in advance with the compiler (C++)?
If you mean without some sort of external library, no.  For a language in which libraries like this are "built-in", you want python (which adopts the "batteries included" philosophy).

---

### Post by kknd on 2007-06-07
Please, Java or Python would be much better in this case! Both where made with internet in mind (at least Java =) )

---

