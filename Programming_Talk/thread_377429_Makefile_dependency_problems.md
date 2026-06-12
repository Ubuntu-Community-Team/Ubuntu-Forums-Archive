---
title: "Makefile dependency problems"
date: 2007-03-06
forum: Programming Talk
---

### Post by PerH on 2007-03-06
Hi! I'm having some dependency problems with the following makefile:

```

BIN               := myapp	# Output application name
BUILD           := build	# Build directory
SOURCES      := src		# Source directory

# List of c sourcefile with source directory path
CFILES          :=	$(foreach dir,$(SOURCES),$(wildcard $(dir)/*.c))
# List of c++ sourcefile with source directory path
CPPFILES      :=	$(foreach dir,$(SOURCES),$(wildcard $(dir)/*.cpp))
# List of c and c++ object files with source directory prefix INVALID!
OFILES          :=	$(CPPFILES:.cpp=.o) $(CFILES:.c=.o)
# List of c and c++ object files with the build directory as prefix
OUTPUT         :=	$(foreach file, $(OFILES), ${BUILD}/$(notdir $(file)))

CCFLAGS  = -g -Wall -std=c99
CXXFLAGS = -g -Wall
INCLUDES= 
LIBS = 	

# Create build directory
$(BUILD):
	@[ -d $@ ] || mkdir -p $@

all: ${BUILD} ${BIN} 

# Generate application bin file.
# Currently depends on the invalid ${OFILES} list!!!
${BIN}: $(OFILES)
	$(CXX) $(OUTPUT) -o $(BIN) ${INCLUDES} $(LIBS)

.cpp.o:
	$(CXX) -c $< -o ${BUILD}/$(notdir $@) $(CXXFLAGS) ${INCLUDES} 
	
.c.o:
	$(CC)  -c $< -o ${BUILD}/$(notdir $@) $(CCFLAGS) ${INCLUDES} 

clean:
	@echo clean ...
	@rm -fr $(BUILD) $(BIN)

```

The following makefile compiles my source code, but it compiles *all* the files even if I only made one changes.
This has probably too do with ${BIN} depending on $(OFILES) instead of $(OUTPUT).
If I make ${BIN} instead depend on $(OUTPUT) then I get the following error:
```

make all 
make: *** No rule to make target `build/AuthDiag.o', needed by `myapp'.  Stop.

```

How do I update my suffix rules to work with subdirectories?

---

### Post by Mr. C. on 2007-03-06
The FIRST rule wins.

Your $(BUILD) rule is first.  It depends on nothing, so will run each and every time.

When you think "make", think "what am I trying to update", and that should be on the RHS.

In general, these overly complex, recursive top level makes are difficult at best.

It is better to provide sub-level makes for each, that are simpler, and far easier to debug, not just for you, but the next person who has to solve maintain this thing.

Your make is telling you that there is no rule to create a build/AuthDiag.o: you will need to provide a generic rule that indicates how to build these.

MrC

---

### Post by PerH on 2007-03-06
> **Mr. C. said:**
> The FIRST rule wins.

Your make is telling you that there is no rule to create a build/AuthDiag.o: you will need to provide a generic rule that indicates how to build these.

MrC

Is it the suffix rule I'll have to update to do this?

---

### Post by Mr. C. on 2007-03-06
My comments were basically in the order I was seeing problems.

First, your all rule, or your primary target should be the first rule (not $(BUILD) as you have now).  You want to be able to just say "make" and your product is build and brought up to date.  Don't force someone to enter "make all".  And I don't think your goal is to simply create a subdirectory!

Now, your all rule: make will do the $(BUILD)  just fine each time, but then it will try to bring $(BIN) up to date.  $(BIN) depends on bring myapp up to date, which then wants to bring OFILES (i'm tired of using ( ) and $) up to date.

OFILES is : src/*.o, which is a long list of :

src/blah.o

I don't think this is what you want.  Don't you want build/blah.o files to be built and used to bring your BIN up to date?

How does make know you really  want src/blah.o to actually be build/blah.o ?

Something else to consider: lookup make's VPATH.  This will greatly simplify your makefiles.

If your goal is to have a common set of definitions, create a single top level global defs, inclusion makefile, and the makefiles in each subdirectory.  Use the top-level simply as a driver of all the rest.

As I said earlier, debugging makefile production and target rules in a recursive environment can be a huge pain.  I built an entire build system around the unix kernel and utililties; simple is better.

MrC

[ Edit:  I'm not sure what happened to one of your posts - I received an email, but the context is no longer in this thread.  Perhaps you deleted, as my follow-up may have answer your questions? ]

---

### Post by PerH on 2007-03-06
Thank you for your help.

I'm starting to understand why these recursive makefiles can be a bit messy :)

I've looked into using VPATH and come across this site [http://make.paulandlesley.org/vpath.html]("http://make.paulandlesley.org/vpath.html")
 which gave an example at the end that got my makefile to work.

My new rules look like this and seems to work pretty well
```

${BIN}: $(addprefix $(BUILD)/,$(OUTPUT))
	$(CXX) $^ -o $(BIN) ${INCLUDES} $(LIBS)

${BUILD}/%.o : ${SOURCES}/%.cpp
	$(CXX) -c $< -o $@ $(CXXFLAGS) ${INCLUDES}

${BUILD}/%.o : ${SOURCES}/%.c
	$(CC) -c $< -o $@ $(CCFLAGS) ${INCLUDES}

```

Thanks again

//Per

---

### Post by Mr. C. on 2007-03-06
You're welcome.

At one point in what seems to have been a lifetime ago, I used to have mastery over make, and had developed some very complex build systems.  While it was very easy for me to add a new module, or ruleset, others were flummoxed.  This was a good lesson not to try to over-engineer a problem by pushing a given to beyond its limits.

Enjoy!
MrC

---

