---
title: "Error: ld returned 1 exit status"
date: 2015-12-27
forum: New to Ubuntu
---

### Post by spr4 on 2015-12-27
hi,
i typed make command to install kaldi program on ubuntu but i got this error:

```

make -C latbin 
make[1]: Entering directory `/usr/local/bin/Kaldi/kaldi-svn-archive-master/src/latbin'
g++ -rdynamic -Wl,-rpath=/usr/local/bin/Kaldi/kaldi-svn-archive-master/tools/openfst/lib  lattice-reverse.o ../lat/kaldi-lat.a ../lm/kaldi-lm.a ../hmm/kaldi-hmm.a ../tree/kaldi-tree.a ../util/kaldi-util.a ../matrix/kaldi-matrix.a ../thread/kaldi-thread.a ../base/kaldi-base.a   -L/usr/local/bin/Kaldi/kaldi-svn-archive-master/tools/openfst/lib -lfst /usr/lib/libatlas.so.3 /usr/lib/libf77blas.so.3 /usr/lib/libcblas.so.3 /usr/lib/liblapack_atlas.so.3 -lm -lpthread -ldl -o lattice-reverse
lattice-reverse.o: In function `main':
/home/tjr/kaldi-trunk/src/latbin/lattice-reverse.cc:44: undefined reference to `kaldi::ParseOptions::NumArgs()'
/home/tjr/kaldi-trunk/src/latbin/lattice-reverse.cc:49: undefined reference to `kaldi::ParseOptions::GetArg(int)'
/home/tjr/kaldi-trunk/src/latbin/lattice-reverse.cc:50: undefined reference to `kaldi::ParseOptions::GetArg(int)'
collect2: error: ld returned 1 exit status
make[1]: *** [lattice-reverse] Error 1

```

this is the lattice-reverse.cc code:

```
#include "base/kaldi-common.h"
#include "util/common-utils.h"
#include "fstext/fstext-lib.h"
#include "lat/kaldi-lattice.h"
//#include "lat/lattice-functions.h"

int main(int argc, char *argv[]) {
  try {
    using namespace kaldi;
    typedef kaldi::int32 int32;
    typedef kaldi::int64 int64;
    using fst::VectorFst;
    using fst::StdArc;

    const char *usage =
        "Time reversal of compact lattice and write out as lattice\n"
        "Usage: lattice-reverse [options] lattice-rspecifier lattice-wspecifier\n"
        " e.g.: lattice-reverse ark:1.lats ark:1.reverse.lats\n";
      
    ParseOptions po(usage);
    
    po.Read(argc, argv);

    if (po.NumArgs() != 2) {
      po.PrintUsage();
      exit(1);
    }

    std::string lats_rspecifier = po.GetArg(1),
        lats_wspecifier = po.GetArg(2);

    SequentialCompactLatticeReader clat_reader(lats_rspecifier);
    
    // Write as compact lattice.
    CompactLatticeWriter compact_lat_writer(lats_wspecifier); 

    int32 n_done = 0;

    for (; !clat_reader.Done(); clat_reader.Next()) {
      std::string key = clat_reader.Key();
      CompactLattice clat = clat_reader.Value();
      clat_reader.FreeCurrent();
      
      Lattice lat;
      ConvertLattice(clat, &lat);
      Lattice reverse_lat;
      fst::Reverse(lat, &reverse_lat);
      RemoveEpsLocal(&reverse_lat);
      CompactLattice reverse_clat;
      ConvertLattice(reverse_lat, &reverse_clat);
      RemoveEpsLocal(&reverse_clat);
    
      compact_lat_writer.Write(key, reverse_clat);
      n_done++;
    }
    KALDI_LOG << "Done converting " << n_done << " to best path";
    return (n_done != 0 ? 0 : 1);
  } catch(const std::exception &e) {
    std::cerr << e.what();
    return -1;
  }
}

```

please help me to solve this error.
thanks

---

### Post by steeldriver on 2015-12-27
Hello and welcome to the forums

What build instructions are you following, exactly? Did you build the 'tools' before trying to build the 'src'?

The method described here (from a git clone) seems to complete successfully on my 14.04 box:

[https://github.com/kaldi-asr/kaldi](https://github.com/kaldi-asr/kaldi)

---

### Post by spr4 on 2015-12-28
yes, i build the 'tools' before trying to build the 'src', i run these commands and all completed successfully except 'make'
./configure
make depend
make

---

