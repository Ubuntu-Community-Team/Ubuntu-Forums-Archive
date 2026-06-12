---
title: "How to tell GCC permanently where to find libraries in /usr/local"
date: 2013-06-05
forum: Programming Talk
---

### Post by DreeDrunk on 2013-06-05
I want to compile code using non standard libraries (e.g. openfst-libs) and do not want to specify the location of the libs every time I type g++.

Greetings,
Dree

---

### Post by dwhitney67 on 2013-06-05
When developers get tired of entering gcc/g++ on the command line with many options, they then to employ the use of a Makefile.

However, since I understand that this query is related to our earlier discussion, I'll instruct you how to add /usr/local/lib (or any other location) to the system's library cache.

All of the following steps require admin privileges; if you don't have them on your system then there's no point reading any further.  To start...

```

# Elevate privileges
#
sudo -i

# Goto the location where library cache configuration files are stored
#
cd /etc/ld.so.conf.d

# Create a new file specifying /usr/local/lib
#
echo /usr/local/lib > local.conf

# Update the system's library cache
#
ldconfig

# log out
#
exit

```

P.S.  I do not have access to my Kubuntu system at the moment; the path to the library cache configuration files (/etc/ld.so.conf.d) may be different on your particular system.  Right now my only reference is a Fedora 16 system.

---------

EDIT:

I have access to my (K)ubuntu system, and have verified that the path, /etc/ld.so.conf.d, is correct.  There should be a file in that directory called 'libc.conf' containing the path /usr/local/lib.  If this is true on your system, then disregard the instructions given above.  There should be no need to augment the system's library path any further, since what you require will already be there.  In case I'm wrong, just run "sudo ldconfig" to update the cache.

---

### Post by DreeDrunk on 2013-06-06
Thanks again dwhitney67! I ran the code you proposed earlier, so I do not know exactly if there was the line /usr/local/lib in the file 'libc.conf'. So GCC searches everytime in the right libraries. If I installed libs somewhere else then I had to do the things, that you proposed. So now I can link my libs to my liking. :D

---

