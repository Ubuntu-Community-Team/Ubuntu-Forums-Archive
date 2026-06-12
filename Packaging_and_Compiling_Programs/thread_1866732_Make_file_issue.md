---
title: "Make file issue"
date: 2011-10-21
forum: Packaging and Compiling Programs
---

### Post by LucasCube on 2011-10-21
I'm running Ubuntu 11.10 and I'm trying to compile C++ with a make file.  I keep on getting an error that is due to that it wants to include  -I/usr/local/include/Sockets but when I go to that file, it is empty. It  seems to be looking for a sockets-config? Next line is -Wall -g -O2  $(INCLUDE) -MD `Sockets-config`.. then I get the error.. fatal error:  parse.h: No such file or directory, compilation terminated.

I've searched the net and have found very little explanation to this  issue, I was hoping someone here might know what the is causing this  problem.

---

### Post by Bachstelze on 2011-10-21
Post the Makefile.

---

### Post by LucasCube on 2011-10-21
> **Bachstelze said:**
> Post the Makefile.

```
VERSION =	1.3

INCLUDE =	-I/usr/local/include/Sockets 
CFLAGS =	-Wall -g -O2 $(INCLUDE) -MD `Sockets-config`
CPPFLAGS =	$(CFLAGS)
LIBS =		-L/usr/local/lib -lSockets -lpthread -lssl -lcrypto

#CFLAGS +=	-DMACOSX
#CFLAGS +=	-DSOLARIS

PROGS =		small small6

all:		$(PROGS)

SMALL =		SmallSocket.o SmallHandler.o World.o \
		MobFactory.o PlayerFactory.o ItemFactory.o cstring.o
small:		$(SMALL) small.o
		g++ -o $@ $^ $(LIBS)

small6:		$(SMALL) small6.o
		g++ -o $@ $^ $(LIBS)
		
clean:
		rm -f *.o *~ *.d slask $(PROGS)

install:	all
		install --strip $(PROGS) /usr/local/bin

-include	*.d

docs:		clean
		./mkdot.sh

PROJ_NAME =	small
PROJ_DIR =	/usr/local/apache/www.alhem.net/htdocs/small/
tar:		clean
		tar czf $(PROJ_NAME)-$(VERSION).tar.gz *.h *.cpp Makefile \
			gpl.txt
		/usr/local/bin/tarfix.sh $(PROJ_NAME)-$(VERSION)
		cp $(PROJ_NAME)-$(VERSION).tar.gz $(PROJ_DIR)
		cp $(PROJ_NAME)-$(VERSION).zip $(PROJ_DIR)


[CODE]
```[/CODE]

---

### Post by MadCow108 on 2011-10-22
apparently you have to install some Sockets stuff into usr/local
Its probably some non standard (= not packaged) software as that unix standard stuff is almost always written in lowercase.

without more information it is impossible to help.

---

### Post by LucasCube on 2011-10-22
> **MadCow108 said:**
> apparently you have to install some Sockets stuff into usr/local
Its probably some non standard (= not packaged) software as that unix standard stuff is almost always written in lowercase.

without more information it is impossible to help.

Ok, that is help enough I think. Perhaps this is what I'm supposed to install? 

[http://www.alhem.net/Sockets/download.html]("http://www.alhem.net/Sockets/download.html")

---

