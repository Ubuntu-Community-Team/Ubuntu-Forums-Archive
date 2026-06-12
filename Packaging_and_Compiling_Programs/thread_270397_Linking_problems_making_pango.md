---
title: "Linking problems making pango"
date: 2006-10-03
forum: Packaging and Compiling Programs
---

### Post by americux on 2006-10-03
Hello everybody,
I'm trying to install pango (1.14.4 in Ubuntu Dapper desktop 2.6.15-27-386) from sources. The ./configure had no problem, but when I make "make" the result is:
...
...
/usr/local/lib/libcairo.so: undefined reference to `png_set_read_user_transform_fn@PNG12_0'
/usr/local/lib/libcairo.so: undefined reference to `png_set_gray_1_2_4_to_8@PNG12_0'
/usr/local/lib/libcairo.so: undefined reference to `png_set_tIME@PNG12_0'
/usr/local/lib/libcairo.so: undefined reference to `png_set_write_user_transform_fn@PNG12_0'
/usr/local/lib/libcairo.so: undefined reference to `png_set_strip_16@PNG12_0'
collect2: ld returned 1 exit status
make[3]: *** [pango-view] Error 1
make[3]: se sale del directorio `/usr/src/pango-1.14.4/examples'
make[2]: *** [all] Error 2
make[2]: se sale del directorio `/usr/src/pango-1.14.4/examples'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/usr/src/pango-1.14.4'
make: *** [all] Error 2

To say that libcairo.so and libpng.so exit in /usr/local/lib and in /usr/lib.
Other thing that happen is that I need to configure and to make being root. I've to run them putting first sudo, if not, it tell me: permission denied.

I tried editting /etc/ld.so.conf (which didn't exit),  adding the line /usr/local/lib, running sudo ldconfing, moving files form /usr/local/lib/pkgconfig to /usr/lib/pkgconfig and creating the soft link to /usr/lib/pkgconfig in /usr/local/lib/pkgconfig and didn't work.

I tried to set PKG_CONFIG_PATH and LD_LIBRARY_PATH but again, unsuccesfully. Maybe I don't set these variables correctly.

Somebody could help me? :-k  Thank you anyway, A.

---

### Post by americux on 2006-11-02
I solved my linking problems reinstalling the denpendent packages.
See ya, a.

---

