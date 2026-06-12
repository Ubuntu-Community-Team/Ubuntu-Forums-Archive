---
title: "C/C++ library to read web pages. (not curl)"
date: 2008-11-06
forum: Programming Talk
---

### Post by unoodles on 2008-11-06
Hey, I am looking for a simple C or C++ library to read web pages.
I has to be very simple to use. The reason I dislike libcurl is because I want to read it into a string/char*. libcurl allows this but IMO its not simple/straight forward enough. What would be best is if there was a library as simple as python's urllib. Also, it would have to be pretty platform independent.
Thanks.

---

### Post by curvedinfinity on 2008-11-06
From my experience, curl-simple is the simplest. :(

---

### Post by WW on 2008-11-06
I know you said you didn't want curl, but just in case someone else is searching for similar information...

The example that I show in [this thread](http://ubuntuforums.org/showthread.php?t=781021) uses libcurl in a C++ program to store the contents of a web page in a string.  There is also a C++ binding for libcurl called curlpp that might have a nicer interface, but I haven't tried it.

---

### Post by StOoZ on 2008-11-07
the issue with curlpp , is that it doesnt have any good references / tutorials over the web , so you end up reading cURL stuff anyway.
just dig in and use cURL , I did it with C++.

---

### Post by LaRoza on 2008-11-07
> **unoodles said:**
> What would be best is if there was a library as simple as python's urllib. 

Well, that is the difference between the languages ;)

---

### Post by slavik on 2008-11-07
like LWP in Perl?

---

### Post by LaRoza on 2008-11-07
> **slavik said:**
> like LWP in Perl?

Yes, but this is C or C++ (or this mystery language "C/C++"), not Perl.

---

