---
title: "Install Targets not Included in deb Package"
date: 2014-02-08
forum: Packaging and Compiling Programs
---

### Post by moonsdad on 2014-02-08
I'm trying to create a package in my [ppa]("https://launchpad.net/~moonsdad/+archive/ppa"). I've done so successfully a few times, but there's one package (warlords-client) that doesn't include the install targets. The contents of my makefile are:

```
# $Id: makefile,v 1.19 2014/02/05 21:53:19 moonsdad Exp $

CC = gcc
CFLAGS = -Wall
CCONF = `pkg-config --cflags --libs gtk+-2.0`
SLINK = -lpcre -lncurses

BASE_SRC = rmhv_stdlib.c game.c
BASE_HED = ${BASE_SRC:.c=.h} game.h
SRV_SRCS = ${BASE_SRC} servsig.c cardplay.c sgui.c server.c
CLI_SRCS = ${BASE_SRC} cligui.c clibuf.c warlord_ai.c clichan.c warlords.c

client : ${CLI_SRCS}
	${CC} ${CFLAGS} ${CLI_SRCS} -o warlords-${@} ${CCONF}

man: warlords.6
	@ gzip -c warlords.6 > warlords.6.gz

install: client man
	@ mv warlords-client ${DESTDIR}/usr/bin/
	@ mv dat/img/warscum.png ${DESTDIR}/usr/share/icons/
	@ cp -r dat ${DESTDIR}/usr/share/games/warlords/

${CLI_SRCS} : ${BASE_HED} client.h warlord_ai.h
```

It has some residual stuff from when the server and client were built with the same makefile. But that shouldn't be a problem (the server package builds just fine). The icon, binary file, and data files are all not included, although the build is reported as successful. I've made sure the install command lines all begin with tabs; what else could be the problem?

---

