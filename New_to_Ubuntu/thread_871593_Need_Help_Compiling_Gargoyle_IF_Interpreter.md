---
title: "Need Help Compiling Gargoyle IF Interpreter"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by safetycopy on 2008-07-27
Hey,

I was wondering if there's anyone who's successfully compiled Gargoyle ([http://ccxvii.net/gargoyle/](http://ccxvii.net/gargoyle/)) from the source? I'm really having trouble getting it to compile... I have jam installed and I'm decompressing the source archive, then cding to the directory and running the command 'jam'. Below is the output I'm getting - can anyone please translate this for me?

OS is LINUX (gtk+) 
BUILD is RELEASE 
...patience...
...found 1066 target(s)...
...updating 18 target(s)...
Cc build/linux.release/garglk/draw.o 
Package freetype2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `freetype2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'freetype2' found
garglk/draw.c:10:22: error: ft2build.h: No such file or directory
garglk/draw.c:11:10: error: #include expects "FILENAME" or <FILENAME>
garglk/draw.c:28: error: expected specifier-qualifier-list before &#8216;FT_Face&#8217;
garglk/draw.c:50: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ftlib&#8217;
garglk/draw.c: In function &#8216;loadglyph&#8217;:
garglk/draw.c:111: error: &#8216;FT_Vector&#8217; undeclared (first use in this function)
garglk/draw.c:111: error: (Each undeclared identifier is reported only once
garglk/draw.c:111: error: for each function it appears in.)
garglk/draw.c:111: error: expected &#8216;;&#8217; before &#8216;v&#8217;
garglk/draw.c:117: error: &#8216;font_t&#8217; has no member named &#8216;loaded&#8217;
garglk/draw.c:121: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:123: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:127: error: &#8216;v&#8217; undeclared (first use in this function)
garglk/draw.c:130: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:132: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:133: error: &#8216;FT_LOAD_NO_BITMAP&#8217; undeclared (first use in this function)
garglk/draw.c:133: error: &#8216;FT_LOAD_NO_HINTING&#8217; undeclared (first use in this function)
garglk/draw.c:138: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:138: error: &#8216;FT_RENDER_MODE_LCD&#8217; undeclared (first use in this function)
garglk/draw.c:140: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:140: error: &#8216;FT_RENDER_MODE_LIGHT&#8217; undeclared (first use in this function)
garglk/draw.c:144: error: &#8216;font_t&#8217; has no member named &#8216;advs&#8217;
garglk/draw.c:144: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:146: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:146: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:147: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:147: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:148: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:148: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:149: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:149: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:150: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:150: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:151: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:152: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:152: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:154: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:155: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:156: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:156: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:156: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:158: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:159: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:160: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:160: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c: In function &#8216;loadfont&#8217;:
garglk/draw.c:191: error: &#8216;ftlib&#8217; undeclared (first use in this function)
garglk/draw.c:191: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:199: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:207: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:210: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:214: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:218: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:218: error: &#8216;ft_encoding_unicode&#8217; undeclared (first use in this function)
garglk/draw.c:223: error: &#8216;font_t&#8217; has no member named &#8216;loaded&#8217;
garglk/draw.c: In function &#8216;gli_initialize_fonts&#8217;:
garglk/draw.c:253: error: &#8216;ftlib&#8217; undeclared (first use in this function)
garglk/draw.c:270: error: &#8216;struct font_s&#8217; has no member named &#8216;advs&#8217;
garglk/draw.c: In function &#8216;charkern&#8217;:
garglk/draw.c:407: error: &#8216;FT_Vector&#8217; undeclared (first use in this function)
garglk/draw.c:407: error: expected &#8216;;&#8217; before &#8216;v&#8217;
garglk/draw.c:411: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:412: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:417: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:417: error: &#8216;FT_KERNING_UNFITTED&#8217; undeclared (first use in this function)
garglk/draw.c:417: error: &#8216;v&#8217; undeclared (first use in this function)
garglk/draw.c: In function &#8216;gli_string_width&#8217;:
garglk/draw.c:428: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:432: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:434: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:444: error: &#8216;font_t&#8217; has no member named &#8216;loaded&#8217;
garglk/draw.c:453: error: &#8216;font_t&#8217; has no member named &#8216;advs&#8217;
garglk/draw.c: In function &#8216;gli_draw_string&#8217;:
garglk/draw.c:465: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:470: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:472: error: &#8216;font_t&#8217; has no member named &#8216;face&#8217;
garglk/draw.c:482: error: &#8216;font_t&#8217; has no member named &#8216;loaded&#8217;
garglk/draw.c:492: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:494: error: &#8216;font_t&#8217; has no member named &#8216;glyphs&#8217;
garglk/draw.c:499: error: &#8216;font_t&#8217; has no member named &#8216;advs&#8217;

gcc -c -o build/linux.release/garglk/draw.o `pkg-config freetype2 gtk+ --cflags` -I/usr/include/SDL -O2  -Igarglk -Igarglk garglk/draw.c

...failed Cc build/linux.release/garglk/draw.o ...
Cc build/linux.release/garglk/imgload.o 
Package freetype2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `freetype2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'freetype2' found
garglk/imgload.c:5:17: error: png.h: No such file or directory
garglk/imgload.c: In function &#8216;load_image_png&#8217;:
garglk/imgload.c:176: error: &#8216;png_structp&#8217; undeclared (first use in this function)
garglk/imgload.c:176: error: (Each undeclared identifier is reported only once
garglk/imgload.c:176: error: for each function it appears in.)
garglk/imgload.c:176: error: expected &#8216;;&#8217; before &#8216;png_ptr&#8217;
garglk/imgload.c:177: error: &#8216;png_infop&#8217; undeclared (first use in this function)
garglk/imgload.c:177: error: expected &#8216;;&#8217; before &#8216;info_ptr&#8217;
garglk/imgload.c:182: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
garglk/imgload.c:182: error: &#8216;rowarray&#8217; undeclared (first use in this function)
garglk/imgload.c:183: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;srcdata&#8217;
garglk/imgload.c:183: error: &#8216;srcdata&#8217; undeclared (first use in this function)
garglk/imgload.c:188: error: &#8216;png_ptr&#8217; undeclared (first use in this function)
garglk/imgload.c:188: error: &#8216;PNG_LIBPNG_VER_STRING&#8217; undeclared (first use in this function)
garglk/imgload.c:193: error: &#8216;info_ptr&#8217; undeclared (first use in this function)
garglk/imgload.c:232: error: &#8216;png_bytep&#8217; undeclared (first use in this function)

gcc -c -o build/linux.release/garglk/imgload.o `pkg-config freetype2 gtk+ --cflags` -I/usr/include/SDL -O2  -Igarglk -Igarglk garglk/imgload.c

...failed Cc build/linux.release/garglk/imgload.o ...
Cc build/linux.release/garglk/sysgtk.o 
Package freetype2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `freetype2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'freetype2' found
garglk/sysgtk.c:11:21: error: gtk/gtk.h: No such file or directory
garglk/sysgtk.c:12:28: error: gdk/gdkkeysyms.h: No such file or directory
garglk/sysgtk.c:14: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:16: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:55: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:63: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c: In function &#8216;winopenfile&#8217;:
garglk/sysgtk.c:75: error: &#8216;filedlog&#8217; undeclared (first use in this function)
garglk/sysgtk.c:75: error: (Each undeclared identifier is reported only once
garglk/sysgtk.c:75: error: for each function it appears in.)
garglk/sysgtk.c:79: error: invalid type argument of &#8216;->&#8217;
garglk/sysgtk.c:80: error: &#8216;onokay&#8217; undeclared (first use in this function)
garglk/sysgtk.c:81: error: invalid type argument of &#8216;->&#8217;
garglk/sysgtk.c:82: error: &#8216;oncancel&#8217; undeclared (first use in this function)
garglk/sysgtk.c: In function &#8216;winsavefile&#8217;:
garglk/sysgtk.c:92: error: &#8216;filedlog&#8217; undeclared (first use in this function)
garglk/sysgtk.c:95: error: invalid type argument of &#8216;->&#8217;
garglk/sysgtk.c:96: error: &#8216;onokay&#8217; undeclared (first use in this function)
garglk/sysgtk.c:97: error: invalid type argument of &#8216;->&#8217;
garglk/sysgtk.c:98: error: &#8216;oncancel&#8217; undeclared (first use in this function)
garglk/sysgtk.c: At top level:
garglk/sysgtk.c:104: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:125: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:148: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:153: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c:189: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
garglk/sysgtk.c: In function &#8216;winopen&#8217;:
garglk/sysgtk.c:204: error: &#8216;GdkGeometry&#8217; undeclared (first use in this function)
garglk/sysgtk.c:204: error: expected &#8216;;&#8217; before &#8216;geom&#8217;
garglk/sysgtk.c:208: error: &#8216;geom&#8217; undeclared (first use in this function)
garglk/sysgtk.c:218: error: &#8216;frame&#8217; undeclared (first use in this function)
garglk/sysgtk.c:218: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; undeclared (first use in this function)
garglk/sysgtk.c:219: error: &#8216;GTK_CAN_FOCUS&#8217; undeclared (first use in this function)
garglk/sysgtk.c:220: error: &#8216;GDK_BUTTON_PRESS_MASK&#8217; undeclared (first use in this function)
garglk/sysgtk.c:221: error: &#8216;onbutton&#8217; undeclared (first use in this function)
garglk/sysgtk.c:222: error: &#8216;onkeypress&#8217; undeclared (first use in this function)
garglk/sysgtk.c:223: error: &#8216;onquit&#8217; undeclared (first use in this function)
garglk/sysgtk.c:225: error: &#8216;canvas&#8217; undeclared (first use in this function)
garglk/sysgtk.c:226: error: &#8216;onresize&#8217; undeclared (first use in this function)
garglk/sysgtk.c:227: error: &#8216;onexpose&#8217; undeclared (first use in this function)
garglk/sysgtk.c:234: error: &#8216;GDK_HINT_MIN_SIZE&#8217; undeclared (first use in this function)
garglk/sysgtk.c:235: error: &#8216;GDK_HINT_MAX_SIZE&#8217; undeclared (first use in this function)
garglk/sysgtk.c: In function &#8216;wintitle&#8217;:
garglk/sysgtk.c:253: error: &#8216;frame&#8217; undeclared (first use in this function)
garglk/sysgtk.c: In function &#8216;winrepaint&#8217;:
garglk/sysgtk.c:259: error: &#8216;canvas&#8217; undeclared (first use in this function)

gcc -c -o build/linux.release/garglk/sysgtk.o `pkg-config freetype2 gtk+ --cflags` -I/usr/include/SDL -O2  -Igarglk -Igarglk garglk/sysgtk.c

...failed Cc build/linux.release/garglk/sysgtk.o ...
...skipped libgarglk.so for lack of <garglk>draw.o...
...skipped advsys for lack of libgarglk.so...
...skipped agility for lack of libgarglk.so...
...skipped alan2 for lack of libgarglk.so...
...skipped alan3 for lack of libgarglk.so...
...skipped frotz for lack of libgarglk.so...
...skipped git for lack of libgarglk.so...
...skipped glulxe for lack of libgarglk.so...
...skipped hugo for lack of libgarglk.so...
...skipped level9 for lack of libgarglk.so...
...skipped magnetic for lack of libgarglk.so...
Cc build/linux.release/scare/sctaffil.o 
terps/scare/sctaffil.c:31:18: error: zlib.h: No such file or directory
terps/scare/sctaffil.c: In function &#8216;taf_decompress&#8217;:
terps/scare/sctaffil.c:378: error: &#8216;z_stream&#8217; undeclared (first use in this function)
terps/scare/sctaffil.c:378: error: (Each undeclared identifier is reported only once
terps/scare/sctaffil.c:378: error: for each function it appears in.)
terps/scare/sctaffil.c:378: error: expected &#8216;;&#8217; before &#8216;stream&#8217;
terps/scare/sctaffil.c:389: error: &#8216;stream&#8217; undeclared (first use in this function)
terps/scare/sctaffil.c:394: error: &#8216;Z_NULL&#8217; undeclared (first use in this function)
terps/scare/sctaffil.c:399: error: &#8216;Z_OK&#8217; undeclared (first use in this function)
terps/scare/sctaffil.c:421: error: &#8216;Z_SYNC_FLUSH&#8217; undeclared (first use in this function)
terps/scare/sctaffil.c:422: error: &#8216;Z_STREAM_END&#8217; undeclared (first use in this function)

gcc -c -o build/linux.release/scare/sctaffil.o -O2  -Iterps/scare -Igarglk terps/scare/sctaffil.c

...failed Cc build/linux.release/scare/sctaffil.o ...
Cc build/linux.release/scare/scserial.o 
terps/scare/scserial.c:30:18: error: zlib.h: No such file or directory
terps/scare/scserial.c: In function &#8216;ser_flush&#8217;:
terps/scare/scserial.c:63: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;stream&#8217;
terps/scare/scserial.c:63: error: &#8216;stream&#8217; undeclared (first use in this function)
terps/scare/scserial.c:63: error: (Each undeclared identifier is reported only once
terps/scare/scserial.c:63: error: for each function it appears in.)
terps/scare/scserial.c:80: error: &#8216;Z_NULL&#8217; undeclared (first use in this function)
terps/scare/scserial.c:84: error: &#8216;Z_DEFAULT_COMPRESSION&#8217; undeclared (first use in this function)
terps/scare/scserial.c:85: error: &#8216;Z_OK&#8217; undeclared (first use in this function)
terps/scare/scserial.c:114: error: &#8216;Z_FINISH&#8217; undeclared (first use in this function)
terps/scare/scserial.c:116: error: &#8216;Z_NO_FLUSH&#8217; undeclared (first use in this function)
terps/scare/scserial.c:117: error: &#8216;Z_STREAM_END&#8217; undeclared (first use in this function)

gcc -c -o build/linux.release/scare/scserial.o -O2  -Iterps/scare -Igarglk terps/scare/scserial.c

...failed Cc build/linux.release/scare/scserial.o ...
...skipped scare for lack of <terps!scare>sctaffil.o...
...skipped tadsr for lack of libgarglk.so...
...failed updating 5 target(s)...
...skipped 13 target(s)...

---

### Post by eightmillion on 2008-07-27
The first thing you need to do is install libfreetype6-dev
> sudo apt-get install libfreetype6-dev

Do that and then try again and see how far you get and we'll take it from there.

---

### Post by safetycopy on 2008-07-27
Thanks for the super-quick reply!

Got the package (bear with me - I'm on dial-up) and ran 'jam' again. Here's the output (much shorter this time!):

OS is LINUX (gtk+) 
BUILD is RELEASE 
...patience...
...found 1069 target(s)...
...updating 18 target(s)...
Cc build/linux.release/garglk/draw.o 
Cc build/linux.release/garglk/imgload.o 
garglk/imgload.c:5:17: error: png.h: No such file or directory
garglk/imgload.c: In function &#8216;load_image_png&#8217;:
garglk/imgload.c:176: error: &#8216;png_structp&#8217; undeclared (first use in this function)
garglk/imgload.c:176: error: (Each undeclared identifier is reported only once
garglk/imgload.c:176: error: for each function it appears in.)
garglk/imgload.c:176: error: expected &#8216;;&#8217; before &#8216;png_ptr&#8217;
garglk/imgload.c:177: error: &#8216;png_infop&#8217; undeclared (first use in this function)
garglk/imgload.c:177: error: expected &#8216;;&#8217; before &#8216;info_ptr&#8217;
garglk/imgload.c:182: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
garglk/imgload.c:182: error: &#8216;rowarray&#8217; undeclared (first use in this function)
garglk/imgload.c:183: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;srcdata&#8217;
garglk/imgload.c:183: error: &#8216;srcdata&#8217; undeclared (first use in this function)
garglk/imgload.c:188: error: &#8216;png_ptr&#8217; undeclared (first use in this function)
garglk/imgload.c:188: error: &#8216;PNG_LIBPNG_VER_STRING&#8217; undeclared (first use in this function)
garglk/imgload.c:193: error: &#8216;info_ptr&#8217; undeclared (first use in this function)
garglk/imgload.c:232: error: &#8216;png_bytep&#8217; undeclared (first use in this function)

gcc -c -o build/linux.release/garglk/imgload.o `pkg-config freetype2 gtk+ --cflags` -I/usr/include/SDL -O2  -Igarglk -Igarglk garglk/imgload.c

...failed Cc build/linux.release/garglk/imgload.o ...
Cc build/linux.release/garglk/sysgtk.o 
...skipped libgarglk.so for lack of <garglk>imgload.o...
...skipped advsys for lack of libgarglk.so...
...skipped agility for lack of libgarglk.so...
...skipped alan2 for lack of libgarglk.so...
...skipped alan3 for lack of libgarglk.so...
...skipped frotz for lack of libgarglk.so...
...skipped git for lack of libgarglk.so...
...skipped glulxe for lack of libgarglk.so...
...skipped hugo for lack of libgarglk.so...
...skipped level9 for lack of libgarglk.so...
...skipped magnetic for lack of libgarglk.so...
Cc build/linux.release/scare/sctaffil.o 
Cc build/linux.release/scare/scserial.o 
...skipped scare for lack of libgarglk.so...
...skipped tadsr for lack of libgarglk.so...
...failed updating 1 target(s)...
...skipped 13 target(s)...
...updated 4 target(s)...

---

### Post by eightmillion on 2008-07-27
Looks like you need the file libpng12-dev this time.
> sudo apt-get install libpng12-dev

---

### Post by safetycopy on 2008-07-27
OK - got that too:

OS is LINUX (gtk+) 
BUILD is RELEASE 
...patience...
...found 1077 target(s)...
...updating 14 target(s)...
Cc build/linux.release/garglk/imgload.o 
SharedLink build/linux.release/garglk/libgarglk.so 
Link build/linux.release/advsys/advsys 
Chmod1 build/linux.release/advsys/advsys 
Link build/linux.release/agility/agility 
/usr/bin/ld: build/linux.release/agility/agtread.o(.text+0xf40): unresolvable R_386_32 relocation against symbol `start_time'
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status

cc  -o build/linux.release/agility/agility  build/linux.release/agility/agtread.o build/linux.release/agility/gamedata.o build/linux.release/agility/util.o build/linux.release/agility/agxfile.o build/linux.release/agility/auxfile.o build/linux.release/agility/filename.o build/linux.release/agility/parser.o build/linux.release/agility/exec.o build/linux.release/agility/runverb.o build/linux.release/agility/metacommand.o build/linux.release/agility/savegame.o build/linux.release/agility/debugcmd.o build/linux.release/agility/agil.o build/linux.release/agility/token.o build/linux.release/agility/disassemble.o build/linux.release/agility/object.o build/linux.release/agility/interface.o build/linux.release/agility/os_glk.o build/linux.release/garglk/libgarglkmain.a build/linux.release/garglk/libgarglk.so -lz 

...failed Link build/linux.release/agility/agility ...
Link build/linux.release/alan2/alan2 
Chmod1 build/linux.release/alan2/alan2 
Link build/linux.release/alan3/alan3 
Chmod1 build/linux.release/alan3/alan3 
Link build/linux.release/frotz/frotz 
Chmod1 build/linux.release/frotz/frotz 
Link build/linux.release/git/git 
Chmod1 build/linux.release/git/git 
Link build/linux.release/glulxe/glulxe 
Chmod1 build/linux.release/glulxe/glulxe 
Link build/linux.release/hugo/hugo 
Chmod1 build/linux.release/hugo/hugo 
Link build/linux.release/level9/level9 
Chmod1 build/linux.release/level9/level9 
Link build/linux.release/magnetic/magnetic 
Chmod1 build/linux.release/magnetic/magnetic 
Link build/linux.release/scare/scare 
Chmod1 build/linux.release/scare/scare 
Link build/linux.release/tads/tadsr 
Chmod1 build/linux.release/tads/tadsr 
...failed updating 1 target(s)...
...updated 13 target(s)...

---

### Post by eightmillion on 2008-07-27
I feel I should go into some detail about how to resolve these compile errors. The first time you tried to compile you got the error:
> Package freetype2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `freetype2.pc'

A person might wonder where they might find the file freetype2.pc. Luckily there's a handy program that allows a person to do that. It's called apt-file.
```
sudo apt-get install apt-file
sudo apt-file update
```
To search for the file, freetype2.pc we do this:
```
$ apt-file search freetype2.pc
libfreetype6-dev: /usr/lib/pkgconfig/freetype2.pc

```
So we see that freetype2.pc is contained in the package libfreetype6-dev. We use apt-get to install that package and try the compilation again.

---

### Post by eightmillion on 2008-07-27
Give me a minute on this. I'm going to try to build the package and see what I get.

---

### Post by safetycopy on 2008-07-27
Thanks for the explanation - it really helps to find out these 'little' things that some users probably take for granted. As a user moving from Windows, I'm completely inexperienced in this kind of stuff so it's great when someone takes the time to explain things a bit.

I really appreciate your help and I'm working on apt-file now...

---

### Post by eightmillion on 2008-07-27
I tried building the package and I get the same linking error. Unfortunately I don't think this issue can be resolved without delving into the code. Did you try the pre-built binary on the gargoyle website?

[http://ccxvii.net/gargoyle/download/gargoyle-2006-09-17-linux.zip]("http://ccxvii.net/gargoyle/download/gargoyle-2006-09-17-linux.zip")

---

### Post by safetycopy on 2008-07-27
Drat! Thanks for trying! I do have the precompiled version, but I wasn't sure what to do with it... It's not like clicking a setup.exe and, like I said, I'm new to Linux.

---

### Post by eightmillion on 2008-07-27
The windows version seems to install and run just fine in wine. You might give that a shot.

---

### Post by safetycopy on 2008-07-27
Yeah - I have the Windows version running in Wine, but I find Wine a bit convoluted and would rather be running straight from Linux. If it's not possible, I'll fall back to running under Wine... Any idea what to do with the precompiled Gargoyle? There's no readme - just a gargoyle shell script and some executables for the different interpreters...

---

### Post by eightmillion on 2008-07-27
I figured it out. You have to move libgarglk.so to /usr/lib. Like so...
> sudo cp libgarglk.so /usr/lib/
Then there are a couple of errors in the gargoyle shell script.
```
You have to change
    if [ x"$dirpath" == x ]
to
    if [ x"$dirpath" = x ]
and 
    if [ x"$1" == x ]
to
    if [ x"$1" = x ]

```
Then gargoyle should run. You have to specify the file that you want to open on the command line like so..
> ./gargoyle ~/crystal.acd

---

### Post by safetycopy on 2008-07-27
Ah! Fabulous! That works perfectly!

OK, last question - can I move the Gargoyle directory somewhere, and if 'yes' where would be appropriate? At the moment I sort of feel like I have a program installed to my 'My Documents' folder :-)

---

### Post by eightmillion on 2008-07-27
What I would do is navigat to the folder where you extracted it and do this.

```

rm GNU\ General\ Public\ License.txt HUGO\ License.txt LUXI\ License.txt libgarglk.so TADS\ License.txt

then

mv ./* /usr/bin/

cd ..
rm ./gargoyle-2006-09-17-linux

```

That way you can just type 'gargoyle' in whatever directory you are in and it will open.

Strike that, don't do this yet.
It will conflict if you ever decide to install git.

---

### Post by safetycopy on 2008-07-27
Yep - that works perfectly!

Thanks so much for your time and patience! I've learned a lot and will save this thread for future reference! :-)

---

### Post by eightmillion on 2008-07-27
Navigate to the folder and do this instead...
```

rm GNU\ General\ Public\ License.txt HUGO\ License.txt LUXI\ License.txt libgarglk.so TADS\ License.txt
cd ..
sudo mv ./gargoyle-2006-09-17-linux /usr/bin
echo export PATH=$PATH:/usr/bin/gargoyle-2006-09-17-linux/ >> ~/.bashrc

```
Then reset any bash sessions you have going and you should be able to type "gargoyle" anywhere and open the program.

---

### Post by safetycopy on 2008-07-28
Just an update to keep Gargoyle-related stuff in one place.

I emailed Tor (Gargoyle developer) with regard to compiling and he kindly replied very quickly with this (edited):

> I have heard some reports that
people needed to add -fPIC to the compiler flags to get it to work
under 64-bit Linux.

Try adding -fPIC to GARGLKCCFLAGS under the LINUX section
in the Jamrules file.

GARGLKCCFLAGS = "`$(PKGCONFIG) --cflags`" -fPIC ;

I have no idea if that helps, but it's worth trying.

I haven't had chance to try it out yet, but thought it might be useful to someone else in the future.

---

### Post by safetycopy on 2008-08-04
Finally tried Tor's suggestion, but it made no difference to me... All this is pretty much academic as I have the precompiled binary running now anyway - just FYI.

---

### Post by farvardin on 2009-04-26
I know it's an old post, but just for you to know, there is a new repository and code clean up for gargoyle, it's located at:
[http://code.google.com/p/garglk/](http://code.google.com/p/garglk/)

It's easier to compile now. 

There is also a deb package I made on Debian Etch, should work on ubuntu too:

[http://ifiction.free.fr/fichiers/gargoyle_i386.deb](http://ifiction.free.fr/fichiers/gargoyle_i386.deb)

Some various stuffs for interactive fiction are there:
[http://ifiction.free.fr/index.php?id=iflinux](http://ifiction.free.fr/index.php?id=iflinux)

---

### Post by Grishka on 2009-05-12
I've put Ubuntu packages [here](https://launchpad.net/~thir/+archive/ppa).

---

### Post by soccerush10 on 2009-06-21
I want to thank Safetycopy and Eightmillion for starting this thread and sharing such useful information with a Linux newbie like myself.  I've never compiled anything, but reading this thread, and having the newfound impetus to use Gargoyle gives me a good reason to learn.  

I will post again with my progress.

---

### Post by biodiesel-bri on 2009-11-11
Old thread but here's a followup anyway.

Griska's PPA archive doesn't include amd64 packages, but I got it to compile under Karmic Koala 9.10 amd64 thusly:

Download gargoyle-2009-08-25-sources.zip from the Google Code repo (mentioned in a previous post)

Extract to a directory

Get the needed dependencies:
```
sudo apt-get install jam libsdl-mixer1.2-dev libgtk2.0-dev libfreetype6-dev libpng12-dev
```

And then compile:
```
jam install
```

The INSTALL text file has more details, but you'll find the compiled program in build/dist under the directory where you unzipped the source.

---

