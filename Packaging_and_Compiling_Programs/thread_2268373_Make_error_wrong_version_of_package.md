---
title: "Make error: wrong version of package???"
date: 2015-03-08
forum: Packaging and Compiling Programs
---

### Post by fscheltens-t on 2015-03-08
Ok a little history to put things into perspective: 

I was trying to make some video this week, and had lots of problems. One of which: Kdenlive (the version as installed by Ubuntu repositories) had a massive memory leak. Today i installed the latest version of KDenlive from the webpage (using apt-get).
When i saw the configuration screen, i noticed i had an old version of MLT, so i decided to get the latest stable version of that:

- I had to compile MTL-0.9.6
- when i ran the configure script, it was recomended to install the frei0r plugins. So i went to compile frei0r-plugins-1.4
- For that, i had to compile m4-1.4.1.tar and autoconf_2.69-18_all

Still with me?

- As far as i can tell, i succesfully made the M4 and  autoconf packages. 
- i then re-ran the ./configure script for the frei0r plugin
- Then i made the frei0r plugins package, i got the following output:

> florian@MuziekPC:~/Downloads/frei0r-plugins-1.4$ make
Making all in src
make[1]: Map '/home/florian/Downloads/frei0r-plugins-1.4/src' wordt binnengegaan
make[1]: Er hoeft niets gedaan te worden voor 'all'.
make[1]: Map '/home/florian/Downloads/frei0r-plugins-1.4/src' wordt verlaten
Making all in include
make[1]: Map '/home/florian/Downloads/frei0r-plugins-1.4/include' wordt binnengegaan
(CDPATH="${ZSH_VERSION+.}:" && cd .. && /bin/bash /home/florian/Downloads/frei0r-plugins-1.4/missing autoheader)
autom4te: need GNU m4 1.4 or later: /usr/bin/m4
autoheader: '/usr/bin/autom4te' failed with exit status: 1
make[1]: *** [config.h.in] Fout 1
make[1]: Map '/home/florian/Downloads/frei0r-plugins-1.4/include' wordt verlaten
make: *** [all-recursive] Fout 1

- How can i tell if the m4 package was correctly installed?
-Am i missing anything else to get this done? 

( FYI: I did in fact check the package "build-essential" in package manager, and it was marked as installed )

Thanks for your help!

EDIT:

I just updated to the latest version of "frei0r plugins" and installed "frei0r-plugins-dev (header files)" using symantic package manager. I still want to know what went wrong before, just for learning purposes. Cheers!


Edit2:

The plot thickens... I just compiled mlt-0.9.6 . After also installing some headers for ALSA, it completed.
I then started the application kdenlive again. The configuration screen again says it detects 0.9.3 !
So something must have gone wrong there also. I have included the output from compilation below (was going to attach a text file, but apparently it was too big.)
Can anyone tell me if something went wrong there?

> 
florian@MuziekPC:~/Downloads/mlt-0.9.6$ ./configure
Configuring framework:
Configuring modules:
Configuring modules/avformat:
- libavformat not found: disabling
Configuring modules/core:
Configuring modules/decklink:
Configuring modules/feeds:
Configuring modules/frei0r:
Configuring modules/gtk2:
- GTK2 components not found: disabling
Configuring modules/jackrack:
- jackrack not found: disabling
Configuring modules/kdenlive:
Configuring modules/lumas:
Configuring modules/oldfilm:
Configuring modules/opengl:
- movit not found: disabling
Configuring modules/plus:
Configuring modules/rtaudio:
Configuring modules/sdl:
- sdl development libs not found: disabling
Configuring modules/sox:
- sox not found: disabling
Configuring modules/swfdec:
- swfdec not found: disabling
Configuring modules/vmfx:
Configuring modules/xml:
- xml2 not found: disabling xml module
Configuring mlt++:
Configuring swig:
LGPLv2.1 license used; GPL components disabled
florian@MuziekPC:~/Downloads/mlt-0.9.6$ make
list='src/framework src/mlt++ src/melt src/modules src/swig profiles'; \
    for subdir in $list; do \
        make -s -C $subdir depend || exit 1; \
        make -C $subdir all || exit 1; \
    done
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/framework' wordt binnengegaan
make[1]: Er hoeft niets gedaan te worden voor 'all'.
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/framework' wordt verlaten
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/mlt++' wordt binnengegaan
make[1]: Er hoeft niets gedaan te worden voor 'all'.
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/mlt++' wordt verlaten
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/melt' wordt binnengegaan
make[1]: Er hoeft niets gedaan te worden voor 'all'.
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/melt' wordt verlaten
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules' wordt binnengegaan
list='decklink gtk2 kino vmfx oldfilm rtaudio motion_est sdl sox plusgpl vid.stab videostab vorbis dv xine swfdec core linsys normalize feeds xml plus frei0r opengl resample avformat jackrack qt lumas kdenlive'; \
    for subdir in $list; do \
        if [ -f $subdir/Makefile -a ! -f disable-$subdir -a ! -f $subdir/deprecated ] ; \
        then make -C $subdir all || exit 1; \
        fi \
    done
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/decklink' wordt binnengegaan
make[2]: 'all' is bijgewerkt.
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/decklink' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/vmfx' wordt binnengegaan
make[2]: Er hoeft niets gedaan te worden voor 'all'.
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/vmfx' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/oldfilm' wordt binnengegaan
make[2]: Er hoeft niets gedaan te worden voor 'all'.
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/oldfilm' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/rtaudio' wordt binnengegaan
g++ -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread -Wno-deprecated -Wno-multichar -fno-rtti -D__LINUX_ALSA__ -I/usr/include/alsa     -c -o RtAudio.o RtAudio.cpp
g++ -shared -o ../libmltrtaudio.so consumer_rtaudio.o RtAudio.o -L../../framework -lmlt -lpthread -Wl,--no-undefined -Wl,--as-needed -lasound  
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/rtaudio' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/core' wordt binnengegaan
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o factory.o factory.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_colour.o producer_colour.c
In file included from /usr/include/string.h:640:0,
                 from producer_colour.c:26:
In function &#8216;memset&#8217;,
    inlined from &#8216;producer_get_image&#8217; at producer_colour.c:180:9:
/usr/include/x86_64-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_consumer.o producer_consumer.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_hold.o producer_hold.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_loader.o producer_loader.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_melt.o producer_melt.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_noise.o producer_noise.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_tone.o producer_tone.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_audiochannels.o filter_audiochannels.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_audioconvert.o filter_audioconvert.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_audiowave.o filter_audiowave.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_brightness.o filter_brightness.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_channelcopy.o filter_channelcopy.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_crop.o filter_crop.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_data_feed.o filter_data_feed.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_data_show.o filter_data_show.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_fieldorder.o filter_fieldorder.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_gamma.o filter_gamma.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_greyscale.o filter_greyscale.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_imageconvert.o filter_imageconvert.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_luma.o filter_luma.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_mirror.o filter_mirror.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_mono.o filter_mono.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_obscure.o filter_obscure.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_panner.o filter_panner.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_region.o filter_region.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_rescale.o filter_rescale.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_resize.o filter_resize.c
In file included from /usr/include/string.h:640:0,
                 from filter_resize.c:25:
In function &#8216;memset&#8217;,
    inlined from &#8216;resize_alpha&#8217; at filter_resize.c:41:9,
    inlined from &#8216;frame_resize_image&#8217; at filter_resize.c:156:10,
    inlined from &#8216;filter_get_image&#8217; at filter_resize.c:276:30:
/usr/include/x86_64-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_transition.o filter_transition.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_watermark.o filter_watermark.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o transition_composite.o transition_composite.c
In file included from /usr/include/string.h:640:0,
                 from transition_composite.c:26:
In function &#8216;memset&#8217;,
    inlined from &#8216;transition_get_image&#8217; at transition_composite.c:1257:11:
/usr/include/x86_64-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
In function &#8216;memset&#8217;,
    inlined from &#8216;transition_get_image&#8217; at transition_composite.c:1260:11:
/usr/include/x86_64-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o transition_luma.o transition_luma.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o transition_mix.o transition_mix.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o transition_region.o transition_region.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o transition_matte.o transition_matte.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o consumer_multi.o consumer_multi.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o consumer_null.o consumer_null.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o composite_line_yuv_sse2_simple.o composite_line_yuv_sse2_simple.c
In file included from /usr/include/string.h:640:0,
                 from composite_line_yuv_sse2_simple.c:22:
In function &#8216;memset&#8217;,
    inlined from &#8216;composite_line_yuv_sse2_simple&#8217; at composite_line_yuv_sse2_simple.c:252:19:
/usr/include/x86_64-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
cc -shared -o ../libmltcore.so factory.o producer_colour.o producer_consumer.o producer_hold.o producer_loader.o producer_melt.o producer_noise.o producer_tone.o filter_audiochannels.o filter_audioconvert.o filter_audiowave.o filter_brightness.o filter_channelcopy.o filter_crop.o filter_data_feed.o filter_data_show.o filter_fieldorder.o filter_gamma.o filter_greyscale.o filter_imageconvert.o filter_luma.o filter_mirror.o filter_mono.o filter_obscure.o filter_panner.o filter_region.o filter_rescale.o filter_resize.o filter_transition.o filter_watermark.o transition_composite.o transition_luma.o transition_mix.o transition_region.o transition_matte.o consumer_multi.o consumer_null.o composite_line_yuv_sse2_simple.o  -L../../framework -lmlt -lm -lpthread -Wl,--no-undefined -Wl,--as-needed
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/core' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/feeds' wordt binnengegaan
make[2]: Er hoeft niets gedaan te worden voor 'all'.
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/feeds' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/plus' wordt binnengegaan
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o consumer_blipflash.o consumer_blipflash.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o factory.o factory.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_affine.o filter_affine.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_charcoal.o filter_charcoal.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_dynamictext.o filter_dynamictext.c
filter_dynamictext.c: In function &#8216;filter_get_image&#8217;:
filter_dynamictext.c:272:12: warning: unused variable &#8216;a_frame&#8217; [-Wunused-variable]
  mlt_frame a_frame = 0;
            ^
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_invert.o filter_invert.c
In file included from /usr/include/string.h:640:0,
                 from filter_invert.c:26:
In function &#8216;memset&#8217;,
    inlined from &#8216;filter_get_image&#8217; at filter_invert.c:62:10:
/usr/include/x86_64-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_lift_gamma_gain.o filter_lift_gamma_gain.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_loudness.o filter_loudness.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_lumakey.o filter_lumakey.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_rgblut.o filter_rgblut.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_sepia.o filter_sepia.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_blipflash.o producer_blipflash.c
In file included from /usr/include/string.h:640:0,
                 from producer_blipflash.c:25:
In function &#8216;memset&#8217;,
    inlined from &#8216;producer_get_image&#8217; at producer_blipflash.c:237:9:
/usr/include/x86_64-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_count.o producer_count.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o transition_affine.o transition_affine.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o ebur128/ebur128.o ebur128/ebur128.c
ebur128/ebur128.c: In function &#8216;ebur128_init&#8217;:
ebur128/ebur128.c:322:1: warning: label &#8216;free_short_term_block_energy_histogram&#8217; defined but not used [-Wunused-label]
 free_short_term_block_energy_histogram:
 ^
ebur128/ebur128.c:235:16: warning: unused variable &#8216;result&#8217; [-Wunused-variable]
   int errcode, result;
                ^
cc -shared -o ../libmltplus.so consumer_blipflash.o factory.o filter_affine.o filter_charcoal.o filter_dynamictext.o filter_invert.o filter_lift_gamma_gain.o filter_loudness.o filter_lumakey.o filter_rgblut.o filter_sepia.o producer_blipflash.o producer_count.o transition_affine.o ebur128/ebur128.o -L../../framework -lmlt -lm -lpthread -Wl,--no-undefined -Wl,--as-needed
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/plus' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/frei0r' wordt binnengegaan
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread     -c -o factory.o factory.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread     -c -o producer_frei0r.o producer_frei0r.c
producer_frei0r.c: In function &#8216;producer_get_frame&#8217;:
producer_frei0r.c:77:18: warning: unused variable &#8216;producer_props&#8217; [-Wunused-variable]
   mlt_properties producer_props = MLT_PRODUCER_PROPERTIES( producer );
                  ^
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread     -c -o filter_frei0r.o filter_frei0r.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread     -c -o transition_frei0r.o transition_frei0r.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread     -c -o frei0r_helper.o frei0r_helper.c
cc -shared -o ../libmltfrei0r.so factory.o producer_frei0r.o filter_frei0r.o transition_frei0r.o frei0r_helper.o -L../../framework -lmlt -Wl,--no-undefined -Wl,--as-needed -lm -ldl  
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/frei0r' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/lumas' wordt binnengegaan
cc -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread    luma.c   -o luma
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/lumas' wordt verlaten
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/kdenlive' wordt binnengegaan
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o factory.o factory.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_boxblur.o filter_boxblur.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_freeze.o filter_freeze.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o filter_wave.o filter_wave.c
cc -I../.. -DARCH_X86_64 -Wall -DPIC   -O2 -pipe -fno-tree-dominator-opts -fno-tree-pre -ffast-math -DUSE_MMX -DUSE_SSE -DUSE_SSE2 -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fPIC -pthread   -c -o producer_framebuffer.o producer_framebuffer.c
cc -shared -o ../libmltkdenlive.so factory.o filter_boxblur.o filter_freeze.o filter_wave.o producer_framebuffer.o -L../../framework -lmlt -Wl,--no-undefined -Wl,--as-needed -lm
make[2]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules/kdenlive' wordt verlaten
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/modules' wordt verlaten
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/swig' wordt binnengegaan
list=''; \
    for subdir in $list; do \
        if [ -x $subdir/build -a ! -f .$subdir -o all = clean ] ; \
        then echo -n Building $subdir... ; \
            cd $subdir && output=$(CXXFLAGS="" ./build all 2>&1) ; \
            if [ $? -eq 0 ] ; \
            then echo OK && touch ../.$subdir ; \
            else echo $output && exit 1 ; \
            fi ; \
            cd .. ; \
            if [ -f $subdir/Makefile -a -f .$subdir ] ; \
            then make -C $subdir all || exit 1 ; \
            fi ; \
            if [ all = clean ] ; \
            then rm -f .$subdir ; \
            fi ; \
        fi \
    done
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/src/swig' wordt verlaten
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/profiles' wordt binnengegaan
make[1]: Er hoeft niets gedaan te worden voor 'all'.
make[1]: Map '/home/florian/Downloads/mlt-0.9.6/profiles' wordt verlaten





EDIT 3:

I just did a little test. i <think> that i can now run kdenlive without memory leak, even without the newer version of mlt. Fingers crossed \\:D/ :-k
Even so, i'm still curious about what went wrong, any info appreciated.

---

