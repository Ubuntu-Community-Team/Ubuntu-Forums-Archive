---
title: "Can't compile speech tools! To use -fno-strict-aliasing maybe?"
date: 2008-06-07
forum: Packaging and Compiling Programs
---

### Post by pavallokazzo on 2008-06-07
Hello everyone!
I'm loosing alot of time trying to get festival+mbrola to work and till now it's only frustation... :mad:
I've tried different howtos and I've reached this one: [http://ilpinguino.altervista.org/doc/sintesi_vocale.html](http://ilpinguino.altervista.org/doc/sintesi_vocale.html)
It's in italian, ok, but basically tells to download those files listed, extract all in work directory (it will create two dirs, festival and speech tools) and then compile the two programs.
Now the problem appears while compiling...

Speech tools dies with those lines:
```
../include/EST_TMatrix.h:310: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TMatrix<T>&)’ declares a non-template function
slib.cc: In function ‘void gc_mark_and_sweep()’:
slib.cc:1088: warning: dereferencing type-punned pointer will break strict-aliasing rules
gmake[1]: *** [slib.o] Error 1
gmake: *** [siod] Error 2

```

Festival (against repository version of speech tools, a different version (reppo 1.2.96-betaubuntusomething, sources from festival website 1.2.95.betasomething), so maybe that's why!):
```

../../../../speech_tools/include/EST_THandle.h: At global scope:
../../../../speech_tools/include/EST_THandle.h:140: warning: friend declaration ‘int operator==(const EST_THandle<BoxT, ObjectT>&, const EST_THandle<BoxT, ObjectT>&)’ declares a non-template function
../../../../speech_tools/include/EST_THandle.h:141: warning: friend declaration ‘int operator!=(const EST_THandle<BoxT, ObjectT>&, const EST_THandle<BoxT, ObjectT>&)’ declares a non-template function
../../../../speech_tools/include/EST_THandle.h:143: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_THandle<BoxT, ObjectT>&)’ declares a non-template function
gmake[3]: *** [festival.o] Error 1
gmake[2]: *** [festival] Error 2
gmake[1]: *** [arch] Error 2
gmake: *** [src] Error 2
```

I tried changing gcc to 3.1 (cd /usr/bin; sudo rm gcc; sudo ln -s gcc-3.1 gcc) but results are the same...


Anyone who can help me?

PS = I'm running Kubuntu Hardy not upgraded (installed from Ubuntu Hardy cd then switched to kubuntu-desktop) and not really up-to-date (I should download 500 mb of update?!?!?!?)!

LOG
Speech Tools
```
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/speech_tools$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for ar... ar
checking whether byte ordering is bigendian... no
checking for tputs in -ltermcap... no
checking for tputs in -lncurses... no
updating cache ./config.cache
creating ./config.status
creating config/config
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/speech_tools$ gmake
bash: gmake: command not found
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/speech_tools$ sudo gmake
sudo: gmake: command not found
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/speech_tools$ sudo apt-get install gmake
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso
Reading state information... Fatto
E: Impossibile trovare gmake
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/speech_tools$ sudo ln -s /usr/bin/make /usr/bin/gmake
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/speech_tools$ gmake
Check system type
Remake modincludes.inc
        NATIVE_AUDIO
                ok
        EDITLINE
                config/modules/editline.mak
        SIOD
                siod/siod.mak
        WAGON
                stats/wagon/wagon.mak
        SCFG
                grammar/scfg/scfg.mak
        WFST
                grammar/wfst/wfst.mak
        OLS
                stats/ols.mak
        RXP
                rxp/rxp.mak
        LINUX16_AUDIO
                config/modules/linux16_audio.mak
Making in directory ./siod ...
making dependencies -- siodeditline.c el_complete.c editline.c el_sys_unix.c slib.cc slib_core.cc slib_doc.cc slib_file.cc slib_format.cc slib_list.cc slib_math.cc slib_sys.cc slib_server.cc slib_str.cc slib_xtr.cc slib_repl.cc siod_fringe.cc siod_server.cc io.cc trace.cc EST_SiodServer.cc siod.cc siod_est.cc
gcc -c -fno-implicit-templates -O3 -Wall -DSUPPORT_EDITLINE -I../include slib.cc
In file included from /usr/include/c++/4.2/backward/iostream.h:31,
                 from ../include/EST_iostream.h:52,
                 from ../include/EST_String.h:50,
                 from ../include/siod.h:17,
                 from slib.cc:88:
/usr/include/c++/4.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
In file included from ../include/EST_String.h:53,
                 from ../include/siod.h:17,
                 from slib.cc:88:
../include/EST_Chunk.h:131: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:132: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:133: error: ‘EST_ChunkPtr’ does not name a type
../include/EST_Chunk.h:135: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:136: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:138: error: ‘EST_ChunkPtr’ has not been declared
../include/EST_Chunk.h:139: error: ‘EST_ChunkPtr’ has not been declared
In file included from ../include/siod.h:17,
                 from slib.cc:88:
../include/EST_String.h: In member function ‘void EST_String::make_updatable()’:
../include/EST_String.h:253: error: no matching function for call to ‘make_updatable(EST_ChunkPtr&, int)’
In file included from ../include/EST_string_aux.h:43,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TList.h: At global scope:
../include/EST_TList.h:226: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TList<T>&)’ declares a non-template function
../include/EST_TList.h:226: warning: (if this is not what you intended, make sure the function template has already been declared and add <> after the function name here) -Wno-non-template-friend disables this warning
In file included from ../include/EST_types.h:44,
                 from ../include/EST_string_aux.h:45,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TVector.h:312: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TVector<T>&)’ declares a non-template function
In file included from ../include/EST_types.h:46,
                 from ../include/EST_string_aux.h:45,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TKVL.h:61: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TKVI<K, V>&)’ declares a non-template function
../include/EST_TKVL.h:146: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TKVL<K, V>&)’ declares a non-template function
In file included from ../include/EST_TSimpleMatrix.h:46,
                 from ../include/EST_FMatrix.h:44,
                 from ../include/EST_types.h:47,
                 from ../include/EST_string_aux.h:45,
                 from ../include/siod.h:18,
                 from slib.cc:88:
../include/EST_TMatrix.h:310: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TMatrix<T>&)’ declares a non-template function
slib.cc: In function ‘void gc_mark_and_sweep()’:
slib.cc:1088: warning: dereferencing type-punned pointer will break strict-aliasing rules
gmake[1]: *** [slib.o] Error 1
gmake: *** [siod] Error 2
```

Festival
```
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/festival$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for ar... ar
checking whether byte ordering is bigendian... no
updating cache ./config.cache
creating ./config.status
creating config/config
pavallo@pavallo-laptop-ubuntu:~/Scrivania/temp/festival$ gmake
Check system type
Remake modincludes.inc
        NATIVE_AUDIO
                ok
        EDITLINE
                config/modules/editline.mak
        SIOD
                ok
        WAGON
                ok
        SCFG
                ok
        WFST
                ok
        OLS
                ok
        RXP
                src/modules/rxp/rxp.mak
        clunits
                unknown module in src/modules/clunits
        hts_engine
                unknown module in src/modules/hts_engine
        MultiSyn
                unknown module in src/modules/MultiSyn
        LINUX16_AUDIO
                config/modules/linux16_audio.mak
Making in directory ./src ...
Making in directory src/arch ...
Making in directory src/arch/festival ...
making dependencies -- festival.cc Phone.cc utterance.cc features.cc wave.cc wagon_interp.cc linreg.cc audspio.cc server.cc client.cc web.cc tcl.cc wfst.cc ngram.cc viterbi.cc ModuleDescription.cc
gcc -c  -fno-implicit-templates  -O3 -Wall           -I../../../src/include -I../../../../speech_tools/include      -DINSTANTIATE_TEMPLATES -DFTNAME='Festival Speech Synthesis System' -DFTLIBDIRC='/home/pavallo/Scrivania/temp/festival/lib ' -DFTVERSION='1.95' -DFTSTATE='beta'  -DFTDATE='July 2004' -DFTOSTYPE=\"unknown_DebianGNULinux\" festival.cc
In file included from /usr/include/c++/4.2/backward/iostream.h:31,
                 from ../../../../speech_tools/include/EST_iostream.h:52,
                 from ../../../../speech_tools/include/EST_String.h:50,
                 from ../../../../speech_tools/include/EST_Pathname.h:37,
                 from festival.cc:42:
/usr/include/c++/4.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
In file included from ../../../../speech_tools/include/EST_String.h:53,
                 from ../../../../speech_tools/include/EST_Pathname.h:37,
                 from festival.cc:42:
../../../../speech_tools/include/EST_Chunk.h:131: error: ‘EST_ChunkPtr’ does not name a type
../../../../speech_tools/include/EST_Chunk.h:132: error: ‘EST_ChunkPtr’ does not name a type
../../../../speech_tools/include/EST_Chunk.h:133: error: ‘EST_ChunkPtr’ does not name a type
../../../../speech_tools/include/EST_Chunk.h:135: error: ‘EST_ChunkPtr’ has not been declared
../../../../speech_tools/include/EST_Chunk.h:136: error: ‘EST_ChunkPtr’ has not been declared
../../../../speech_tools/include/EST_Chunk.h:138: error: ‘EST_ChunkPtr’ has not been declared
../../../../speech_tools/include/EST_Chunk.h:139: error: ‘EST_ChunkPtr’ has not been declared
In file included from ../../../../speech_tools/include/EST_Pathname.h:37,
                 from festival.cc:42:
../../../../speech_tools/include/EST_String.h: In member function ‘void EST_String::make_updatable()’:
../../../../speech_tools/include/EST_String.h:253: error: no matching function for call to ‘make_updatable(EST_ChunkPtr&, int)’
In file included from ../../../../speech_tools/include/EST_Pathname.h:38,
                 from festival.cc:42:
../../../../speech_tools/include/EST_TList.h: At global scope:
../../../../speech_tools/include/EST_TList.h:226: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TList<T>&)’ declares a non-template function
../../../../speech_tools/include/EST_TList.h:226: warning: (if this is not what you intended, make sure the function template has already been declared and add <> after the function name here) -Wno-non-template-friend disables this warning
In file included from ../../../../speech_tools/include/EST_types.h:44,
                 from ../../../../speech_tools/include/EST_string_aux.h:45,
                 from ../../../../speech_tools/include/EST.h:47,
                 from ../../../src/include/festival.h:44,
                 from festival.cc:44:
../../../../speech_tools/include/EST_TVector.h:312: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TVector<T>&)’ declares a non-template function
In file included from ../../../../speech_tools/include/EST_types.h:46,
                 from ../../../../speech_tools/include/EST_string_aux.h:45,
                 from ../../../../speech_tools/include/EST.h:47,
                 from ../../../src/include/festival.h:44,
                 from festival.cc:44:
../../../../speech_tools/include/EST_TKVL.h:61: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TKVI<K, V>&)’ declares a non-template function
../../../../speech_tools/include/EST_TKVL.h:146: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TKVL<K, V>&)’ declares a non-template function
In file included from ../../../../speech_tools/include/EST_TSimpleMatrix.h:46,
                 from ../../../../speech_tools/include/EST_FMatrix.h:44,
                 from ../../../../speech_tools/include/EST_types.h:47,
                 from ../../../../speech_tools/include/EST_string_aux.h:45,
                 from ../../../../speech_tools/include/EST.h:47,
                 from ../../../src/include/festival.h:44,
                 from festival.cc:44:
../../../../speech_tools/include/EST_TMatrix.h:310: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TMatrix<T>&)’ declares a non-template function
In file included from ../../../../speech_tools/include/ling_class/EST_Relation.h:48,
                 from ../../../../speech_tools/include/EST_wave_aux.h:52,
                 from ../../../../speech_tools/include/EST_speech_class.h:44,
                 from ../../../../speech_tools/include/EST.h:60,
                 from ../../../src/include/festival.h:44,
                 from festival.cc:44:
../../../../speech_tools/include/ling_class/EST_Item.h: In function ‘bool operator!=(const EST_Item&, const EST_Item&)’:
../../../../speech_tools/include/ling_class/EST_Item.h:398: error: ‘::same_item’ has not been declared
../../../../speech_tools/include/ling_class/EST_Item.h: In function ‘bool operator==(const EST_Item&, const EST_Item&)’:
../../../../speech_tools/include/ling_class/EST_Item.h:400: error: ‘::same_item’ has not been declared
In file included from ../../../../speech_tools/include/EST_TrackMap.h:41,
                 from ../../../../speech_tools/include/EST_Track.h:48,
                 from ../../../../speech_tools/include/EST_speech_class.h:45,
                 from ../../../../speech_tools/include/EST.h:60,
                 from ../../../src/include/festival.h:44,
                 from festival.cc:44:
../../../../speech_tools/include/EST_THandle.h: At global scope:
../../../../speech_tools/include/EST_THandle.h:140: warning: friend declaration ‘int operator==(const EST_THandle<BoxT, ObjectT>&, const EST_THandle<BoxT, ObjectT>&)’ declares a non-template function
../../../../speech_tools/include/EST_THandle.h:141: warning: friend declaration ‘int operator!=(const EST_THandle<BoxT, ObjectT>&, const EST_THandle<BoxT, ObjectT>&)’ declares a non-template function
../../../../speech_tools/include/EST_THandle.h:143: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_THandle<BoxT, ObjectT>&)’ declares a non-template function
gmake[3]: *** [festival.o] Error 1
gmake[2]: *** [festival] Error 2
gmake[1]: *** [arch] Error 2
gmake: *** [src] Error 2

```

Thank you

---

### Post by basemhaa on 2010-09-21
I have the same problem

---

### Post by MadCow108 on 2010-09-22
the source code needs fixing to be more standard compliant.

ask the developers to do so or do it yourself.

from a brief look some forward declarations are missing, include statements need fixing (dropping .h) and std:: namespace needs to be added in some places


always look at the first **error** message and fix that first.

---

