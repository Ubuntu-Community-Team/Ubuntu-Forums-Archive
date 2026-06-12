---
title: "Who foo?"
date: 2006-03-06
forum: Programming Talk
---

### Post by bountonw on 2006-03-06
I am a third of the way through my intro to C book.  Fun.  Anyway, looking through different source codes here and there and finding it still mostly greek, but beginning to understand some.

I keep coming accross this very Chinese looking word, "foo". I thought that it might be an abreviation for  Egg Foo Young, but didn't quite fit the context.  Looking on several online computer dictionaries didn't enlighten me.

What's cooking?

---

### Post by soce_32 on 2006-03-06
Foo is the ultimate generic variable.  It is used to show that just about any arbitrary word, command, or variable could be substituted based on your specific situation.

If you are trying to communicate the use of a |, you could say `cat foo | sort`, and foo could be any file floating around on your hard drive.

Or in a programming sense, you could say `foreach (foo); do bar; done` where foo is  any old test, and bar is just about any action you could dream up.  The important thing you are trying to communicate is the foreach syntax, not so much the test (foo) or the action (bar).

Check out wikipedia's entry for foo if you really want some dense explanation.

---

### Post by bountonw on 2006-03-06
Thank you.  I understand now.  

[http://en.wikipedia.org/wiki/Foo](http://en.wikipedia.org/wiki/Foo)

---

### Post by bountonw on 2006-03-06
Maybe I don't understand.

I was reading through the linux journal and saw this article on Python.  I was interested in the C code.

[http://www.linuxjournal.com/article/8794](http://www.linuxjournal.com/article/8794)

When I try to compile, I get errors.

```

#include <stdio.h>

void main()
{
	int origPile, tempPile, man;
	for (origPile=5; origPile<99999; ++origPile) {   //A
		tempPile = origPile;                         //B
		for (man=0; man<5; ++man) {                  //C
		if ((tempPile%5) != 1) goto foo;         //D
		tempPile = (tempPile-1) * 4 / 5;         //E
		}
		if (tempPile%5) continue;                    //F
		printf("Victory! %d\n", origPile);           //G
		break;
	foo:
		}
}
```

```
coconuts.c: In function ‘main’:
coconuts.c:16: error: label at end of compound statement
coconuts.c:4: warning: return type of ‘main’ is not ‘int’

```

So what is the foo doing here that my compiler doesn't like?

---

### Post by hod139 on 2006-03-06
They are using foo as a label for the goto statement.  They seem to be missing a semicolon ';' after the label though. It should say 
```

foo:;

```

I should also add that the use of goto is highly discouraged.

---

