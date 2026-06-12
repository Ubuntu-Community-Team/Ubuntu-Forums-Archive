---
title: "Basic Stamp Editing"
date: 2008-02-05
forum: Packaging and Compiling Programs
---

### Post by Exefurious on 2008-02-05
Good Morning,

I am having trouble getting the Basic Stamp tools for Linux (Ubuntu 7.1) to run.  I seem to be hung up on the installation / getting started.

I downloaded the bstamp-2006.05.31.tar.gz package from source forge.  After extracting it to the desktop, there is a folder called bstamp within which are the following:

A folder called pbasic_examples
bstamp_run.cpp
bstamp_tokenize.cpp
CHANGES.txt
COPYING.txt
error_handling.cpp
GPL.txt
Makefile
PBASIC_Tokenizer_Software_Distribution_License.pdf
PBASIC_Tokenizer_Software_Distribution_License.doc
README.txt
TODO.txt
tokenizer.h
tokenizer.so

Inside the examples folder mentioned above is a makefile and two stamp programs:

hello.bs2
Makefile
touch.bs2


Now, when I follow directions on the internet (at various locations) and try to make the file, I get an error 127, and that is as far as I get...

Could someone help me, or direct me to a helpful tutorial / resource?  

I would like to be able to program the stamp within Linux without using WINE, which didn't work anyway when I tried it.

---

### Post by geraldm on 2008-02-05
The package is apparently using two licenses, GNU for the volunteered portion, and PBASIC license.  PBASIC Tokenizer Library software is used with hardware that is sold by Parallax.  The license to redistribute  any programs written is very restrictive, including requiring a driver's license, and written agreement in the possession of Parallax, and subject to revokations including those mentioned within that package.
The source for the library is not provided, and the library file is stripped.  It is only useful with their hardware.  

You can use these commands to get by the problems you cited.  You can use this as a script, or just type in the commands.
```

#!/bin/sh
# linux_setup.sh
# This script is to be executed withiin the source top directory of bstamp

# assure clean directory; then make
make clean
make

# create the files hello.tok touch.tok; put them in directory pbasic_examples/
./bstamp_tokenize pbasic_examples/hello.bs2 pbasic_examples/hello.tok
./bstamp_tokenize pbasic_examples/touch.bs2 pbasic_examples/touch.tok

# Here the serial device to be used must be linked to /dev/bstamp
# Some help is in the file README.txt.  

# Continue with instructions within README.txt 

```

Gerald

---

