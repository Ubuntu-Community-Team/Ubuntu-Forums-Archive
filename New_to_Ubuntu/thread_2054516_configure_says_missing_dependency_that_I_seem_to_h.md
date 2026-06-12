---
title: "configure says missing dependency that I seem to have?"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Jmob on 2012-09-07
So, I'm trying to compile the computer side of a tethering app for android.   When I run configure, I get this

```
Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for program gcc or cc           : /usr/bin/gcc 
Checking for gcc                         : ok  
Checking for library dl                  : yes 
Checking for openssl                     : not found 
Checking for function SSL_library_init   : not found 
Checking for header openssl/crypto.h     : not found 
/home/jmobrien/Downloads/Tether/node/wscript:374: error: Could not autodetect OpenSSL support. Make sure OpenSSL development packages are installed. Use configure --without-ssl to disable this message.

```Synaptic says I have openssl installed.  What could be causing this?

---

### Post by jerome1232 on 2012-09-07
just clarification, you have openssl-dev? Probably libopenssl-dev actually.

When you are compiling from source, usually you need the -dev versions of packages (means development)

I apologize if you were already aware of this.

---

### Post by Jmob on 2012-09-07
Don't let my use of Synaptic fool you.  There's a reason I'm posting this in the AB subforum--I'm quite new to compiling, but I needed this particular application.

Hmm, but synaptic has no packages with either particular name (openssl-dev, or libopenssl-dev).   There is libssl-dev, though.  Is that what I need?

While I'm at it,  are the other two "not found"s related like they seem to be, or do I need to get something additional for them as well?

Edit: yes, that seems to have been it.  Thanks for the help!

One other question.  What's best practices for locating a self-compiled application?  /usr/local?  And one needs root to copy there, right?

---

### Post by jerome1232 on 2012-09-07
> **Jmob said:**
> Don't let my use of Synaptic fool you.  There's a reason I'm posting this in the AB subforum--I'm quite new to compiling, but I needed this particular application.

Hmm, but synaptic has no packages with either particular name (openssl-dev, or libopenssl-dev).   There is libssl-dev, though.  Is that what I need?

While I'm at it,  are the other two "not found"s related like they seem to be, or do I need to get something additional for them as well?

My guess is libssl-dev is the one.  I would just install it and try. Those other not founds are related to openssl and I assume installing the library will take care of those as well.

I checked the description of libssl-dev, and I'm sure it's what you need

```
Description-en: SSL development libraries, header files and documentation
 libssl and libcrypto development libraries, header files and manpages.
 .
 It is part of the OpenSSL implementation of SSL.
```

---

### Post by Jmob on 2012-09-07
Yes, editing the above while you were replying.  It seemed to be it.  Added one other question above, though, if you don't mind.

---

### Post by jerome1232 on 2012-09-07
If it was just for my user, I would put it under ~/bin, ~/ means your users home.

If it was a system wide install, I like to put it under /usr/local/bin/packagename/

Some people like to put them under /opt

It's been a long while since I've actually needed to compile anything, I think when you run make install it has a default and you can change it somehow.... I'd honestly have to google it.

---

### Post by SeijiSensei on 2012-09-07
> **Jmob said:**
> One other question.  What's best practices for locating a self-compiled application?  /usr/local?  And one needs root to copy there, right?

/usr/local is the standard location.  I actually have a separate hard drive partition mounted as /usr/local to keep it from being overwritten if I install a new version of the OS.  Same for /home.

---

### Post by Jmob on 2012-09-07
Yeah, I keep /home separate already.  I'll consider moving /usr/local off if I start doing more of my own compiling.  Thanks.

---

