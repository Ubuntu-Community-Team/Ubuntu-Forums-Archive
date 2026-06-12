---
title: "segfault... why why why?"
date: 2007-06-20
forum: Programming Talk
---

### Post by hardyn on 2007-06-20
i have this defined globally...

/* Each line is a list of WordNodes. */
typedef struct WTWordNode {
	char* word;
	struct WTWordNode* nextWordPtr;
} WTWordNode;
typedef WTWordNode* WTWordNodePtr;

/* The LineStorage module stores a list of LineNodes */
typedef struct WTLineNode {
	WTWordNodePtr headWordPtr;
	WTWordNodePtr tailWordPtr;
	int wordCount;
} WTLineNode;
typedef WTLineNode* WTLineNodePtr;

then when trying to do this...

WTBuffer->wordCount++;
or
WTBuffer->wordCount = 0;

from inside a function, im segfaulting... its looks legal to me... any ideas?

thanks in advance.

---

### Post by Mr. C. on 2007-06-20
Since we can't see how you allocated the space for WTBuffer, we can only guess.

You've likely declared and defined:

WTLineNodePtr WTBuffer;

This gives you a single, 4-byte pointer.

What you want is:

WTLineNode MyBuf;
WTLineNodePtr WTBuffer = &MyBuf;

This gives you the entire struct, and WTBuffer is then a pointer to reserved space.

MrC

---

### Post by hardyn on 2007-06-20
. thanks ill try it.

---

### Post by Mr. C. on 2007-06-20
Incorrect code sometimes works without apparent flaw.

I only guessed what was a likely problem; it could be something else.

MrC

---

