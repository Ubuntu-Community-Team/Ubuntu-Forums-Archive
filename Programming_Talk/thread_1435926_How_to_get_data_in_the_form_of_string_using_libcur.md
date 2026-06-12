---
title: "How to get data in the form of string using libcurl"
date: 2010-03-22
forum: Programming Talk
---

### Post by bilalakhtar on 2010-03-22
Hi people,
Iam using libcurl from a C++ program. I want to make a Twitter client, with all calls to the API being made by libcurl. I am successful to some extent (my program can send tweets) but I can't get the tweets using libcurl in string form. Here is some code spec:-
[PHP]CURL* handle = curl_easy_init();
curl_easy_setopt(handle,CURLOPT_URL,"http://api.twitter.com/1/statuses/home_timeline.xml");
curl_easy_setopt(handle,CURLOPT_USERPWD,m_userpwd.c_str());[/PHP]

I want to put the data in a Glib::ustring called m_tweets, which I could later on parse using libxml++ and display the tweets to the user.
I have searched the net for solutions, but most of the solutions cause a segfault for me.

---

### Post by bilalakhtar on 2010-03-23
bump? :popcorn: :guitar: :-({|=\\ :D/

---

### Post by heikaman on 2010-03-23
I don't see the problem here ? I'm assuming that you set the callback function using the CURLOPT_WRITEFUNCTION, right ? here's a small example:

[PHP]#include <curl/curl.h>

size_t curl_write( void *ptr, size_t size, size_t nmemb, void *stream)
{
    return fwrite(ptr, size, nmemb, stdout);
}

int main(int argc, char **argv)
{
    CURL *curl = curl_easy_init();
    curl_easy_setopt(curl, CURLOPT_URL, "http://ubuntuforums.org"); 
    curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, curl_write);
    curl_easy_perform(curl);
    curl_easy_cleanup(curl);
}
[/PHP]

Compile with:
[PHP]
gcc test.c -o test -lcurl && ./test[/PHP]

---

### Post by falconindy on 2010-03-23
It's slightly more involved to actually get it into a string, since the recv() call that triggers the write callback is buffered. The easiest way (i've found) is to declare struct that contains a char* and a integer value to keep track of how much you've written so that you can append after that.

```
#include <curl/curl.h> 
#include <stdlib.h>
#include <string.h>

#define BUFFER_SIZE     (256 * 1024) /* 256kB */

struct write_result {
    char *data;
    int pos;
};

static size_t curl_write( void *ptr, size_t size, size_t nmemb, void *stream) {

    struct write_result *result = (struct write_result *)stream;

    /* Will we overflow on this write? */
    if(result->pos + size * nmemb >= BUFFER_SIZE - 1) {
        fprintf(stderr, "curl error: too small buffer\n");
        return 0;
    }

    /* Copy curl's stream buffer into our own buffer */
    memcpy(result->data + result->pos, ptr, size * nmemb);

    /* Advance the position */
    result->pos += size * nmemb;

    return size * nmemb;
} 


int main(int argc, char **argv) {
    CURL *curl = curl_easy_init(); 
    char *data;

    /* Create the write buffer */
    data = malloc(BUFFER_SIZE);
    if (! data)
        fprintf(stderr, "Error allocating %d bytes.\n", BUFFER_SIZE);

    struct write_result write_result = {
        .data = data,
        .pos = 0
    };

    /* Set curl's parameters */
    curl_easy_setopt(curl, CURLOPT_URL, "http://ubuntuforums.org");
    curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, curl_write);
    curl_easy_setopt(curl, CURLOPT_WRITEDATA, &write_result);

    curl_easy_perform(curl);

    /* null terminate the string */
    data[write_result.pos] = '\0';

    /* Print what we got. can't use printf because the data is too big */
    fwrite(data, write_result.pos, sizeof(char), stdout);

    /* Don't forget to free your memory! */
    free(data);
    curl_easy_cleanup(curl);
    curl_global_cleanup();

}
```

I know this is C and not C++, but it should get you started (and it's what I wrote over the weekend >.>).

---

### Post by bilalakhtar on 2010-03-24
> **falconindy said:**
> It's slightly more involved to actually get it into a string, since the recv() call that triggers the write callback is buffered. The easiest way (i've found) is to declare struct that contains a char* and a integer value to keep track of how much you've written so that you can append after that.

```
#include <curl/curl.h> 
#include <stdlib.h>
#include <string.h>

#define BUFFER_SIZE     (256 * 1024) /* 256kB */

struct write_result {
    char *data;
    int pos;
};

static size_t curl_write( void *ptr, size_t size, size_t nmemb, void *stream) {

    struct write_result *result = (struct write_result *)stream;

    /* Will we overflow on this write? */
    if(result->pos + size * nmemb >= BUFFER_SIZE - 1) {
        fprintf(stderr, "curl error: too small buffer\n");
        return 0;
    }

    /* Copy curl's stream buffer into our own buffer */
    memcpy(result->data + result->pos, ptr, size * nmemb);

    /* Advance the position */
    result->pos += size * nmemb;

    return size * nmemb;
} 


int main(int argc, char **argv) {
    CURL *curl = curl_easy_init(); 
    char *data;

    /* Create the write buffer */
    data = malloc(BUFFER_SIZE);
    if (! data)
        fprintf(stderr, "Error allocating %d bytes.\n", BUFFER_SIZE);

    struct write_result write_result = {
        .data = data,
        .pos = 0
    };

    /* Set curl's parameters */
    curl_easy_setopt(curl, CURLOPT_URL, "http://ubuntuforums.org");
    curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, curl_write);
    curl_easy_setopt(curl, CURLOPT_WRITEDATA, &write_result);

    curl_easy_perform(curl);

    /* null terminate the string */
    data[write_result.pos] = '\0';

    /* Print what we got. can't use printf because the data is too big */
    fwrite(data, write_result.pos, sizeof(char), stdout);

    /* Don't forget to free your memory! */
    free(data);
    curl_easy_cleanup(curl);
    curl_global_cleanup();

}
```

I know this is C and not C++, but it should get you started (and it's what I wrote over the weekend >.>).

Sorry, falconindy, This solution causes a segfault for me, even though it compiles fine. I found exactly same solutions on the net, which didn't work.

---

### Post by heikaman on 2010-03-24
> **bilalakhtar said:**
> Sorry, falconindy, This solution causes a segfault for me, even though it compiles fine. I found exactly same solutions on the net, which didn't work.

1) falconindy's code doesn't segfault
2) another way:
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

---

### Post by bilalakhtar on 2010-03-26
Thanks, heikman,
[SIZE="7"][COLOR="Red"]IT WORKS![/COLOR][/SIZE]

---

