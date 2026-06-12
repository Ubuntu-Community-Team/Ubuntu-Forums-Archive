---
title: "i386 architecture of input file *.o is incompatible with i386:x86-64 output"
date: 2016-01-06
forum: New to Ubuntu
---

### Post by Balbir_Kumar on 2016-01-06
Where to add "ld -m elf_i386 -s" in my makefile. My makefile is as follows.

CFLAGS= `pkg-config --cflags pixman-1 cairo`-I/home/mjc_in1/usr/local/include
LIBS= `pkg-config --libs pixman-1 cairo` -L/home/mjc_in1/usr/local/lib
CC = g++-4.8 #g++-4.8
OBJECTS= EnlyteHandler.o EnlyteGS.o CairoAPI.o GraphicsAPI.o EnlyteFontCache.o EnlyteFont.o EnlyteXObj.o DataMap.o EnlytePdf.o

render: EnlyteMain.cpp $(OBJECTS)
    $(CC) -g EnlyteMain.cpp $(OBJECTS) -o EnlyteRender $(CFLAGS) $(LIBS) -lpodofo -lfreetype -lfontconfig -ljpeg -lz -lcrypto -lm -lstdc++


DataMap.o: DataMap.h DataMap.cpp
    $(CC) -g -c DataMap.cpp $(CFLAGS) $(LIBS)

EnlyteHandler.o: EnlyteHandler.h EnlyteHandler.cpp
    $(CC) -g -c EnlyteHandler.cpp $(CFLAGS) $(LIBS)
    
EnlyteGS.o: EnlyteGS.h EnlyteGS.cpp
    $(CC) -g -c EnlyteGS.cpp $(CFLAGS) $(LIBS)    

EnlyteFontCache.o: EnlyteFontCache.h EnlyteFontCache.cpp
    $(CC) -g -c EnlyteFontCache.cpp $(CFLAGS) $(LIBS)

EnlyteFont.o: EnlyteFont.h EnlyteFont.cpp
    $(CC) -g -c EnlyteFont.cpp $(CFLAGS) $(LIBS)
        
EnlyteXObj.o: EnlyteXObj.h EnlyteXObj.cpp
    $(CC) -g -c EnlyteXObj.cpp $(CFLAGS) $(LIBS)
                
CairoAPI.o: CairoAPI.h CairoAPI.cpp
    $(CC) -g -c CairoAPI.cpp $(CFLAGS) $(LIBS)        
    
GraphicsAPI.o: GraphicsAPI.h GraphicsAPI.cpp
    $(CC) -g -c GraphicsAPI.cpp $(CFLAGS) $(LIBS)        

EnlytePdf.o: EnlytePdf.h EnlytePdf.cpp
    $(CC) -g -c EnlytePdf.cpp $(CFLAGS) $(LIBS)        

clean:
    rm -rf EnlyteRender $(OBJECTS)

---

