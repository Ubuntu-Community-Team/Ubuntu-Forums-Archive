---
title: "Make Muine get covers and play aac/m4a"
date: 2005-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by tmowerman on 2005-10-05
Well muine annoyed me because it stopped downloading cover images and refused to play aac files.  Here is my fix.  It is probably really poor but I hope I help someone.  If anyone has any suggestions as to how to do it better, ie build a proper package, let me know.  Oh you need to sign up to use Amazon web services from 
[Amazon web services]("http://www.amazon.com/gp/browse.html/103-3726852-4756629?%5Fencoding=UTF8&node=3435361")
Any way we need to get the build dependencies to build muine.  Like so.
```
sudo apt-get build-dep muine
```
And for AAC playback
```
sudo apt-get install libfaad2-dev
```
And, annoyingly you also need to save this file
[http://cvs.sourceforge.net/viewcvs.py/*checkout*/faac/faad2/common/mp4ff/mp4ff_int_types.h]("http://cvs.sourceforge.net/viewcvs.py/*checkout*/faac/faad2/common/mp4ff/mp4ff_int_types.h")
into /usr/local/include 
Now we want a directory for our source to go into
```
mkdir ~/src
```
```
cd ~/src
```
Now with the magic of apt, we get the source
```
sudo apt-get source muine
```
Now change to the newly created source directory
```
cd muine-0.8.3
```
Next you wget the patch from my webspace. 
```
wget www.elemoto.com/tim/patch
```
then
```
nano patch
```
and change Get A DEVTAG!!!!! to your own devtag
Then we apply the patch
```
patch -p1 <patch
```
and hopefully it will say patch applied.  
Now we do the standard
```
./configure
```
```
make
```
```
sudo checkinstall
```
and give the package the name muine.  
Hope it works for you, now if anyone can make amarok add aac to its collection, or make the muine inotify patches from the mailing list work I will be happy.  I actually had the inotify working, but it broke audioscrobbler.  And iinvolved hunting through the muine mailing list to find both inotify patches.  
Happy Music Listening
Tim

---

### Post by green_lifesaver on 2005-10-10
Hello

   Thank-you for writing this mini how-to, I am a new Linux user who just installed Ubuntu last night on my pc. I am switching over from mac os x and it is really important for me to be able to play my aac files that I already have, I do have muine running at the moment but it is unable to playback any aac files. I tried installing FAAC/FAAC as well as an updated Gstreamer but nothing seems able to make it play back AAC. So I tried to build from source using your guide. I went through all of the instructions that you have made but there seems to be a problem on my system. the ./configure part seems to work fine but when I go to "make" the file, I get the following error.

```
my name@host:~/muine-0.8.3$ make
make  all-recursive
make[1]: Entering directory `/home/matt/muine-0.8.3'
Making all in data
make[2]: Entering directory `/home/matt/muine-0.8.3/data'
Making all in glade
make[3]: Entering directory `/home/matt/muine-0.8.3/data/glade'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/matt/muine-0.8.3/data/glade'
Making all in images
make[3]: Entering directory `/home/matt/muine-0.8.3/data/images'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/matt/muine-0.8.3/data/images'
Making all in ui
make[3]: Entering directory `/home/matt/muine-0.8.3/data/ui'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/matt/muine-0.8.3/data/ui'
make[3]: Entering directory `/home/matt/muine-0.8.3/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/matt/muine-0.8.3/data'
make[2]: Leaving directory `/home/matt/muine-0.8.3/data'
Making all in libmuine
make[2]: Entering directory `/home/matt/muine-0.8.3/libmuine'
Making all in id3-vfs
make[3]: Entering directory `/home/matt/muine-0.8.3/libmuine/id3-vfs'
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DG_LOG_DOMAIN=\"id3-vfs\" -I../.. -DORBIT2=1 -pthread -DXTHREADS -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libbonobo-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/gstreamer-0.8 -I/usr/include/libxml2    -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare -Werror  -DG_DISABLE_DEPRECATED    -g -O2 -MT id3-vfs.lo -MD -MP -MF ".deps/id3-vfs.Tpo" \
  -c -o id3-vfs.lo `test -f 'id3-vfs.c' || echo './'`id3-vfs.c; \
then mv -f ".deps/id3-vfs.Tpo" ".deps/id3-vfs.Plo"; \
else rm -f ".deps/id3-vfs.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DG_LOG_DOMAIN=\"id3-vfs\" -I../.. -DORBIT2=1 -pthread -DXTHREADS -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libbonobo-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/gstreamer-0.8 -I/usr/include/libxml2 -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare -Werror -DG_DISABLE_DEPRECATED -g -O2 -MT id3-vfs.lo -MD -MP -MF .deps/id3-vfs.Tpo -c id3-vfs.c  -fPIC -DPIC -o .libs/id3-vfs.o
In file included from id3-vfs.c:23:
id3-vfs.h:27:20: id3tag.h: No such file or directory
In file included from id3-vfs.c:44:
tag.h:25:21: id3tag.h: No such file or directory
In file included from id3-vfs.c:45:
field.h:25:21: id3tag.h: No such file or directory
In file included from id3-vfs.c:45:
field.h:27: warning: `enum id3_field_type' declared inside parameter list
field.h:27: warning: its scope is only this definition or declaration, which is probably not what you want
field.h:27: warning: `union id3_field' declared inside parameter list
field.h:27: warning: parameter has incomplete type
field.h:28: warning: `union id3_field' declared inside parameter list
field.h:30: warning: `union id3_field' declared inside parameter list
field.h:32: error: syntax error before "id3_byte_t"
field.h:33: warning: `union id3_field' declared inside parameter list
field.h:35: error: syntax error before "id3_field_render"
field.h:35: error: syntax error before "id3_byte_t"
field.h:36: warning: `union id3_field' declared inside parameter list
field.h:36: warning: type defaults to `int' in declaration of `id3_field_render'field.h:36: warning: data definition has no type or storage class
id3-vfs.c:51: error: syntax error before "id3_length_t"
id3-vfs.c:51: warning: no semicolon at end of struct or union
id3-vfs.c: In function `query_tag':
id3-vfs.c:76: error: `id3_byte_t' undeclared (first use in this function)
id3-vfs.c:76: error: (Each undeclared identifier is reported only once
id3-vfs.c:76: error: for each function it appears in.)
id3-vfs.c:76: error: syntax error before "query"
id3-vfs.c:82: error: `query' undeclared (first use in this function)
id3-vfs.c:83: warning: implicit declaration of function `id3_tag_query'
id3-vfs.c: At top level:
id3-vfs.c:97: error: syntax error before "id3_length_t"
id3-vfs.c: In function `read_tag':
id3-vfs.c:101: error: `id3_byte_t' undeclared (first use in this function)
id3-vfs.c:101: error: `data' undeclared (first use in this function)
id3-vfs.c:104: error: `size' undeclared (first use in this function)
id3-vfs.c:106: error: `iofile' undeclared (first use in this function)
id3-vfs.c:109: warning: implicit declaration of function `id3_tag_parse'
id3-vfs.c:109: warning: assignment makes pointer from integer without a cast
id3-vfs.c: In function `update_primary':
id3-vfs.c:127: error: dereferencing pointer to incomplete type
id3-vfs.c:127: error: `ID3_TAG_EXTENDEDFLAG_TAGISANUPDATE' undeclared (first use in this function)
id3-vfs.c:128: warning: implicit declaration of function `id3_tag_clearframes'
id3-vfs.c:130: error: dereferencing pointer to incomplete type
id3-vfs.c:131: warning: implicit declaration of function `id3_tag_attachframe'
id3-vfs.c:131: error: dereferencing pointer to incomplete type
id3-vfs.c: At top level:
id3-vfs.c:143: error: syntax error before "id3_length_t"
id3-vfs.c: In function `add_tag':
id3-vfs.c:147: error: storage size of `filetag' isn't known
id3-vfs.c:150: error: `file' undeclared (first use in this function)
id3-vfs.c:158: error: `length' undeclared (first use in this function)
id3-vfs.c:172: error: dereferencing pointer to incomplete type
id3-vfs.c:183: warning: implicit declaration of function `id3_tag_delete'
id3-vfs.c:147: warning: unused variable `filetag'
id3-vfs.c: In function `search_tags':
id3-vfs.c:240: warning: implicit declaration of function `id3_tag_findframe'
id3-vfs.c:240: error: invalid use of undefined type `struct vfstag'
id3-vfs.c:240: error: invalid use of undefined type `struct vfstag'
id3-vfs.c:240: error: dereferencing pointer to incomplete type
id3-vfs.c:240: warning: assignment makes pointer from integer without a cast
id3-vfs.c:243: warning: implicit declaration of function `id3_field_getint'
id3-vfs.c:243: error: dereferencing pointer to incomplete type
id3-vfs.c: In function `finish_file':
id3-vfs.c:300: error: invalid use of undefined type `struct vfstag'
id3-vfs.c:300: error: dereferencing pointer to incomplete type
id3-vfs.c:301: error: invalid use of undefined type `struct vfstag'
id3-vfs.c:301: error: dereferencing pointer to incomplete type
id3-vfs.c: In function `new_file':
id3-vfs.c:331: warning: implicit declaration of function `id3_tag_new'
id3-vfs.c:331: warning: assignment makes pointer from integer without a cast
id3-vfs.c: In function `id3_vfs_update':
id3-vfs.c:417: error: `id3_length_t' undeclared (first use in this function)
id3-vfs.c:417: error: syntax error before "size"
id3-vfs.c:424: error: dereferencing pointer to incomplete type
id3-vfs.c:424: error: `ID3_TAG_OPTION_ID3V1' undeclared (first use in this function)
id3-vfs.c:426: error: `size' undeclared (first use in this function)
id3-vfs.c:426: warning: implicit declaration of function `id3_tag_render'
id3-vfs.c:438: error: dereferencing pointer to incomplete type
make[3]: *** [id3-vfs.lo] Error 1
make[3]: Leaving directory `/home/matt/muine-0.8.3/libmuine/id3-vfs'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matt/muine-0.8.3/libmuine'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matt/muine-0.8.3'
make: *** [all] Error 2

```

This is the first program I have ever tried to build from source so please bear with me if this is painfully obvious what I should have done, but I have spent around four hours researching this and trying to come to up with my own solution with no luck. If anyone could help me it would be greatly appreciated!

---

