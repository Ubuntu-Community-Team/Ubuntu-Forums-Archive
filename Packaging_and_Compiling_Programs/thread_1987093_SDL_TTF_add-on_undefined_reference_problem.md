---
title: "SDL TTF add-on undefined reference problem"
date: 2012-05-25
forum: Packaging and Compiling Programs
---

### Post by 21a21 on 2012-05-25
Hello,

I'm using Ubuntu 12.04 with SDL installed with Geany as my IDE. The issue I'm having is with the SDL TTF add-on library, whenever I compile my application I get these error messages...

```

g++ -Wall  -o "test" "test.cpp"  -lSDL -lSDL_ttf (in directory: /home/user/Programming)
Compilation failed.
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x42f): undefined reference to `FT_Load_Glyph'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x58f): undefined reference to `FT_Outline_Transform'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x5b3): undefined reference to `FT_Get_Glyph'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x5c8): undefined reference to `FT_Stroker_New'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x621): undefined reference to `FT_Render_Glyph'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x7bc): undefined reference to `FT_Done_Glyph'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x7d1): undefined reference to `FT_Get_Char_Index'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x856): undefined reference to `FT_Stroker_Set'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x86e): undefined reference to `FT_Glyph_Stroke'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x87a): undefined reference to `FT_Stroker_Done'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x89d): undefined reference to `FT_Glyph_To_Bitmap'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `Find_Glyph':
(.text+0x8b6): undefined reference to `FT_Done_Glyph'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_Init':
(.text+0xd28): undefined reference to `FT_Init_FreeType'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_CloseFont':
(.text+0xd6d): undefined reference to `FT_Done_Face'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_OpenFontIndexRW':
(.text+0xeee): undefined reference to `FT_Open_Face'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_OpenFontIndexRW':
(.text+0xfba): undefined reference to `FT_Set_Pixel_Sizes'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_OpenFontIndexRW':
(.text+0x1070): undefined reference to `FT_Set_Charmap'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_OpenFontIndexRW':
(.text+0x10a7): undefined reference to `FT_Set_Char_Size'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_SizeUNICODE':
(.text+0x168a): undefined reference to `FT_Get_Kerning'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_RenderUNICODE_Solid':
(.text+0x1b2e): undefined reference to `FT_Get_Kerning'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_RenderUNICODE_Shaded':
(.text+0x21f7): undefined reference to `FT_Get_Kerning'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_RenderUNICODE_Blended':
(.text+0x291e): undefined reference to `FT_Get_Kerning'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_Quit':
(.text+0x2da9): undefined reference to `FT_Done_FreeType'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_GetFontKerningSize':
(.text+0x2dfd): undefined reference to `FT_Get_Kerning'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/libSDL_ttf.a(SDL_ttf.o): In function `TTF_GlyphIsProvided':
(.text+0x13c4): undefined reference to `FT_Get_Char_Index'
collect2: ld returned 1 exit status

```

I've installed the sdl ttf library from this site: [http://www.libsdl.org/projects/SDL_ttf/](http://www.libsdl.org/projects/SDL_ttf/) (SDL_ttf-devel-2.0.11-1.i386.rpm). First I extracted the files and draged them into their correct locations in File System, but that resulted in the error above. I then converted the rpm file into a deb package and installed it, but it still resulted in this error. Finally, I've searched for SDL ttf libraries using Synaptic Package Manager and have installed libsdl-ttf2.0-0, but I can't install libsdl-ttf2.0-dev due to this error...

```

E: /var/cache/apt/archives/libsdl-ttf2.0-dev_2.0.9-1.1ubuntu1_i386.deb: trying to overwrite '/usr/include/SDL/SDL_ttf.h', which is also in package sdl-ttf-devel 2.0.11-2

```

Regardless the problem still persists. Any assistance is appreciated, Thank you.

---

### Post by MadCow108 on 2012-05-26
remove sdl-ttf-devel and reinstall libsdl-ttf2.0-dev
this will get you the shared library symlink which avoids the original linking problem

you currently try to link against the static library which requires an additional freetype link, so this would work too after installing libfreetype6-dev:
```
g++ -Wall  -o "test" "test.cpp"  -lSDL -lSDL_ttf -lfreetype
```

---

