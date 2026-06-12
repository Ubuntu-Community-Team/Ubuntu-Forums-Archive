---
title: "No Rules to make  lsalm.o"
date: 2011-08-13
forum: Packaging and Compiling Programs
---

### Post by andereasmehdi on 2011-08-13
hi
I downloaded an open source program. And I want to make it. at the end I must have three compiled files. I make the make file and it creates two of them but for third one it gives me this error: "No rules to make lsalm.o". the output files must be *[COLOR=Navy]ngram-count[/COLOR] [COLOR=Purple]trainmodel[/COLOR]* [COLOR=Red]*lsalm*[/COLOR]. but I just have *[COLOR=Navy]ngram-count[/COLOR] [COLOR=Purple]trainmodel[/COLOR]* !!!

here is my Makefile:
```

MACHINE_TYPE=i686
INCLUDE_DIR=../include
LIB_DIR=../lib
SRC_DIR=./
ALL_INCLUDES = -I./ -I$(INCLUDE_DIR) -I$(INCLUDE_DIR)/srilm
ALL_LIBRARIES =  -lm -L$(LIB_DIR)/$(MACHINE_TYPE) -llattice -lflm -loolm -ldstruct -lmisc

CXXFLAGS =  -O3 -Wno-deprecated


###########################################################################

OBJ_LSALM= lsalm.o LsaNgram.o LsaLM.o LsaFile.o 
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

```Can anybody help me to make it completely?

Thanks

---

