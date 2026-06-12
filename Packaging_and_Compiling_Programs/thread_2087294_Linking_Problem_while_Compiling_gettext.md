---
title: "Linking Problem while Compiling gettext"
date: 2012-11-23
forum: Packaging and Compiling Programs
---

### Post by dodle on 2012-11-23
I have been trying to compile gettext 0.18.1.1 for a while now. All goes well until it enters the gettext-tools/gnulib-lib directory:

```
....
Creating library file: .libs/libgettextlib.dll.a../woe32dll/.libs/c++html-styled-ostream.o: In function `htmlled_ostream(float, long double,...)(...)':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/html-styled-ostream.oo.c:70: unded reference to `html_ostream_free(any_ostream_representation*)'
../woe32dll/.libs/c++html-styled-ostream.o: In function `html_styled_ostream_create':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/html-styled-ostream.oo.c:143: unned reference to `ostream_write_mem(any_ostream_representation*, void const*, unsigned int)'
../woe32dll/.libs/c++html-styled-ostream.o: In function `html_styled_ostream__end_use_class':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/html-styled-ostream.oo.c:88: unded reference to `html_ostream_end_span(any_ostream_representation*, char const*)'
../woe32dll/.libs/c++html-styled-ostream.o: In function `html_styled_ostream__begin_use_class':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/html-styled-ostream.oo.c:81: unded reference to `html_ostream_begin_span(any_ostream_representation*, char const*)'
../woe32dll/.libs/c++html-styled-ostream.o: In function `html_styled_ostream__flush':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/html-styled-ostream.oo.c:64: unded reference to `html_ostream_flush(any_ostream_representation*)'
../woe32dll/.libs/c++html-styled-ostream.o: In function `html_styled_ostream__write_mem':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/html-styled-ostream.oo.c:58: unded reference to `html_ostream_write_mem(any_ostream_representation*, void const*, unsigned int)'
../woe32dll/.libs/c++term-styled-ostream.o: In function `style_compute_color_value':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:308: unned reference to `term_ostream_rgb_to_color(any_ostream_representation*, int, int, int)'
../woe32dll/.libs/c++term-styled-ostream.o: In function `term_styled_ostream(float, long double,...)(...)':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:107: unned reference to `term_ostream_free(any_ostream_representation*)'
../woe32dll/.libs/c++term-styled-ostream.o: In function `term_styled_ostream__write_mem':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:89: unded reference to `term_ostream_set_color(any_ostream_representation*, int)'
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:90: unded reference to `term_ostream_set_bgcolor(any_ostream_representation*, int)'
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:91: unded reference to `term_ostream_set_weight(any_ostream_representation*, term_weight_t)'
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:92: unded reference to `term_ostream_set_posture(any_ostream_representation*, term_posture_t)'
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:93: unded reference to `term_ostream_set_underline(any_ostream_representation*, term_underline_t)'
../woe32dll/.libs/c++term-styled-ostream.o: In function `term_styled_ostream_create':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:615: unned reference to `term_ostream_free(any_ostream_representation*)'
../woe32dll/.libs/c++term-styled-ostream.o: In function `term_styled_ostream__flush':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:101: unned reference to `term_ostream_flush(any_ostream_representation*)'
../woe32dll/.libs/c++term-styled-ostream.o: In function `term_styled_ostream__write_mem':
c:\Development\Sources\gettext-0.18.1.1\build-win32\gettext-tools\gnulib-lib/term-styled-ostream.oo.c:95: unded reference to `term_ostream_write_mem(any_ostream_representation*, void const*, unsigned int)'
collect2.exe: error: ld returned 1 exit status

make[1]: *** [libgettextlib.la] Error 1
make[1]: Leaving directory `/c/Development/Sources/gettext-0.18.1.1/build-win32/gettext-tools/gnulib-lib'
make: *** [all] Error 2
....
```

I've no clue what's going on and the only reference to the problem that I can find is this: [http://savannah.gnu.org/bugs/?36443](http://savannah.gnu.org/bugs/?36443).

**----- Edit -----**

I dropped down to version 0.17 and was able to compile. It still had a couple problems but I was able to patch it.

---

