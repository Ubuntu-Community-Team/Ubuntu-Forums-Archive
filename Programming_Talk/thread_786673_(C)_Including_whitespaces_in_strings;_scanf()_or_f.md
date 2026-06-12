---
title: "(C) Including whitespaces in strings; scanf() or fgets()?"
date: 2008-05-08
forum: Programming Talk
---

### Post by spadewarrior on 2008-05-08
Hi.

I'm very new to C and I'm trying to store a string with whitespaces from stdin. I can't get this to work in either scanf or fgets (my tutor only knows TurboC and said to use gets(), obviously this is a bad idea).

Can anyone show me a way to include whitespaces and then end the input to the string after \n is pressed?

Any help greatly appreciated. This is driving me mad!

---

### Post by smartbei on 2008-05-08
gets() is obviously a bad idea; fgets() is fine. Try it. :)

---

### Post by spadewarrior on 2008-05-08
Thanks for replying. I'm trying fgets but it won't accept the input when enter is pressed, i.e. it waits until the whole of the buffer is filled. How can I get it to stop at enter? Is this happening because I'm using ncurses.h?

---

### Post by smartbei on 2008-05-08
Hmmm...

This:
```

#include <stdio.h>

#define BUFFER_SIZE (20)

int main(void)
{
	char input[BUFFER_SIZE];
	
	fgets(input, BUFFER_SIZE, stdin);
	
	puts(input);
	
	return 0;
}

```
works for me, so perhaps it is indeed ncurses.

---

### Post by spadewarrior on 2008-05-08
Works for me too. In that case I need to find a way of moving the cursor to different parts of the screen without ncurses. 

Any ideas?

---

### Post by WW on 2008-05-08
If you are using ncurses, why not use the one of the [ncurses input functions](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/scanw.html), perhaps getstr()?

---

### Post by spadewarrior on 2008-05-08
Excellent! Thanks for that, just what I was looking for.

---

