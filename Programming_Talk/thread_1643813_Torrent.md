---
title: "Torrent"
date: 2010-12-12
forum: Programming Talk
---

### Post by stealthc on 2010-12-12
I'm not new to programming, though in the past I've always done it under windows, linux is different....obviously.

So first thing is first, I uninstalled transmission using the software center.

Then I downloaded the source code and extracted the folder to my desktop.
Then I used the following command to obtain dependencies:
$ sudo apt-get install build-essential automake autoconf libtool pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev libnotify-dev libglib2.0-dev libevent-dev

Then I used the following commands within the folder on my desktop in the command terminal:
./configure -q>configure1.txt && make -s>make1.txt
su
make install>install1.txt

and I've attached both files.  So what now?  How do I run this thing?  Is there a .sh file I have to execute or something to get this to work?  That wasn't my first attempt at building.... this is a headache I would like to actually take a look at the code and start fiddling with it but cannot till I can execute this build... which is not described well in the directions.

Also note, install1.txt was split into install1.txt and install2.txt because of the size limitation on .txt files.

---

### Post by Vox754 on 2010-12-12
> **stealthc said:**
> I'm not new to programming, though in the past I've always done it under windows, linux is different....obviously.

So first thing is first, I uninstalled transmission using the software center.

Then I downloaded the source code and extracted the folder to my desktop.
Then I used the following command to obtain dependencies:
$ sudo apt-get install build-essential automake autoconf libtool pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev libnotify-dev libglib2.0-dev libevent-dev

Then I used the following commands within the folder on my desktop in the command terminal:
./configure -q>configure1.txt && make -s>make1.txt
su
make install>install1.txt

and I've attached both files.  So what now?  How do I run this thing?  Is there a .sh file I have to execute or something to get this to work?  That wasn't my first attempt at building.... this is a headache I would like to actually take a look at the code and start fiddling with it but cannot till I can execute this build... which is not described well in the directions.

Also note, install1.txt was split into install1.txt and install2.txt because of the size limitation on .txt files.

Please don't attach files, it's a pain. If you want us to look at an output quickly, put it in code tags
```

like this

```

As for your question. The procedure to build a program is usually
```

./configure
make
sudo make install

```

What "configure" does is setting the environment, it will tell you the tools available and if you have missing development files. "make" runs the appropriate tools and effectively compiles the program, and "make install" usually moves the compiled program and supporting files to their definite directory.

It is typical that if you don't give parameters to "configure", compiled programs will be moved to "/usr/local" as opposed to "/usr", which is where the package manager installs everything.

Therefore, your binary is most probably ```
/usr/local/bin/transmission
``` just as the package manager's is ```
/usr/bin/transmission
```

In fact, programs in "/usr/local/bin" take precedence over those in "/usr/bin". This can be verified by the PATH environment variable
```

echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

This means you can have both binaries installed simultaneously. You still can run both by giving their full paths from the terminal.

If you want to test stuff, you should run "make" but not "make install". The compiled program should be in the same source directory in your desktop and you may run it from there. You may change the code as you like, run "make" again (recompiling), and run the binary again.

In Linux, files don't need an extension, so the binary file may just be called "transmission".

Shell scripts are not really binaries, but collections of instructions that you can run in the terminal. Many programs provide shell scripts that "wrap" around a binary, that is, they set some environment variables and options, and then they run the real binary. An example is "firefox".

However, for your case, I'd assume "transmission" is called directly.

---

### Post by stealthc on 2010-12-12
I figured it out, transmission-gtk in the terminal does it, after all is compiled.

So now I'm stuck at the point where I have to dig through the source code and divorce my client from transmission so that I can integrate extended features I am planning.  I have gone into the version.h and clients.h files in the source and made accomodations but it's hard figuring out how many places I have to do this... and then comes the part that I'm dreading, is to figure out where I want to put in the client check that enables commands to be issued between clients to provided these extensions, and of course how that procedure takes place.

I was thinking of soaking rpc protocol in because it seems to be part of the process in torrent, and of course examining the bencoding aspect since that seems to be part of it as well.  Am I missing anything here?  This is tricky.....

I've done a test run and compiled the software and observed the version number changed in the client shell, but I have yet to determine if I've successfully changed the peer id....I have no way to test this (perhaps I need a packet analyzer to do this?)

---

### Post by cgroza on 2010-12-12
You could do : whereis transmission and that would give you a list of all locations, and one of them is the binary.

---

### Post by stealthc on 2010-12-12
I was just fiddling with the source code and I've stumbled on .o files.
I cannot view them in gedit.  How do I manipulate these files?

---

### Post by iponeverything on 2010-12-12
> **stealthc said:**
> I was just fiddling with the source code and I've stumbled on .o files.
I cannot view them in gedit.  How do I manipulate these files?

those are binary object files. To "manipulate" them, modify the originating .c file and recompile.

---

### Post by stealthc on 2010-12-14
ahh so when I do the ./configure and make commands, it builds these .o files from the .c and .h source files, and so if I go through my source folder and delete these they'll reappear once I recompile again?  I was thinking this shortly after noticing them but figured I would leave it and see if someone confirmed this or not.

I've noticed a bunch of excess language files, figured if I would be changing the shell that they would be moot, for now.  I was baffled for a little bit that the default language does not appear to be included in this list (and must be contained within the source documents with other languages as an option).  It was a folder of potfiles.  Deleting them and recompiling produced no issues so I figure it was ok to do that.

Moving on I would like to have the program reserve hard drive space with a slider for use with the software.  I would like to have this set to a static size to contain default sized blocks (1mb?) of data that is to be data within the virtual hard drive this software is to offer.  I've also decided setting a 20:1 ratio for amount of space offered to what you actually get (which seems stingy, but is required for a bit of duplication and a margin to increase duplication for high demand files on the virtual drive).  Deployment seems tricky because I would like to test this out, have only 2 computers, and need some connectivity with web serving software (php or cfm).  Getting a virtual hard drive first is alot easier to pull off, then I can consider the virtual server capabilities I would like to add to this client.

This is a big thing to wrap my head around, seems my inexperience in linux might get me into a little trouble.  Not yet, but probably sometime soon from now.

---

