---
title: "Make error and Binutils bug"
date: 2014-11-04
forum: Packaging and Compiling Programs
---

### Post by sainath-nambiar on 2014-11-04
Hi all,
        I was trying to install an Ebmbedded SSL library called cyaSSL and when I type "make command" to compile the source after configuring with options, I get an binutils error , the following is the error descryption.

[B]/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.24 internal error, aborting at ../../bfd/merge.c line 873 in _bfd_merged_section_offset

/usr/bin/ld: Please report this bug.

collect2: error: ld returned 1 exit status
make[1]: *** [examples/client/client] Error 1
make[1]: *** Waiting for unfinished jobs....
/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.24 internal error, aborting at ../../bfd/merge.c line 873 in _bfd_merged_section_offset

/usr/bin/ld: Please report this bug.

collect2: error: ld returned 1 exit status
/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.24 internal error, aborting at ../../bfd/merge.c line 873 in _bfd_merged_section_offset

/usr/bin/ld: Please report this bug.

collect2: error: ld returned 1 exit status
make[1]: *** [examples/server/server] Error 1
make[1]: *** [ctaocrypt/test/testctaocrypt] Error 1
/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.24 internal error, aborting at ../../bfd/merge.c line 873 in _bfd_merged_section_offset

/usr/bin/ld: Please report this bug.

collect2: error: ld returned 1 exit status
make[1]: *** [examples/echoclient/echoclient] Error 1
/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.24 internal error, aborting at ../../bfd/merge.c line 873 in _bfd_merged_section_offset

/usr/bin/ld: Please report this bug.

collect2: error: ld returned 1 exit status
make[1]: *** [ctaocrypt/benchmark/benchmark] Error 1
make[1]: Leaving directory `/home/dt/Documents/ssl/cyassl/cyassl-3.2.0'
make: *** [all] Error 2
[/B]
As the linker itself says its a bug I thought it would be worthwhile to post it here and get some inputs.
My best bet after googling is that automake-generated makefiles behave badly
when invoked with multiple targets and -j. Awaiting your suggestions.

Regards
Sainath

---

