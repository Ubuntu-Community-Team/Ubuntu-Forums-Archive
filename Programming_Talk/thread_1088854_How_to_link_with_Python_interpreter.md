---
title: "How to link with Python interpreter?"
date: 2009-03-06
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-06
Somebody helpful guy made me this makefile some time ago:
```

SRCS          = main.c graphics.c collisions.c init.c misc.c
APPNAME   = output

CFLAGS    = -g -Wall -pedantic -std=gnu99 -ffast-math `sdl-config --cflags`
LFLAGS     = `sdl-config --libs` -lSDL -lSDL_image -lSDL_ttf -lSDL_mixer -lGL -lGLU
LPATH      = 

# No changes below this line are required!

OBJS         = $(SRCS:.c=.o)
DEP_FILE  = .depend

.PHONY: all clean distclean


all: depend $(APPNAME)

$(APPNAME): $(OBJS)
	@echo Makefile - linking $@
	@$(CC) $^ $(LPATH) $(LFLAGS) -o $@

.c.o:
	@echo Makefile - compiling $<
	@$(CC) $(CFLAGS) -c $< -o $@

clean:
	$(RM) $(OBJS)

distclean: clean
	$(RM) $(APPNAME)
	$(RM) $(DEP_FILE)

depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Makefile - building dependencies in: $@
	@$(CC) -E -MM $(CFLAGS) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

But I'm just wondering, how can I add python interpreter there, probably using python-config?

"python-config --cflags" adds there some stuff that will cause some errors, like warnings about a function prototype not being a function prototype.


Edit: Solved, here are the changes:
```

CFLAGS    = -g -Wall -pedantic -std=gnu99 -ffast-math `sdl-config --cflags`
LFLAGS     = `sdl-config --libs` -lSDL -lSDL_image -lSDL_ttf -lSDL_mixer -lGL -lGLU -lpython2.5 -lm
LPATH      = -L/usr/lib/python2.5/config

```
But when compiling this on another machine it might require some changes. No good.

---

