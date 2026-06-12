---
title: "problems with ftgl &amp; freetype2"
date: 2010-02-02
forum: Packaging and Compiling Programs
---

### Post by lewc on 2010-02-02
Hi,

I have a problem compiling anything that needs freetype2 and ftgl

the latter of which is necessary for a project im working on. here is the compiler errors I am getting
```

g++ -c introstate.cpp `sdl-config --cflags --libs` -lGL -lGLU -lGLEW
In file included from /usr/local/include/FTGL/ftgl.h:32,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/ftgl.h:33:10: error: #include expects "FILENAME" or <FILENAME>
/usr/local/include/FTGL/ftgl.h:34:10: error: #include expects "FILENAME" or <FILENAME>
/usr/local/include/FTGL/ftgl.h:35:10: error: #include expects "FILENAME" or <FILENAME>
In file included from /usr/local/include/FTGL/ftgl.h:110,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTPoint.h:75: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/FTGL/FTPoint.h: In constructor ‘FTPoint::FTPoint(int)’:
/usr/local/include/FTGL/FTPoint.h:77: error: ‘ft_vector’ was not declared in this scope
In file included from /usr/local/include/FTGL/ftgl.h:111,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTBBox.h: At global scope:
/usr/local/include/FTGL/FTBBox.h:75: error: expected ‘)’ before ‘glyph’
In file included from /usr/local/include/FTGL/ftgl.h:114,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTGlyph.h:58: error: expected ‘)’ before ‘glyph’
/usr/local/include/FTGL/FTGlyph.h:112: error: ‘FT_Error’ does not name a type
/usr/local/include/FTGL/FTGlyph.h:196: error: ‘FT_Error’ does not name a type
In file included from /usr/local/include/FTGL/ftgl.h:115,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTBitmapGlyph.h:50: error: expected ‘)’ before ‘glyph’
/usr/local/include/FTGL/FTBitmapGlyph.h:77: error: ‘FT_GlyphSlot’ was not declared in this scope
In file included from /usr/local/include/FTGL/ftgl.h:116,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTBufferGlyph.h:49: error: expected ‘)’ before ‘glyph’
In file included from /usr/local/include/FTGL/ftgl.h:117,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTExtrdGlyph.h:59: error: expected ‘)’ before ‘glyph’
/usr/local/include/FTGL/FTExtrdGlyph.h:97: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/local/include/FTGL/FTExtrdGlyph.h:97: error: expected primary-expression before ‘float’
/usr/local/include/FTGL/FTExtrdGlyph.h:98: error: expected primary-expression before ‘float’
/usr/local/include/FTGL/FTExtrdGlyph.h:98: error: expected primary-expression before ‘float’
/usr/local/include/FTGL/FTExtrdGlyph.h:99: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTExtrdGlyph.h:99: error: initializer expression list treated as compound expression
In file included from /usr/local/include/FTGL/ftgl.h:118,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTOutlineGlyph.h:56: error: expected ‘)’ before ‘glyph’
/usr/local/include/FTGL/FTOutlineGlyph.h:88: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/local/include/FTGL/FTOutlineGlyph.h:88: error: expected primary-expression before ‘float’
/usr/local/include/FTGL/FTOutlineGlyph.h:89: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTOutlineGlyph.h:89: error: initializer expression list treated as compound expression
In file included from /usr/local/include/FTGL/ftgl.h:119,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTPixmapGlyph.h:50: error: expected ‘)’ before ‘glyph’
/usr/local/include/FTGL/FTPixmapGlyph.h:77: error: ‘FT_GlyphSlot’ was not declared in this scope
In file included from /usr/local/include/FTGL/ftgl.h:120,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTPolyGlyph.h:57: error: expected ‘)’ before ‘glyph’
/usr/local/include/FTGL/FTPolyGlyph.h:92: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/local/include/FTGL/FTPolyGlyph.h:92: error: expected primary-expression before ‘float’
/usr/local/include/FTGL/FTPolyGlyph.h:93: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTPolyGlyph.h:93: error: initializer expression list treated as compound expression
In file included from /usr/local/include/FTGL/ftgl.h:121,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTTextureGlyph.h:59: error: expected ‘)’ before ‘glyph’
/usr/local/include/FTGL/FTTextureGlyph.h:92: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/local/include/FTGL/FTTextureGlyph.h:92: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTTextureGlyph.h:93: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTTextureGlyph.h:93: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTTextureGlyph.h:94: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTTextureGlyph.h:94: error: expected primary-expression before ‘int’
/usr/local/include/FTGL/FTTextureGlyph.h:94: error: initializer expression list treated as compound expression
In file included from /usr/local/include/FTGL/ftgl.h:123,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTFont.h:128: error: ‘FT_Int’ has not been declared
/usr/local/include/FTGL/FTFont.h:137: error: ‘FT_Encoding’ has not been declared
/usr/local/include/FTGL/FTFont.h:151: error: ‘FT_Encoding’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTFont.h:151: error: expected ‘;’ before ‘*’ token
/usr/local/include/FTGL/FTFont.h:363: error: ‘FT_Error’ does not name a type
/usr/local/include/FTGL/FTFont.h:378: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTFont.h:378: error: expected ‘;’ before ‘(’ token
/usr/local/include/FTGL/FTFont.h:411: error: expected ‘,’ or ‘...’ before ‘(’ token
/usr/local/include/FTGL/FTFont.h:451: error: ‘FT_Encoding’ has not been declared
/usr/local/include/FTGL/FTFont.h:467: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/local/include/FTGL/FTFont.h:579: error: ‘FT_Error’ does not name a type
In file included from /usr/local/include/FTGL/ftgl.h:124,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTGLBitmapFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTGLBitmapFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:125,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTBufferFont.h:79: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTBufferFont.h:79: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:126,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTGLExtrdFont.h:82: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTGLExtrdFont.h:82: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:127,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTGLOutlineFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTGLOutlineFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:128,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTGLPixmapFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTGLPixmapFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:129,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTGLPolygonFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTGLPolygonFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:130,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTGLTextureFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTGLTextureFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:132,
                 from playstate.h:7,
                 from introstate.cpp:7:
/usr/local/include/FTGL/FTLayout.h:134: error: ‘FT_Error’ does not name a type
/usr/local/include/FTGL/FTLayout.h:187: error: ‘FT_Error’ does not name a type
In file included from introstate.cpp:7:
playstate.h:36: error: ISO C++ forbids declaration of ‘FTfont’ with no type
playstate.h:36: error: expected ‘;’ before ‘*’ token
make: *** [introstate.o] Error 1

```

This is my makefile as you can see it uses SDL & glew so it needs -lGL & -lGLU so I'm assuming ftgl needs something from freetype 
```

stateman:    gameengine.o introstate.o main.o menustate.o playstate.o
    g++ gameengine.o introstate.o main.o menustate.o playstate.o `pkg-config --libs ftgl freetype2` -lSDL -lGL -lGLU -lGLEW -o stateman

main.o:        main.cpp
    g++ -c main.cpp `sdl-config --cflags --libs`

gameengine.o:    gameengine.cpp gameengine.h
    g++ -c gameengine.cpp `sdl-config --cflags --libs` -lGL -lGLU -lGLEW

introstate.o:    introstate.cpp introstate.h
    g++ -c introstate.cpp `sdl-config --cflags --libs` -lGL -lGLU -lGLEW

menustate.o:    menustate.cpp menustate.h
    g++ -c menustate.cpp `sdl-config --cflags --libs`

playstate.o:    playstate.cpp playstate.h
    g++ -c playstate.cpp `pkg-config --cflags ftgl freetype2 --libs` -lGL -lGLU -lGLEW -lSDL

clean:
    rm -f *.o stateman

```
I have been searching the internet for days and it's quite literally hurting my head right now trying to figure out if I'm stupid or the people that write these supposedly helpful libs are stupid or if it's another ubuntu breakage like the c++ <algorithm> break

thanks

---

### Post by lewc on 2010-02-02
I have fixed the problem, it's all freetypes fault because it is for lack of a better word retarded.

just fire up terminal and sudo ln -s /usr/include/freetype2/freetype /usr/include/freetype
works like a charm

---

### Post by wolfwoolford on 2013-04-16
> **lewc said:**
> I have fixed the problem, it's all freetypes fault because it is for lack of a better word retarded.

just fire up terminal and sudo ln -s /usr/include/freetype2/freetype /usr/include/freetype
works like a charm

Or just use gcc include flags and supply -I/usr/include/freetype2

---

### Post by codemaniac on 2013-04-16
Old thread closed. As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks.

---

### Post by Elfy on 2013-04-16
Closed.

OP's not been back for over 3 years.

Please don't drag old threads back.

---

