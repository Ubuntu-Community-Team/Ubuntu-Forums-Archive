---
title: "How pure C program calls a C++ library"
date: 2007-12-11
forum: Programming Talk
---

### Post by jsatubnutufroums on 2007-12-11
Hi, everyone:
I develop a project in pure environment. Now, I get a open source about STUN protocol written in C++ and want to use those function. An the beginning, I try to manually convert C++ functions into corresponding C functions and find that there are really so many statements I need to modify. So I wanto to find another way to replace the iteractive way. What shall I do???
The following is part of content of Makefile:
```

STUNLIB=libstun.a
CXXFLAGS+=-g -O -Wall
LDFLAGS+=-g -O -Wall

all: server client 

clean:
	- rm *.o server client tlsServer 

server: server.o stun.o udp.o 
	$(CXX) $(LDFLAGS) -o $@  $^

client: client.o stun.o udp.o 
	$(CXX) $(LDFLAGS) -o $@  $^

%.o:%.cxx
	$(CXX)  -c $(CPPFLAGS) $(CXXFLAGS) $< -o $@

libstun.a: stun.o udp.o
	ar rv $@ $<

%:RCS/%
	co $@

# Dependancies
server.o: stun.h udp.h 
client.o: stun.h udp.h 
stun.o: stun.h udp.h
udp.o: stun.h udp.h 
```

---

### Post by yabbadabbadont on 2007-12-11
Try compiling your C source files as C++ files to see if they will build without error.  A lot of times, C programs are syntactically valid as C++ programs, but just don't use any of the object oriented features.

---

