---
title: "Codeblocks c++ linking curl lib ?"
date: 2011-04-29
forum: Programming Talk
---

### Post by highspider on 2011-04-29
I have a very basic curl program to display a google web page.
```

/***************************************************************************
 * Project CURL
 * ORIGANL AOURTER, Daniel Stenberg, <daniel@haxx.se>, et al.
 * EDITED: highspdier
 ***************************************************************************/
#include <stdio.h>
#include <curl/curl.h>
#include <iostream>
using namespace std;

int main(void)
{
  CURL *curl;
  CURLcode res;

  curl = curl_easy_init();
  if(curl) {
    curl_easy_setopt(curl, CURLOPT_URL, "http://www.google.com");
    res = curl_easy_perform(curl);

    cout << res;
    /* always cleanup */
    curl_easy_cleanup(curl);
  }
  return 0;
}

```I CAN build the main from commandline it works 100%
```
g++ -lcurl main.cpp -o build
```
But have no idea how to link the library or do what ever it is i need to do to make it work inside code blocks.

---

### Post by highspider on 2011-04-29
Solved-


opened code blocks.  settings->complier - debugging settinges->
  selected the the tab "Linker settings"  went to add

 /usr/lib/libcurl-gnutls.so.4.2.0

done

---

