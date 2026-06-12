---
title: "How can i handle &quot;undefined reference to&quot; error"
date: 2011-06-21
forum: Packaging and Compiling Programs
---

### Post by andereasmehdi on 2011-06-21
hi all,
I am new in linux and i use cygwin gcc for compiling a code.
but i crush into this error:
          undefined reference to `Vocab::Vocab(unsigned int, unsigned int)'
          undefined reference to `File::File(char const*, char const*, int)'
          .....

how can i handle it?

thanks

---

### Post by Beacon11 on 2011-06-21
Looks like you're not linking correctly. Is Vocab and File defined by you, or are they provided by a third-party library? How are you compiling this?

---

### Post by andereasmehdi on 2011-06-22
well i have header file by that name in include/srilm folder. and it is included by this command in code. 
#include "File.h"
#include "Vocab.h"

Here is my make file if you are interested: 

#
#  Makefile 
# 

PROGS=  ngram-count trainmodel lsalm
CXX = g++
#for compiling C files
CC = cc


#change the following variable: tcl library
TCLLIB=/usr/share/tcllib1.13


MACHINE_TYPE=i686
INCLUDE_DIR=../include
LIB_DIR=../lib
SRC_DIR=./
#ALL_INCLUDES = -I./ -I$(INCLUDE_DIR) -I$(INCLUDE_DIR)/srilm
ALL_INCLUDES = -I./ -I$(INCLUDE_DIR)
ALL_LIBRARIES =  -lm -L$(LIB_DIR)/$(MACHINE_TYPE) -llattice -lflm -loolm -ldstruct -lmisc

CXXFLAGS =  -O3 -Wno-deprecated


###########################################################################

OBJ_LSALM=lsalm.o LsaNgram.o LsaLM.o LsaFile.o 
OBJ_MIPLSA = trainmodel.o miplsa.o tools.o writeModel.o option.o las2.o LsaFile.o
OBJ_READMATRIX=ngram-count.o

all : $(PROGS)

.PHONY : all

lsalm: $(OBJ_LSALM)
      $(CXX)  -o $@  $(OBJ_LSALM)  $(ALL_LIBRARIES)  $(CXXFLAGS) 
      
ngram-count: $(OBJ_READMATRIX)
      $(CXX)  -o $@  $(OBJ_READMATRIX)  $(ALL_LIBRARIES)  $(CXXFLAGS) 
      
trainmodel: $(OBJ_MIPLSA)
      $(CXX)  -o $@  $(OBJ_MIPLSA)  $(ALL_LIBRARIES)  
     
    
$(SRC_DIR)%.o: $(SRC_DIR)%.cpp
    cd $(SRC_DIR) && $(CXX) -c  $(CXXFLAGS)  $(ALL_INCLUDES)  $*.cpp
    
$(SRC_DIR)%.o: $(SRC_DIR)%.cc
    cd $(SRC_DIR) && $(CXX) -c  $(CXXFLAGS)  $(ALL_INCLUDES)  $*.cc

$(SRC_DIR)%.o: $(SRC_DIR)%.c
    cd $(SRC_DIR) && $(CC) -c   $(ALL_INCLUDES)  $*.c
        
#######################################################################

clean:
    rm -f *.o  $(PROGS)
--------------------------------------------------------------

Compiling this program is very important to me I dont know how to work with linux codes. could you please help me to compile these codes. :(

Thanks alot

<email removed>

---

### Post by lisati on 2011-06-22
Posting your email address here isn't a smart thing to do. It won't be long before the spammers find you.

---

### Post by Beacon11 on 2011-06-22
Lisati is right-- I'd edit that post if I were you.

Okay, do you have a File.cpp and Vocab.cpp? Could you please try to make this and paste the entire result in here?

---

### Post by andereasmehdi on 2011-06-22
In fact they are just header files in include/srilm folder and they are not .cpp files.

you know I download the code from a scientific site that it is free license. 

Here is the link:

  [[COLOR=#1F497D][FONT=&quot]http://userver.ftw.at/~pucher/semanlm/semanlm0.91.zip[/FONT][/COLOR]]("http://userver.ftw.at/%7Epucher/semanlm/semanlm0.91.zip")

if it is useful.

Thanks for your attention.

---

### Post by Beacon11 on 2011-06-22
Okay, I would still like to see what happens when you make.

First dependency I see is the TCL library-- do you have it installed and is it actually located at /usr/share/tcllib1.13?

---

### Post by andereasmehdi on 2011-06-22
well I download tcllib library from [http://sourceforge.net/projects/tcllib/files/tcllib/1.13/](http://sourceforge.net/projects/tcllib/files/tcllib/1.13/)
and i install it with this command tclsh installer.tcl 

the installer copies to these directories:
packages ----> C:/cygwin/usr/share/tcllib1.13
applications---->C:/cygwin/usr/bin

I think the compiler doesn't reach to that stage to use tcllib and before that compiler stops because i omit the TCLLIB=/usr/share/tcllib1.13 line and still it has those errors.

I write this command to see the errors "make > make.txt 2>&1" and it prints the process to make.txt and the errors are the same.

here is the errors that i found in make.txt :[INDENT]g++  -o ngram-count  ngram-count.o  -lm -L../lib/i686 -llattice -lflm -loolm -ldstruct -lmisc  -O3 -Wno-deprecated 
ngram-count.o:ngram-count.cc: (.text+0xa9): undefined reference to `_Opt_Parse'
ngram-count.o:ngram-count.cc: (.text+0x11f): undefined reference to `Vocab::Vocab(unsigned int, unsigned int)'
ngram-count.o:ngram-count.cc: (.text+0x204): undefined reference to `SubVocab::SubVocab(Vocab&)'
ngram-count.o:ngram-count.cc: (.text+0x245): undefined reference to `StopNgramStats::StopNgramStats(Vocab&, SubVocab&, unsigned int)'
ngram-count.o:ngram-count.cc: (.text+0x2b5): undefined reference to `File::File(char const*, char const*, int)'
ngram-count.o:ngram-count.cc: (.text+0x2f7): undefined reference to `File::~File()'
ngram-count.o:ngram-count.cc: (.text+0x31f): undefined reference to `File::File(char const*, char const*, int)'
ngram-count.o:ngram-count.cc: (.text+0x339): undefined reference to `File::~File()'
ngram-count.o:ngram-count.cc: (.text+0x36e): undefined reference to `SubVocab::SubVocab(Vocab&)'
ngram-count.o:ngram-count.cc: (.text+0x38f): undefined reference to `File::File(char const*, char const*, int)'
ngram-count.o:ngram-count.cc: (.text+0x39b): undefined reference to `Vocab::read(File&)'
ngram-count.o:ngram-count.cc: (.text+0x3c7): undefined reference to `File::~File()'
ngram-count.o:ngram-count.cc: (.text+0x3d1): undefined reference to `vtable for Vocab'
ngram-count.o:ngram-count.cc: (.text+0x3d9): undefined reference to `LHash<unsigned int, unsigned int>::~LHash()'
ngram-count.o:ngram-count.cc: (.text+0x3e4): undefined reference to `LHash<unsigned int, unsigned int>::~LHash()'
ngram-count.o:ngram-count.cc: (.text+0x3fe): undefined reference to `LHash<char const*, unsigned int>::~LHash()'

.
.
.
and so on.
[/INDENT]thanks

---

### Post by andereasmehdi on 2011-06-25
I changed Opt_Parse(argc, argv, options, Opt_Number(options), 0); to  std::Opt_Parse(argc, argv, options, Opt_Number(options), 0); and it  works!!!
I skip those errors. and these are new one [IMG]http://im.cprogramming.com/images/smilies/confused.png[/IMG]

g++ -g -O3 -Wno-deprecated   -c -o ngram-count.o ngram-count.cc
In file included from ngram-count.cc:17:
option.h:25:24: error: cfuncproto.h: No such file or directory
ngram-count.cc:18:18: error: File.h: No such file or directory
ngram-count.cc:19:19: error: Vocab.h: No such file or directory
ngram-count.cc:20:22: error: SubVocab.h: No such file or directory
ngram-count.cc:21:19: error: Ngram.h: No such file or directory
ngram-count.cc:22:22: error: VarNgram.h: No such file or directory
ngram-count.cc:23:25: error: TaggedNgram.h: No such file or directory
ngram-count.cc:24:23: error: SkipNgram.h: No such file or directory
ngram-count.cc:25:23: error: StopNgram.h: No such file or directory
ngram-count.cc:26:24: error: NgramStats.h: No such file or directory
ngram-count.cc:27:30: error: TaggedNgramStats.h: No such file or directory


i checked the ALL_INCLUDES = -I./ -I$(INCLUDE_DIR) -I$(INCLUDE_DIR)/srilm and it is were my headers are there.

---

