---
title: "C++ String URL Reading"
date: 2008-05-03
forum: Programming Talk
---

### Post by solarwind on 2008-05-03
Hey all,

How do you read the content of a web page into a string? For example, I want to read the html source of google.com into a string.

---

### Post by WW on 2008-05-04
You can use the [libcurl](http://curl.haxx.se/libcurl/) library in C++.

For example, this quick demonstration puts the contents of a web page into a string, and then prints the string.

**curltest.cpp**
[php]
//
// curltest.cpp
//

#include <string>
#include <iostream>
#include <curl/curl.h>

using namespace std;

//
// For this demonstration, the contents of the web page are put
// into this global variable.
//
string contents;

//
// This is the callback function that is called by
// curl_easy_perform(curl)
//
size_t handle_data(void *ptr, size_t size, size_t nmemb, void *stream)
    {
    int numbytes = size*nmemb;
    // The data is not null-terminated, so get the last character, and replace
    // it with '\0'.
    char lastchar = *((char *) ptr + numbytes - 1);
    *((char *) ptr + numbytes - 1) = '\0';
    contents.append((char *)ptr);
    contents.append(1,lastchar);
    *((char *) ptr + numbytes - 1) = lastchar;  // Might not be necessary.
    return size*nmemb;
    }

int main(int argc, char *argv[])
    {
    if (argc != 2)
        {
        cerr << "use: curltest url\n";
        return -1;
        }

    CURL* curl = curl_easy_init();
    if(curl)
        {
        // Tell libcurl the URL
        curl_easy_setopt(curl,CURLOPT_URL, argv[1]);
        // Tell libcurl what function to call when it has data
        curl_easy_setopt(curl,CURLOPT_WRITEFUNCTION,handle_data);
        // Do it!
        CURLcode res = curl_easy_perform(curl);
        curl_easy_cleanup(curl);
        if (res == 0)
            cout << contents << endl;
        else
            cerr << "Error: " << res << endl;
        }
    return 0;
    }
[/php]

Compile and run:
```

$ g++ -Wall curltest.cpp `pkg-config --cflags --libs libcurl` -o curltest
$ ./curltest www.google.com     
<html><head><meta http-equiv="content-type" content="text/html; charset=ISO-8859-1"><title>Google</title>
[...snip...]
<a href="/intl/en/about.html">About Google</a></font><p><font size=-2>&copy;2008 Google</font></p></center></body></html>
$ 

```
To use the library, the Ubuntu package to install is either libcurl4-openssl-dev or libcurl4-gnutls-dev (you have a choice).

---

### Post by solarwind on 2008-05-04
> **WW said:**
> You can use the [libcurl](http://curl.haxx.se/libcurl/) library in C++.

For example, this quick demonstration puts the contents of a web page into a string, and then prints the string.

**curltest.cpp**
[php]
//
// curltest.cpp
//

#include <string>
#include <iostream>
#include <curl/curl.h>

using namespace std;

//
// For this demonstration, the contents of the web page are put
// into this global variable.
//
string contents;

//
// This is the callback function that is called by
// curl_easy_perform(curl)
//
size_t handle_data(void *ptr, size_t size, size_t nmemb, void *stream)
    {
    int numbytes = size*nmemb;
    // The data is not null-terminated, so get the last character, and replace
    // it with '\0'.
    char lastchar = *((char *) ptr + numbytes - 1);
    *((char *) ptr + numbytes - 1) = '\0';
    contents.append((char *)ptr);
    contents.append(1,lastchar);
    *((char *) ptr + numbytes - 1) = lastchar;  // Might not be necessary.
    return size*nmemb;
    }

int main(int argc, char *argv[])
    {
    if (argc != 2)
        {
        cerr << "use: curltest url\n";
        return -1;
        }

    CURL* curl = curl_easy_init();
    if(curl)
        {
        // Tell libcurl the URL
        curl_easy_setopt(curl,CURLOPT_URL, argv[1]);
        // Tell libcurl what function to call when it has data
        curl_easy_setopt(curl,CURLOPT_WRITEFUNCTION,handle_data);
        // Do it!
        CURLcode res = curl_easy_perform(curl);
        curl_easy_cleanup(curl);
        if (res == 0)
            cout << contents << endl;
        else
            cerr << "Error: " << res << endl;
        }
    return 0;
    }
[/php]

Compile and run:
```

$ g++ -Wall curltest.cpp `pkg-config --cflags --libs libcurl` -o curltest
$ ./curltest www.google.com     
<html><head><meta http-equiv="content-type" content="text/html; charset=ISO-8859-1"><title>Google</title>
[...snip...]
<a href="/intl/en/about.html">About Google</a></font><p><font size=-2>&copy;2008 Google</font></p></center></body></html>
$ 

```
To use the library, the Ubuntu package to install is either libcurl4-openssl-dev or libcurl4-gnutls-dev (you have a choice).

1. Thanks!
2. I don't use Ubuntu, I use Arch Linux :P
3. I was looking at the curlpp library (cURL c++ wrapper).

---

