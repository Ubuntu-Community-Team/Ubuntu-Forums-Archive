---
title: "make: Nothing to be done for $program"
date: 2016-06-21
forum: Packaging and Compiling Programs
---

### Post by Arcesso on 2016-06-21
I have created a makefile for a simple NYT reader in C, but make will not compile it with error make: Nothing to be done for nyt_feed.  Below are the contents of the makefile.
```

P=nyt_feed
OBJECTS=
CFLAGS=-g -Wall -O3 `curl-config --cflags` -I/usr/include/libxml2
LDLIBS=`curl-config --libs` -lxml2 -lpthread
CC=c99

nyt_feed: $(OBJECTS)

```

There is no file called nyt_feed so the time stamp cannot be newer.  
What am I doing wrong?

---

### Post by steeldriver on 2016-06-21
You haven't specified a rule to make the target, and it has no dependencies - what are you expecting to happen, exactly?

---

### Post by Arcesso on 2016-06-21
I am not sure what you mean.
How would I specify a rule?  Do I need dependencies?

---

### Post by Arcesso on 2016-06-21
I successfully created a program called hello with a source of hello.c using a makefile that included:
```

P=nyt_feeds
OBJECTS=
CFLAGS= -g -Wall -O3
LDLIBS=
CC=c99

$(P): $(OBJECTS)

```
I didn't have to set the OBJECTS variable.  Why would this program be different?

I have added the line you described but I now get:
```
make: *** No rule to make target 'nyt_feed.o', needed by 'nyt_feed'.  Stop.
```

---

### Post by steeldriver on 2016-06-21
I *think* the way it works is that if you have a source file with the same basename as the target, `make` uses that by default

I assumed that explicitly setting an empty OBJECTS dependency would prevent that, but apparently it doesn't

Sorry I don't know what is the difference in your two cases

---

