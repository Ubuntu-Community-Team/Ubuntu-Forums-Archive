---
title: "Error trying to compile RHVoice - sox_option_default is &quot;undeclared&quot;"
date: 2012-05-20
forum: Packaging and Compiling Programs
---

### Post by El Potro on 2012-05-20
Hello comrades,

I'm trying to compile RHvoice, a voice synthesizer for Russian language, on Ubuntu 10.04.

In order to advance a little, I had to compile and install last versions of libunistring and flite, because the ones available in the repositories are were too outdated for compiling this program.

Now I don't know exactly what to do, because I'm getting this error:

```
p@e:/usr/local/git/RHVoice$ scons
scons: Reading SConscript files ...
Mkdir("build/linux2")
Checking whether the C compiler works(cached) yes
Checking for C library m... (cached) yes
Checking for C header file flite.h... (cached) no
trying to search in /usr/local/include/flite
Checking for C header file flite.h... (cached) yes
Checking for flite_init() in C library flite... (cached) no
Perhaps this version of flite depends on alsa
Checking for C library asound... (cached) yes
Checking for flite_init() in C library flite... (cached) yes
Checking for cst_utf8_explode() in C library flite... (cached) yes
Checking for C library flite_cmulex... (cached) yes
Checking for u8_strconv_to_locale((const uint8_t*)"a") in C library unistring... (cached) yes
Checking for XML_ParserCreate("UTF-8") in C library expat... (cached) yes
Checking for pcre_compile("^$",0,NULL,NULL,NULL) in C library pcre... (cached) yes
Checking for sox_init() in C library sox... (cached) yes
scons: done reading SConscript files.
scons: Building targets ...
gcc -o build/linux2/lib/config.os -c -Wno-unused-function -O2 -fPIC -finput-charset=UTF-8 -DPACKAGE=\"RHVoice\" -DVERSION=\"0.3\" -Dpath_sep=\"\/\" -DSONIC_USE_SIN=1 -DAUDIO_PLAY_NONE=1 -DDATADIR=\"/usr/local/share/RHVoice\" -DCONFDIR=\"/usr/local/etc/RHVoice\" -I/usr/local/include/flite -Ibuild/linux2/lib -Isrc/lib -Isrc/include -Ibuild/linux2/hts_engine_api/include -Isrc/hts_engine_api/include src/lib/config.c
gcc -o build/linux2/lib/en_consonants_lts.os -c -Wno-unused-function -O2 -fPIC -finput-charset=UTF-8 -DPACKAGE=\"RHVoice\" -DVERSION=\"0.3\" -Dpath_sep=\"\/\" -DSONIC_USE_SIN=1 -DAUDIO_PLAY_NONE=1 -DDATADIR=\"/usr/local/share/RHVoice\" -DCONFDIR=\"/usr/local/etc/RHVoice\" -I/usr/local/include/flite -Ibuild/linux2/lib -Isrc/lib -Isrc/include -Ibuild/linux2/hts_engine_api/include -Isrc/hts_engine_api/include src/lib/en_consonants_lts.c
gcc -o build/linux2/lib/io_utils.os -c -Wno-unused-function -O2 -fPIC -finput-charset=UTF-8 -DPACKAGE=\"RHVoice\" -DVERSION=\"0.3\" -Dpath_sep=\"\/\" -DSONIC_USE_SIN=1 -DAUDIO_PLAY_NONE=1 -DDATADIR=\"/usr/local/share/RHVoice\" -DCONFDIR=\"/usr/local/etc/RHVoice\" -I/usr/local/include/flite -Ibuild/linux2/lib -Isrc/lib -Isrc/include -Ibuild/linux2/hts_engine_api/include -Isrc/hts_engine_api/include src/lib/io_utils.c
gcc -o build/linux2/lib/labels.os -c -Wno-unused-function -O2 -fPIC -finput-charset=UTF-8 -DPACKAGE=\"RHVoice\" -DVERSION=\"0.3\" -Dpath_sep=\"\/\" -DSONIC_USE_SIN=1 -DAUDIO_PLAY_NONE=1 -DDATADIR=\"/usr/local/share/RHVoice\" -DCONFDIR=\"/usr/local/etc/RHVoice\" -I/usr/local/include/flite -Ibuild/linux2/lib -Isrc/lib -Isrc/include -Ibuild/linux2/hts_engine_api/include -Isrc/hts_engine_api/include src/lib/labels.c
gcc -o build/linux2/lib/lib.os -c -Wno-unused-function -O2 -fPIC -finput-charset=UTF-8 -DPACKAGE=\"RHVoice\" -DVERSION=\"0.3\" -Dpath_sep=\"\/\" -DSONIC_USE_SIN=1 -DAUDIO_PLAY_NONE=1 -DDATADIR=\"/usr/local/share/RHVoice\" -DCONFDIR=\"/usr/local/etc/RHVoice\" -I/usr/local/include/flite -Ibuild/linux2/lib -Isrc/lib -Isrc/include -Ibuild/linux2/hts_engine_api/include -Isrc/hts_engine_api/include src/lib/lib.c
src/lib/lib.c: In function 'hts_synth':
src/lib/lib.c:911: error: 'sox_option_default' undeclared (first use in this function)
src/lib/lib.c:911: error: (Each undeclared identifier is reported only once
src/lib/lib.c:911: error: for each function it appears in.)
scons: *** [build/linux2/lib/lib.os] Error 1
scons: building terminated because of errors.
```

I'm not very much into compiling programs and source code, can somebody please tell me what does it mean that sox_option_default is "undeclared"?

I already have installed all the packages with the names libsox and sox. Will this be solved if I download and compile the latest versions of sox and libsox?

(ps:before I got to this point, there were problems referring to libunstring when compiling RHVoice. I solved them by compiling and installing the last version of libunstring from git.)

I hope you can help me, thank you very much in advance

---

### Post by Sorbing on 2012-06-18
I get such a error "Checking for XML_ParserCreate("UTF-8") in C library expat... no
Error: cannot link with expat". How to solve this problem?

---

### Post by El Potro on 2012-06-18
Perhaps this will do for you **Sorbing**

```
sudo apt-get install libexpat1-dev
```

As for me: I gave up so far with this attempt. Nobody is helping here. As soon as I find enough free time I will switch to the latest LTS and then I'll try to go on from there.

---

### Post by ikt on 2012-07-07
> **El Potro said:**
> Perhaps this will do for you **Sorbing**

```
sudo apt-get install libexpat1-dev
```

As for me: I gave up so far with this attempt. Nobody is helping here. As soon as I find enough free time I will switch to the latest LTS and then I'll try to go on from there.

Thank you kind sir, I was having a small problem:

```
checking for XML_ParserCreate in -lexpat... no
configure: error: Expat not found
```

When trying to install jabberd-2.2.16 on my debian server.

> sudo apt-get install libexpat1-dev

Fixed it, and now I move onto the next issue...

---

### Post by El Potro on 2012-07-07
I'm glad this helped you **ikt**. Regards.

---

### Post by SevenMachines on 2012-07-10
src/lib/lib.c:
```
#ifndef SOX_OPTION_DEFAULT
#define SOX_OPTION_DEFAULT sox_option_default
#endif
```
but
```
$ grep -ri sox_option_default /usr/include/sox.h 
typedef enum {SOX_OPTION_NO, SOX_OPTION_YES, SOX_OPTION_DEFAULT} sox_option_t;
```
So SOX_OPTION_DEFAULT is an enum value so the lib.c test will fail and the preprocessor define will take place and break the code, at least on my machine. 
Try removing the define from lib.c, should be ok, but I don't know when api's changed and so on

---

