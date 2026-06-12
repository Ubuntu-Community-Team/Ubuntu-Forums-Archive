---
title: "can't link openssl static libraries"
date: 2012-02-26
forum: Programming Talk
---

### Post by Avega768 on 2012-02-26
Hi Everyone!

It can't link openssl static libraries. i'm using Ubuntu Server 10.04.4 LTS (x86_64)

And i have the next problem when i try to build my application.

Please help me!!!)

_That is my MakeFile:_
```

#-----------------------------------------------------------------------------
#	Usage of make file
#-----------------------------------------------------------------------------
# Clean operation:
#	make -f MakeLogic clean
#
# Make operation:
#	make -f MakeLogic
#
#


#OBJ = $(SRC:.cpp=.o)
OBJ_DIR = ./obj

LIB_DIR = -L../lib -L../../libs/x86_64/boost -L../../libs/x86_64/icu -L../../libs/x86_64/openssl \
-L../../libs/x86_64/ticpp -L../../libs/x86_64/torrent-rasterbar

LIBS = -lclient -lcommon -lsicuuc -lsicudata -lticpp -ltorrent-rasterbar -lssl -lcrypto -ldl -luuid -lboost_program_options-mt -lboost_serialization-mt \
-lpthread -lboost_thread-mt -lboost_system-mt -lboost_filesystem-mt

OUT_DIR= ../bin
OUT_FILE_NAME = logic_client

# include directories
INCLUDES=-I. -I../common -I../client -I../../depends -I../../depends/zlib -I../../libs/includes -I../../depends/icu/include

# C++ compiler flags (-g -O2 -Wall)
CCFLAGS =

# compiler
CCC = g++


# Enumerating of every *.cpp as *.o and using that as dependency
$(OUT_FILE_NAME): $(patsubst %.cpp,$(OBJ_DIR)/%.o,$(wildcard *.cpp))
	$(CCC) -o $(OUT_DIR)/$@ $^ $(LIB_DIR) $(LIBS)

#Compiling every *.cpp to *.o
$(OBJ_DIR)/%.o: %.cpp dircreation
	$(CCC) -c $(INCLUDES) $(CCFLAGS) -o $@ $<

dircreation:
	@mkdir -p $(OUT_DIR)
	@mkdir -p $(OBJ_DIR)

.PHONY : clean
clean:
	rm -f $(OBJ_DIR)/*.o $(OUT_DIR)/$(OUT_FILE_NAME) Makefile.bak

```

But during linking i have the next error:
```

avega@linux-builder:~/projects/logicstor/logic_client$ make -f MakeLogic
g++ -c -I. -I../common -I../client -I../../depends -I../../depends/zlib -I../../libs/includes -I../../depends/icu/include  -o obj/logic_client_app.o logic_client_app.cpp
In file included from ../common/utils.h:4,
                 from ../client/common_client_includes.h:15,
                 from ../client/logic_client.h:4,
                 from logic_client_app.cpp:7:
../common/protocol.h:14: warning: scoped enums only available with -std=c++0x or -std=gnu++0x
g++ -c -I. -I../common -I../client -I../../depends -I../../depends/zlib -I../../libs/includes -I../../depends/icu/include  -o obj/stdafx.o stdafx.cpp
g++ -o ../bin/logic_client obj/logic_client_app.o obj/stdafx.o -L../lib -L../../libs/x86_64/boost -L../../libs/x86_64/icu -L../../libs/x86_64/openssl -L../../libs/x86_64/ticpp -L../../libs/x86_64/torrent-rasterbar -lclient -lcommon -lsicuuc -lsicudata -lticpp -ltorrent-rasterbar -lssl -lcrypto -ldl -luuid -lboost_program_options-mt -lboost_serialization-mt -lpthread -lboost_thread-mt -lboost_system-mt -lboost_filesystem-mt
../lib/libcommon.a(utils.o): In function `logic::GenerateTempFileName(std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> >, std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> >)':
utils.cpp:(.text+0x15dd): warning: the use of `tempnam' is dangerous, better use `mkstemp'
../lib/libclient.a(torrent_actor.o): In function `libtorrent::hasher::hasher(char const*, int)':
torrent_actor.cpp:(.text._ZN10libtorrent6hasherC1EPKci[libtorrent::hasher::hasher(char const*, int)]+0x1b): undefined reference to `SHA1_Init(SHA_CTX*)'
torrent_actor.cpp:(.text._ZN10libtorrent6hasherC1EPKci[libtorrent::hasher::hasher(char const*, int)]+0x31): undefined reference to `SHA1_Update(SHA_CTX*, unsigned char const*, unsigned int)'
../lib/libclient.a(torrent_actor.o): In function `libtorrent::hasher::final()':
torrent_actor.cpp:(.text._ZN10libtorrent6hasher5finalEv[libtorrent::hasher::final()]+0x3c): undefined reference to `SHA1_Final(unsigned char*, SHA_CTX*)'
collect2: ld returned 1 exit status
make: *** [logic_client] Error 1

```

Does anybody know the solution?

Thanks

---

### Post by Zugzwang on 2012-02-27
First Idea: Try to change the order in the linking command

This line:
```

$(CCC) -o $(OUT_DIR)/$@ $^ $(LIB_DIR) $(LIBS)

```
should be changed to this line:
```

$(CCC) $(LIB_DIR) $(LIBS) -o $(OUT_DIR)/$@ $^ 

```

---

### Post by Avega768 on 2012-02-27
I have found the solution, we have to use the same preprocessor definitions for every project where we use libtorrent-rasterbar !!!

Thanks for all

---

### Post by dwhitney67 on 2012-02-27
> **Zugzwang said:**
> First Idea: Try to change the order in the linking command

This line:
```

$(CCC) -o $(OUT_DIR)/$@ $^ $(LIB_DIR) $(LIBS)

```
should be changed to this line:
```

$(CCC) $(LIB_DIR) $(LIBS) -o $(OUT_DIR)/$@ $^ 

```

-1

Always specify the libraries after the object files, not the other way around.

---

### Post by Zugzwang on 2012-02-27
> **dwhitney67 said:**
> -1

Always specify the libraries after the object files, not the other way around.

Aaaww, right - I mixed the left-to-right evaluation order with right-to-left.

---

