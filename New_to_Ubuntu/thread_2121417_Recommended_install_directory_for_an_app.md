---
title: "Recommended install directory for an app?"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by fr33z0n3r on 2013-03-01
I'm in the process of installing an alpha version of an app.  I'm new to this. I'm looking for generic guidance for Ubuntu.   The app to be installed is KeePassX and the link is below.

[http://www.keepassx.org/news/2012/10/367](http://www.keepassx.org/news/2012/10/367)

I've gotten through the initial directions for the Build stage. (default commands, assume those will work)  Now I need to know where to *install* it.  Since there is no clear guidance and I'm a newb, I figure I could cause a problem easily by choosing a poor location.

What are the risks of choosing a certain directory?  Educational links will suffice if you prefer.  I couldn't find anything.


Directions shown:[INDENT]
Installing:
===========
make install [DESTDIR=X]
[/INDENT]


I'm sure I will be re-installing it in future rev's.

What should a user choose when faced with this question?  Is there a safe answer?  Is there a bad answer?


Thanks,
fr33z0n3r


btw - I like the posting in this forum. It's clean and friendly.

---

### Post by audiomick on 2013-03-01
I will assume you know what I mean when I say /home/user.  That is your personal directory, and it is in /home.  To install a programme that way you are going about it, I would create a directory in there, and use that for the installation. I consider that as the safest, as that  belongs to you the user and you have control over it.

Having said that, I am able to find Keepass in the software centre on this 10.04 install. I would strongly suggest you look for it in your software centre and install it from there. That way you are sure of getting a version of the program that wont mess up your install somehow.

---

### Post by andrew.46 on 2013-03-01
Something like the following should work:

```

mkdir build && cd build/
cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local
make -j 5
sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
                  --pkgname keepassx --pkgversion "2.0" --fstrans=no \
                  --deldesc=yes --delspec=yes --default

```

although there were a few dependencies required...

---

### Post by 3rdalbum on 2013-03-01
> **fr33z0n3r said:**
> 
Directions shown:[INDENT]
Installing:
===========
make install [DESTDIR=X]
[/INDENT]


The square brackets indicate that this is an optional parameter. You don't need yo specify it, just do 'sudo make install' and it will install to the default location. That's the safest option.

---

### Post by fr33z0n3r on 2013-03-01
Uggh.  I had a whole response typed up.....

ok.    Thanks everyone.  The app is installed thanks to your help!

@Andrew - I prolly shoulda listened to your usage of checkinstall.  I've saved off the install showing the file paths at least.

---

