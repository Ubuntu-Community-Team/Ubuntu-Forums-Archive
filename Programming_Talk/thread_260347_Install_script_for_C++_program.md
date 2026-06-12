---
title: "Install script for C++ program?"
date: 2006-09-18
forum: Programming Talk
---

### Post by Laterix on 2006-09-18
I just finished [my first C++ project]("http://www.taimila.com/bluelink") and I would like to release that program under GPL. Code is ready for first release, but I don't know how to make install script for it. I would need to copy some config files under ~/.bluelink and then executable to /usr/bin. What is the correct way to do that?

---

### Post by skymt on 2006-09-18
The "kosher" way to do it is to use the GNU autotools: autoconf, automake and libtool. There's a good online book on the (rather confusing) topic called [GNU Autoconf, Automake and Libtool](http://sources.redhat.com/autobook/), also known as the Autobook or the Goat Book.

The easy way, however, is to make a shell script that cp's your binary to /usr/bin and any other files to wherever they go. It will only work on a system configured like yours, but... it's easy!

---

### Post by Laterix on 2006-09-18
> **skymt said:**
> The "kosher" way to do it is to use the GNU autotools: autoconf, automake and libtool. There's a good online book on the (rather confusing) topic called [GNU Autoconf, Automake and Libtool](http://sources.redhat.com/autobook/), also known as the Autobook or the Goat Book.

I was a affraid that I need to read a book to make install script for my program.

> 
The easy way, however, is to make a shell script that cp's your binary to /usr/bin and any other files to wherever they go. It will only work on a system configured like yours, but... it's easy!
Yeah, this crossed my mind and I quess this is my way. I want to concentrate developeing my software not to spend all my time to figure out how to make installation for it. :) Users can do that :P ...or perhaps some helpful person from Ubuntuforums. ;)

---

