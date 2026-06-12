---
title: "C++ Hello World"
date: 2007-01-13
forum: Programming Talk
---

### Post by Ryan H on 2007-01-13
I'm learning C++ and I'm writing a basic program:
```
#include <iostream>

int main()
{
	using std::cout;
	using std::end1;
	
	cout << "Hello World!\n";
	cout << end1;
	return 0;
}
```
When I try to compile it I get this error: ```
./hello.cpp: In function &#8216;int main()&#8217;:
./hello.cpp:6: error: &#8216;std::end1&#8217; has not been declared
./hello.cpp:9: error: &#8216;end1&#8217; was not declared in this scope
```
I followed the book I am reading correctly, did I type it wrong?

-Ryan H

Edit: It was an error in my typing, the only difference between '1's and lowercase 'L's in the font is there is no tail on the 1's but there is on the l's. Seens backwards but now everything is fixed,

---

### Post by rand0m3r on 2007-01-13
i'm glad i bumped into ur thread. i just started learning C++ half an hr ago and had the same prob! :D

---

### Post by xtacocorex on 2007-01-13
It is endl (end little L) not end1.  Correct that, and your program should work.

---

### Post by Wybiral on 2007-01-13
Yes, it's endl (with an L), think of it as standing for "end line"

Also, if you are going to be using cout and endl it's easier to just use the entire std namespace.

This is a pretty common "hello world"

```

#include <iostream>

using namespace std;

int main()
{
	cout << "Hello World!" << endl;
	return 0;
}

```

---

### Post by kinson on 2007-01-14
> **xtacocorex said:**
> It is endl (end little L) not end1.  Correct that, and your program should work.

I blame the font of many books :p "l" and "1" look almost the same in certain fonts :P

---

### Post by lloyd mcclendon on 2007-01-14
always prefer the "\n" over the endl since that .. i forget why i think it flushes the buffer or something.  decades ago when i did c++ i rmember reading that in a good book

cout << "Hello\n";

is better ( & cleaner) than

cout << "Hello" << endl;

---

### Post by supirman on 2007-01-14
For reference, you should realize that using std::endl is not exactly the same as placing a newline in the output.  Using std::endl actually forces the buffer to be flushed, whereas \n does not.  

Link: [http://www.cplusplus.com/reference/iostream/manipulators/endl.html]("http://www.cplusplus.com/reference/iostream/manipulators/endl.html")

---

### Post by cocteau on 2007-01-14
> **lloyd mcclendon said:**
> always prefer the "\n" over the endl since that .. i forget why i think it flushes the buffer or something.

It's actually the other way round. endl flushes the buffer, the newline character doesn't. It depends what to use where. As I understand it endl produces a very slight additional overhead as it causes the text to get printed here and now, whereas the newline character just hangs in the buffer until it is full, and/or it is flushed automatically.

The only problem there is with \n is that if your program is off to do other things that keep your system busy the buffer might not be flushed and your text might not get printed. Best bet is to always end the last output output statement with an 'endl'.


...as the previous post said... sorry hadn't seen that...

---

### Post by Sonicgoo on 2007-02-27
Great information. Thanks!

Exactly what I was looking for, I'm so happy with my decision to load up Ubuntu, 

Thanks again.

---

### Post by pmasiar on 2007-02-28
> **lloyd mcclendon said:**
> always prefer the "\n" over the endl since that .. i forget why i think it flushes the buffer or something.  decades ago when i did c++ i rmember reading that in a good book

Prime example of [http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming) :-)

---

