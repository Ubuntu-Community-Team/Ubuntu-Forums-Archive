---
title: "makefile help"
date: 2008-04-20
forum: Packaging and Compiling Programs
---

### Post by themoebius on 2008-04-20
I wrote a makefile to compile all the modules in my src directory, but when I make all, not all dependencies are compiled.

Here's the Makefile
```

TARGETS = mapper gui nodeManager libjaus libopenjaus
ECHO = @echo

all: nodeManager mapper gui

libjaus: 
	$(MAKE) -C libjaus
	$(ECHO)

libopenjaus: libjaus
	$(MAKE) -C libopenJaus
	$(ECHO)
	
nodeManager: libjaus libopenjaus 
	$(MAKE) -C ojNodeManager
	$(ECHO)
	
mapper: 
	$(MAKE) -C mapper
	$(ECHO)

gui: mapper
	cd gui && qmake
	$(MAKE) -C gui
	$(ECHO)

clean:
	$(MAKE) clean -C libjaus
	$(MAKE) clean -C libopenJaus
	$(MAKE) clean -C ojNodeManager
	$(MAKE) clean -C mapper
	$(MAKE) clean -C gui
	

```

And here's the terminal output
```

zac@zac-desktop:~/workspace/paradroid/src$ make
make -C libopenJaus
make[1]: Entering directory `/home/zac/workspace/paradroid/src/libopenJaus'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/zac/workspace/paradroid/src/libopenJaus'
make -C ojNodeManager
make[1]: Entering directory `/home/zac/workspace/paradroid/src/ojNodeManager'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/zac/workspace/paradroid/src/ojNodeManager'

```

---

