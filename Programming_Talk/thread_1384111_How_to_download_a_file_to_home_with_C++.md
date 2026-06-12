---
title: "How to download a file to home with C++"
date: 2010-01-18
forum: Programming Talk
---

### Post by shababhsiddique on 2010-01-18
I have heard that it is possible to download a file from link using C++ wanna know how. help me downloading the simple file in C++

[]("http://3.bp.blogspot.com/_I2X40Rw3Mog/Saus9LfBVZI/AAAAAAAAABY/k2sSSJZomN4/s1600-h/seek+patience.jpg")[ftp://ftp.gnu.org/pub/gnu/wget/wget-latest.tar.gz](ftp://ftp.gnu.org/pub/gnu/wget/wget-latest.tar.gz)

curl doesnot seem to download a file , it just access the html code for some reason I cant even try curl since last install, under linker settings which file should I add? libcurl.so.x.x?

I am a not very good in C++ but got the basics, try to be simple

---

### Post by dwhitney67 on 2010-01-18
You should read here:
[http://curl.haxx.se/libcurl/using/](http://curl.haxx.se/libcurl/using/)

And here (for programming examples):
[http://curl.haxx.se/libcurl/c/example.html](http://curl.haxx.se/libcurl/c/example.html)

Edit:  Added example below...
```

#include <curl/curl.h>
#include <libgen.h>
#include <stdio.h>

size_t writeData(void* ptr, const size_t size, const size_t nmemb, FILE* stream)
{
   return fwrite(ptr, size, nmemb, stream);
}

int main(int argc, char** argv)
{
   CURL* curl = curl_easy_init();

   if (curl)
   {
      const char* url      = argv[1];
      const char* filename = basename((char*)url);
      FILE*       ofile    = fopen(filename, "wb");

      if (ofile)
      {
         curl_easy_setopt(curl, CURLOPT_URL, url);
         curl_easy_setopt(curl, CURLOPT_WRITEDATA, ofile);
         curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, writeData);

         curl_easy_perform(curl);

         fclose(ofile);
      }

      /* always cleanup */
      curl_easy_cleanup(curl);
   }

   return 0;
}

```
To build:
```

gcc getURL.c -lcurl

```

---

### Post by shababhsiddique on 2010-01-21
sorry for late response..
I cant get my curl work.It says xxCURLxx not found/not declared....blah blah blah...

 here is how my linker looks like.

---

### Post by dwhitney67 on 2010-01-21
IMO, IDEs tend to numb the mind, and hence one's progress/knowledge in the field of s/w development.  Why not consider using the command line to build your applications before jumping into using code::blocks?

Nevertheless, based on the screen shot you provided, it looks like you are not specifying the library correctly.  Remove the two entries you entered, and instead enter "curl", of course, without the quotes.

---

### Post by s3a on 2010-01-21
I don't know anything about this but I just wanted to add that the geany IDE (don't know about others) lets you use a built-in terminal that can automatically go to the directory of your program's files by right clicking and selecting the option. This allows for convenient usage of the "troublesome" way of doing things. (answer to the numbing the mind comment)

---

### Post by shababhsiddique on 2010-01-22
> **dwhitney67 said:**
> IMO, IDEs tend to numb the mind, and hence one's progress/knowledge in the field of s/w development.  Why not consider using the command line to build your applications before jumping into using code::blocks?


ARE YOU SURE????? IDE to COMMAND LINE??? I AM NOT THAT GEEK  ( YET!! ) I shall be pleased if you show me the path ....!.... were can I learn this thinks?? I havent got any book about it... books here seem to just stay upto "compiling from command"

> **dwhitney67 said:**
> 
Nevertheless, based on the screen shot you provided, it looks like you are not specifying the library correctly. Remove the two entries you entered, and instead enter "curl", of course, without the quotes.

Well I know that I am entering a wrong linker, I know it is curl but could not find the actual .so / .a / .lib /.bundle name.......... Plz anyone tell me what is the actual linker name and were is it located???? /lib*  .. /usr/lib* .... I am new to ubuntu donno where are those stuff saved?. Entering simply "curl" or "CURL" does not work(of course without quotes! ) . consider that

---

### Post by Zugzwang on 2010-01-22
Ok, two things:

- Please copy & paste the precise error message you get. "Not declared" and "Not found" are two different things. 

- Then, if just adding "curl" as a library does not work, consider this: you probably do not have have the libcurl development package installed (either libcurl4-gnutls-dev or libcurl4-openssl-dev).

---

### Post by shababhsiddique on 2010-01-22
> **Zugzwang said:**
> Ok, two things:

- Please copy & paste the precise error message you get. "Not declared" and "Not found" are two different things. 

- Then, if just adding "curl" as a library does not work, consider this: you probably do not have have the libcurl development package installed (either libcurl4-gnutls-dev or libcurl4-openssl-dev).

here is it

---

### Post by dwhitney67 on 2010-01-23
It was suggested that you consider doing two things, yet it appears that you only did one of them.

Please, install the curl development library on your system!
```

sudo apt-get install libcurl4-openssl-dev

```

When you are done, you should be able to list the libcurl files using a typical terminal:
```

$ ls-l /usr/lib/libcurl*
-rw-r--r-- 1 root root 378518 2009-08-13 18:07 /usr/lib/libcurl.a
lrwxrwxrwx 1 root root     19 2009-11-12 17:18 /usr/lib/libcurl-gnutls.so.3 -> libcurl-gnutls.so.4
lrwxrwxrwx 1 root root     23 2009-11-12 17:18 /usr/lib/libcurl-gnutls.so.4 -> libcurl-gnutls.so.4.1.1
-rw-r--r-- 1 root root 256384 2009-08-13 18:07 /usr/lib/libcurl-gnutls.so.4.1.1
-rw-r--r-- 1 root root    929 2009-08-13 18:07 /usr/lib/libcurl.la
lrwxrwxrwx 1 root root     16 2010-01-18 14:11 /usr/lib/libcurl.so -> libcurl.so.4.1.1
lrwxrwxrwx 1 root root     12 2009-11-12 17:32 /usr/lib/libcurl.so.3 -> libcurl.so.4
lrwxrwxrwx 1 root root     16 2009-11-12 17:32 /usr/lib/libcurl.so.4 -> libcurl.so.4.1.1
-rw-r--r-- 1 root root 273020 2009-08-13 18:07 /usr/lib/libcurl.so.4.1.1

```

---

### Post by shababhsiddique on 2010-01-24
Thanks for the reply .... 


I think I would restore my system . ..  Is it causing from the update crash???(I have poor Internet connection here, the update error occurred a few day ago..)

---

### Post by dwhitney67 on 2010-01-24
Maybe I made a mistake; maybe it is this package that you need to install:  libcurl4-gnutls-dev

---

### Post by shababhsiddique on 2010-01-25
> **dwhitney67 said:**
> Maybe I made a mistake; maybe it is this package that you need to install:  libcurl4-gnutls-dev

thanks again for the reply

Well re-installing my system solved it....! May be it was due to the update crash..

You were right curl+ libcurl4-openssl-dev was enough... anyway what is in -   libcurl4-gnutls-dev? its not installed yet but still working.

Thanks again for your kind help..

---

