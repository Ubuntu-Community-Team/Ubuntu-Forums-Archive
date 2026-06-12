---
title: "How to install FTGL?"
date: 2009-03-12
forum: Programming Talk
---

### Post by tneva82 on 2009-03-12
Found this rather handy sounding library for printing out text in openGL that apparently works in both Windows and Linux. Huzah! Just what I have been looking for.

Just one tiny problem. The second I try to include them I get bucketloads of errors. Lots of them. Lots and lots and lots. Small snippet:

```
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
                 from src/./headers/client.h:16,
                 from src/mainclient.cpp:2:
/usr/local/include/FTGL/FTGLBitmapFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTGLBitmapFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:125,
                 from src/./headers/client.h:16,
                 from src/mainclient.cpp:2:
/usr/local/include/FTGL/FTBufferFont.h:79: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/local/include/FTGL/FTBufferFont.h:79: error: expected ‘;’ before ‘(’ token
In file included from /usr/local/include/FTGL/ftgl.h:126,
                 from src/./headers/client.h:16,
                 from src/mainclient.cpp:2:

```

Umm...What's up with that? I can't believe library would be that badly done that users are expected to fix code themselves so obviously I haven't done everything right. I have installed both the FTGL AND freetype 2(and synaptic packet manager shows them all as installed) but still no help. Maybe I need to add something to makefile? Or what?

Hopefully somebody knows how to solve this. I would hate to have to toss away what seems to be perfect solution to me for printing text in openGL.

---

### Post by cabalas on 2009-03-12
When compiling have you remembered to include the headers and link to the library when compiling like so:

```

gcc -c somefile.c `pkg-config --cflags ftgl`
gcc -o output_name somefile.o otherfile.o `pkg-config --libs ftgl`

```

---

### Post by tneva82 on 2009-03-12
Thanks! Makefile adjusted.

---

