---
title: "Can you make a library with other libraries included into them?"
date: 2007-12-18
forum: Programming Talk
---

### Post by KPexEA on 2007-12-18
I have written a c++ library that I use in many other programs. My library also references freetype, jpeg, pnglib, zlib, mysql and ffmpeg. In my "windows" version I can include those other libraries directly into mine so programs that use my library only need to link against the one library. 

I'm relatively new at using linux and would like to know if it is possible to do this with linux too. 

I've tried:

LINK=ar
LIB_OBJ= list of object files form my library

$(LINK) rc $@ $(LIB_OBJ) freetype/objs/.libs/libfreetype.a lpng128/libpng.a zlib/libz.a jpeg/libjpeg.a

Thanks
Kevin

---

### Post by Zugzwang on 2007-12-19
What you are trying to do is quite uncommon in Linux. This is partly due to the fact that you mix up the licences of the libs you are using. Since you include "mysql" which is under GPL licence afaik, what you get would be GPL as well (provided that the rest of the libs you include have compaticle licences). This would require you to publish the source of your library as well, *if* you publish/sell/whatever your software.

If you are just coding for yourself, well, then there is no problem in simply including all the libraries in your actual program.

Furthermore, most Linux applications load the commonly used libraries dynamically from the shared set of libs, whereas Windows applications usually provide their own copies, so static linking is usable there.

Using windows and a decent IDE, what you describe might be handy, although here there is no need to do it "here".

The conclusion is that you shouldn't expect an answer here if your question is too uncommon. :(

Note that the order of the libraries specified *is* of importance in the GNU world when linking your program, so any of such approach *may* cause problems you wouldn't expect.

---

