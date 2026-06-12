---
title: "Enable Readline capability in Python 2.6.1"
date: 2009-02-19
forum: Programming Talk
---

### Post by dorseye on 2009-02-19
Greetings. 
I am running a virtual machine Ubuntu Gutsy Gibbon.
It came with Python 2.5 preinstalled, and I'm able to use the "up arrow" (repeat last command entered) in Bash and the 2.5 Python Interpreter.

I installed Python 2.6.1 from source, but in the 2.6.1 interpreter when I hit up arrow to repeat a command all I get is:
>>> ^[[A

I went ahead and ran aptitude and installed the libreadline5-dev using aptitude, then rebuilt from source, and still nothing. Any idea how to resolve this and get the "up arrow" functionality working in my 2.6.1 installation working?

---

### Post by ssam on 2009-02-20
have you tried
```
import readline
```

if that works there are a few places you can put to get it imported every time you start the interpreter, see man python for details.

---

### Post by dorseye on 2009-02-20
> **ssam said:**
> have you tried
```
import readline
```

if that works there are a few places you can put to get it imported every time you start the interpreter, see man python for details.

I have -- no luck with "import readline" either.

---

### Post by imdano on 2009-02-20
Did readline support show up as being on when you ran ./configure the second time?  It's possible that the "no" status you got the first time got cached.

---

### Post by dorseye on 2009-02-20
I wondered about the readline-no being cached also, but I did try a new ./configure using --with-readline, and still nothing.

The other thing that is really weird, is that the /usr/Python2.5 and /usr/Python2.6 directories are vastly different, I dont know if I just built it from source totally incorrect?

---

### Post by imdano on 2009-02-20
When you install 2.6 it's going to be missing all the 3rd party libraries you had in 2.5, which might account for some of the differences.  I'd take a closer look at your configure output, I remember having an issue where it would ignore a library I just installed even when I explicitly told it to look for it.  It started working after I deleted the config.cache file.

---

### Post by casevh on 2009-02-20
You need to install libreadline5-dev.

casevh

---

### Post by dorseye on 2009-02-20
> **casevh said:**
> You need to install libreadline5-dev.

casevh

As I said in my first message, 

"I went ahead and ran aptitude and installed the libreadline5-dev"

Should I install it a different way?

---

### Post by casevh on 2009-02-20
Sorry, missed that part.

Did you do "make distclean" and "./configure" again?

casevh

---

### Post by dorseye on 2009-02-21
> **casevh said:**
> Sorry, missed that part.
Did you do "make distclean" and "./configure" again?
casevh

Now I did:

```
make distclean
./configure --with-readline
make
```

And still get:
>>> ^[[A

---

### Post by casevh on 2009-02-21
Are there any warnings at the end of "make"? This is what I get on my system:

Failed to find the necessary bits to build these modules:
_bsddb             bsddb185           dbm             
dl                 gdbm               imageop         
sunaudiodev                                           

Is readline listed?

Have you verified that the file "readline.h" exists? (Probably in /usr/include/readline/)

casevh

---

