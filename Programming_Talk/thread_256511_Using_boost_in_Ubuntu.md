---
title: "Using boost in Ubuntu"
date: 2006-09-13
forum: Programming Talk
---

### Post by nullmind on 2006-09-13
I'm using Anjuta to code in C/C++ and I need to use the boost libraries. I have installed all of the packages available for boost and libboost. All of the header files are found in /usr/include. The problem is that during the build EVERY reference to anything boost-related is said to be unreferenced.... do I need to build boost from source, if so, how and what is the point of these packages in the repository?

---

### Post by thumper on 2006-09-13
Easiest thing would to create the simplest small example program and post it here along with the errors you are getting.

What about something simple and template only like lexical_cast or shared_ptr?  Are you having problems with those?

---

### Post by thumper on 2006-09-13
I quickly wrote this:
```
#include <iostream>
#include <boost/lexical_cast.hpp>

int main()
{
  int value = boost::lexical_cast<int>("42");
  std::cout << value << '\n';
}

```
and did this
```
tim@slacko:~/sandbox$ g++ -o cast cast.cpp
tim@slacko:~/sandbox$ ./cast
42
tim@slacko:~/sandbox$ 
```
Can you get that working in Anjuta?

---

### Post by nullmind on 2006-09-13
As I noted I had tried to build something with boost using the packages I downloaded via apt-get (libboost-dev, libboost-thread-dev, etc.) and it didn't work :(

I have it working now, I downloaded the boost source from boost.org and ran bjam && bjam install (this took a while and generated over 500mb in libs)

In Anjuta I added the boost_thread, boost_filesystem, and boost_date_time libraries.

All in all I finally have libtorrent compiled and working. Yay, my Gtk torrent frontend is finally underway.

Hope this helps anyone who had the same issue.

---

### Post by thumper on 2006-09-13
You didn't need to build the libraries yourself.

I just installed the libboost-python-dev and libboost-datetime-dev using aptitude, and I do have the libboost libraries in /usr/lib.

What you probably just needed to do was to add the libraries into your Anjuta project.

---

