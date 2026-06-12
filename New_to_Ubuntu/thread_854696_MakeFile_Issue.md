---
title: "MakeFile Issue"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by HABalloonGirl on 2008-07-09
Hi all,

I was wondering if anyone could help me with a makefile problem I'm having; I don't write many.  My make file looks something like
CC=g++
C= -c
i2ctry2: i2ctry2.cpp i2capi.c i2c.c i2cioapi.c Crc8.c DumpMem.c Log.c i2cioapi.h i2c.h i2cdev.h i2cio.h i2capi.h Log.h Crc8.h DumpMem.h Config.h
	${CC} $(C) $(CFLAGS) $(LDFLAGS) -o Log.o Log.c
	$(CC) $(C) $(CFLAGS) $(LDFLAGS) -o Crc8.o Crc8.c
	$(CC) $(C) $(CFLAGS) $(LDFLAGS) -o DumpMem DumpMem.c
	$(CC) $(C) $(CFLAGS) $(LDFLAGS) -o i2cioapi.o i2cioapi.c
	$(CC) $(C) $(CFLAGS) $(LDFLAGS) -o i2c.o i2c.c
	$(CC) $(C) $(CFLAGS) $(LDFLAGS) -o i2capi.o i2capi.c
	$(CC) $(C) $(CFLAGS) $(LDFLAGS) -o i2ctry2.o i2ctry2.cpp

Where I want to compile but not link my pieces of code.  I'm going to link them in a .bb file to avoid another error I'm having with bitbake.  Bu when I do make i2ctry2 I get make: *** No rule to make target `i2ctry2'.  Stop.
Any suggestions?

---

### Post by jamesapnic on 2008-07-09
hmm, it looks ok, presuming you have tabs in the right places

I tested it with dummy files

> 
$ make i2ctry2
g++ -c   -o Log.o Log.c
g++ -c   -o Crc8.o Crc8.c
g++ -c   -o DumpMem DumpMem.c
g++ -c   -o i2cioapi.o i2cioapi.c
g++ -c   -o i2c.o i2c.c
g++ -c   -o i2capi.o i2capi.c
g++ -c   -o i2ctry2.o i2ctry2.cpp


I guess its due to the paste, but each line under i2ctry2: should be tabbed in.

---

### Post by Sydius on 2008-07-09
It's hard to tell from your example, but make sure there are tabs in front of all the lines after "i2ctry2: ..." -- tabs, not spaces.

---

### Post by HABalloonGirl on 2008-07-09
Yeah, I've got the tabs.  Copy paste thing but they are there.

---

### Post by Sydius on 2008-07-09
I notice the first $(CC) is ${CC} -- could that be it?

---

### Post by HABalloonGirl on 2008-07-09
just changed it to see and no. still gives me the same error.  I also noticed I left out the .o on one object in what I posted and fixing that doesn't help either.

---

### Post by Sydius on 2008-07-09
I took the dive and learned how to contort the autotools to generate my makefiles, so I've been spoiled by them... but I don't see anything wrong with the snippet you posted.  Can you post your entire makefile?

---

### Post by HABalloonGirl on 2008-07-09
ah, that's the entire thing.  Am I missing something big?  Unless I add them together with 

${CC} ${CFLAGS} i2capi.o Log.o Crc8.o DumpMem.o i2cioapi.o i2c.o i2ctry2.o

that's it.

---

### Post by Sydius on 2008-07-09
I don't know if it matters, but try replacing all the () with {} to see if that fixes it... your CFLAGS and LDFLAGS seems to be undefined?

---

### Post by HABalloonGirl on 2008-07-09
changed the brackets, same error.  didn't realize those 2 were undefined... if I take them out I get the same error.  If I make them anything else, I also get the same error.  sigh.

I have to leave for a while but thanks for the help Sidius.

---

### Post by Sydius on 2008-07-09
Oh, one more novel thought: What is your makefile called? Make will give that error if it cannot find the makefile (I just tried "make blah" in an empty directory, and it gave me the same error).  If I remember right, it has to be named (exactly) "Makefile" and be in the same directory as the command is executed from.  Verify that it is seeing the makefile.  Also, you shouldn't need to specify what to make--by default, it runs the first one, which should be the one you want (so just typing "make" will work AND tell you if it couldn't find a makefile).

---

