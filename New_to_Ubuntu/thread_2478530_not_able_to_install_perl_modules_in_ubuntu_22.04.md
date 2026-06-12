---
title: "not able to install perl modules in ubuntu 22.04"
date: 2022-08-29
forum: New to Ubuntu
---

### Post by rskhome on 2022-08-29
Hi all,

When i try to install perl module, I receive below message. please help me what i have to do to fix this issue?

cpan[1]> install Image::Magick                                                  
Reading '/root/.cpan/Metadata'
  Database was generated on Mon, 29 Aug 2022 14:41:02 GMT
Running install for module 'Image::Magick'
Checksum for /root/.cpan/sources/authors/id/J/JC/JCRISTY/Image-Magick-7.0.11-3.tar.gz ok
Scanning cache /root/.cpan/build for sizes
............................................................................DONE
Configuring J/JC/JCRISTY/Image-Magick-7.0.11-3.tar.gz with Makefile.PL
Checking if your kit is complete...
Looks good
Have /usr/lib/x86_64-linux-gnu/perl-base
Want /usr/lib/x86_64-linux-gnu/perl/5.34
Your perl and your Config.pm seem to have different ideas about the
architecture they are running on.
Perl thinks: [perl-base]
Config says: [x86_64-linux-gnu-thread-multi]
This may or may not cause problems. Please check your installation of perl
if you have problems building this extension.
Warning (mostly harmless): No library found for -lMagickCore-7.Q16HDRI
Generating a Unix-style Makefile
Writing Makefile for Image::Magick
Writing MYMETA.yml and MYMETA.json
  JCRISTY/Image-Magick-7.0.11-3.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- OK
Running make for J/JC/JCRISTY/Image-Magick-7.0.11-3.tar.gz
cp Magick.pm blib/lib/Image/Magick.pm
AutoSplitting blib/lib/Image/Magick.pm (blib/lib/auto/Image/Magick)
Running Mkbootstrap for Magick ()
chmod 644 "Magick.bs"
"/usr/bin/perl" -MExtUtils::Command::MM -e 'cp_nonempty' -- Magick.bs blib/arch/auto/Image/Magick/Magick.bs 644
"/usr/bin/perl" "/usr/share/perl/5.34/ExtUtils/xsubpp"  -typemap '/usr/share/perl/5.34/ExtUtils/typemap' -typemap '/root/.cpan/build/Image-Magick-7.0.11-5/typemap'  Magick.xs > Magick.xsc
mv Magick.xsc Magick.c
x86_64-linux-gnu-gcc -c  -I/usr/local/include/ImageMagick-7 -DMAGICKCORE_HDRI_ENABLE=1 -DMAGICKCORE_QUANTUM_DEPTH=16 -I/usr/include/libxml2 -I"/usr/include/ImageMagick-7" -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fwrapv -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/freetype2 -g -O2 -Wall -pthread -DMAGICKCORE_HDRI_ENABLE=1 -DMAGICKCORE_QUANTUM_DEPTH=16 -O2 -g   -DVERSION=\"7.0.11\" -DXS_VERSION=\"7.0.11\" -fPIC "-I/usr/lib/x86_64-linux-gnu/perl/5.34/CORE"  -D_LARGE_FILES=1 -DHAVE_CONFIG_H Magick.c
Magick.xs:56:10: fatal error: MagickCore/MagickCore.h: No such file or directory
   56 | #include <MagickCore/MagickCore.h>
      |          ^~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
make: *** [Makefile:351: Magick.o] Error 1
  JCRISTY/Image-Magick-7.0.11-3.tar.gz
  /usr/bin/make -- NOT OK
Failed during this command:
 JCRISTY/Image-Magick-7.0.11-3.tar.gz         : make NO

cpan[2]>  

regards,
Srikrishnan

---

