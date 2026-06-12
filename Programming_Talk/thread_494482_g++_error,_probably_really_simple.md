---
title: "g++ error, probably really simple"
date: 2007-07-06
forum: Programming Talk
---

### Post by rocksTONIC52 on 2007-07-06
Hello,

I have recently abandoned Visual Studio in exchange for vim/g++.  Everything's going fine, except for the fact that I don't know what to check when the compiler gives me those "silly errors" (you know the ones!)  At least in VS I generally knew where to go from experience.

So I'm asking for a push :P  I'm really expecting this to be a makefile error.
```

g++ -c CMessageSystem.cpp
CMessageSystem.cpp:9: error: variable or field &#8216;sendMessage&#8217; declared void
CMessageSystem.cpp:9: error: &#8216;int CMessageSystem::sendMessage&#8217; is not a static member of &#8216;class CMessageSystem&#8217;
CMessageSystem.cpp:9: error: &#8216;tMessage&#8217; was not declared in this scope
CMessageSystem.cpp:10: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
CMessageSystem.cpp:13: error: no &#8216;void CMessageSystem::dispatchMessages()&#8217; member function declared in class &#8216;CMessageSystem&#8217;
make: *** [CMessageSystem.o] Error 1
```


```
/*@@
 * CMessageSystem.h
 * Nicholas Thompson
 * Created: Fri Jul 6, 12:30 AM
 * Purpose: Define the CMessageSystem class
 * @@*/

#ifndef __CMESSAGESYSTEM_H__
#define __CMESSAGESYSTEM_H__

#include "allMessages.h"
#include "tMessage.h"

class CMessageSystem
{
	private:
	
	public:
	void sendMessage(tMessage msg);
	void dispatchMessages();
};

#endif
```

(where allMessages.h contains a #define, and tMessage contains a properly terminated tMessage structure)

```
/*@@
 * CMessageSystem.cpp
 * Nicholas Thompson
 * Created: Fri Jul 6, 2:26 AM
 * Purpose: implement methods described in CMessageSystem.h
 * @@*/
#include "CMessageSystem.h"

void CMessageSystem::sendMessage(tMessage msg)
{
}

void CMessageSystem::dispatchMessages()
{
}
```

```
#	Makefile - Message System
#	Nicholas Thompson
#	Created: Fri Jul 6, 12:23AM
OBJ = CMessageSystem.o main.o

messageSystem: $(OBJ)
	g++ -o messageSystem $(OBJ)

main.o: main.cpp CMessageSystem.h
	g++ -c main.cpp

CMessageSystem.o: CMessageSystem.h CMessageSystem.cpp allMessages.h tMessage.h
	g++ -c CMessageSystem.cpp

clean:
	rm -f *.o
```

I'd really appreciate any help.  I'll bake you some e-cookies or something.

edit: thanks for the formatting advice, scxtt :)

---

### Post by scxtt on 2007-07-06
change the "quote" to "code" ...

---

### Post by Modred on 2007-07-07
If I attempt to compile the CMessageSystem.cpp with just what you provided, I get the errors you experienced plus the expected "header not found" for the files I don't have.  If  I create a tMessage.h with the following contents:

```

#ifndef TMESSAGE_H
#define TMESSAGE_H

typedef struct {
    int value;
} tMessage;

#endif

```

And then the only error I get is the missing allMessages.h.  Are you sure your tMessage.h is correct?

Also, if you haven't yet, check out the make command in Vim.

---

### Post by rocksTONIC52 on 2007-07-07
Thanks for your reply.  I'll try getting rid of tMessage.h in a minute, but I dont really see anything wrong with it.

```

/*@@
 * tMessage.h
 * Nicholas Thompson
 * Created: Fri Jul 6, 2:17AM
 * Purpose: Define a message
 * @@*/

#ifndef __TMESSAGE_H__
#define __TMESSAGE_H__

struct tMessage
{
	int msg;
	void *params;
};

#endif

```

edit:
Tried removing all references to tMessage from the program.  I'm still getting these two errors.

```

g++ -c CMessageSystem.cpp
CMessageSystem.cpp:9: error: no &#8216;void CMessageSystem::sendMessage()&#8217; member function declared in class &#8216;CMessageSystem&#8217;
CMessageSystem.cpp:13: error: no &#8216;void CMessageSystem::dispatchMessages()&#8217; member function declared in class &#8216;CMessageSystem&#8217;
make: *** [CMessageSystem.o] Error 1

```

---

### Post by Modred on 2007-07-07
CMessageSystem.h
```

/*@@
 * CMessageSystem.h
 * Nicholas Thompson
 * Created: Fri Jul 6, 12:30 AM
 * Purpose: Define the CMessageSystem class
 * @@*/

#ifndef __CMESSAGESYSTEM_H__
#define __CMESSAGESYSTEM_H__


class CMessageSystem
{
	private:
	
	public:
	void sendMessage();
	void dispatchMessages();
};

#endif

```

CMessageSystem.cpp
```

/*@@
 * CMessageSystem.cpp
 * Nicholas Thompson
 * Created: Fri Jul 6, 2:26 AM
 * Purpose: implement methods described in CMessageSystem.h
 * @@*/
#include "CMessageSystem.h"

void CMessageSystem::sendMessage()
{
}

void CMessageSystem::dispatchMessages()
{
}

```

This compiles with no errors for me.  Do you have any precompiled headers?  Try an:
```
ls *.gch
```
This would explain your incompatible return type problem.  Try removing any .gch files.  Although that wouldn't explain why I was getting the same error as you originally got.  Hmm...

---

### Post by rocksTONIC52 on 2007-07-07
well i'll be dipped.  seems I accidentally compiled CMessageSystem.h while trying to figure out the whole makefile dealy-o.  Compiles with no problems, and I'm adding *.gch to my clean rule.  Thanks a million!

---

### Post by Modred on 2007-07-07
To be honest, I wasn't even aware of precompiled headers until I accidentally compiled CMessageSystem.h from within Vim because I was in the wrong buffer.  Serendipity strikes again.

---

