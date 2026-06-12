---
title: "Problem with libpng while trying to install Stage-3.2.2"
date: 2011-03-02
forum: Packaging and Compiling Programs
---

### Post by sharonshabtai on 2011-03-02
I got the following error while running make on stage-3.2.2
after looking looking around the web I have already installed these packages:
(im working on ubunto i686 -> if it helps :P )

freeglut3 (for stage)
freeglut3-dev (for stage)
libfltk1.1 (for stage)
libfltk1.1-dev (for stage)
libgtk2.0-dev (for stage)
libltdl7 (for stage)
libltdl7-dev (for stage)
libpng12-0 (for stage)
libpng12-0-dev (for stage) 

and still I get the same errors

-----------------------------------

Linking CXX shared library libstage.so
[ 59%] Built target stage
[ 61%] Building CXX object libstage/CMakeFiles/stagebinary.dir/main.o
Linking CXX executable stage
libstage.so.3.2.2: undefined reference to `png_create_info_struct'
libstage.so.3.2.2: undefined reference to `png_set_IHDR'
libstage.so.3.2.2: undefined reference to `png_set_rows'
libstage.so.3.2.2: undefined reference to `png_destroy_write_struct'
libstage.so.3.2.2: undefined reference to `png_init_io'
libstage.so.3.2.2: undefined reference to `png_write_png'
libstage.so.3.2.2: undefined reference to `fl_register_images()'
libstage.so.3.2.2: undefined reference to `Fl_PNG_Image::Fl_PNG_Image(char const*)'
libstage.so.3.2.2: undefined reference to `png_create_write_struct'
collect2: ld returned 1 exit status
make[2]: *** [libstage/stage] Error 1
make[1]: *** [libstage/CMakeFiles/stagebinary.dir/all] Error 2
make: *** [all] Error 2


----------------------------

any help would be very much appreciated

---

