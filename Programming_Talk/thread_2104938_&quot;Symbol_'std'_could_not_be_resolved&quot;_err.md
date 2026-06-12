---
title: "&quot;Symbol 'std' could not be resolved&quot; error in Eclipse"
date: 2013-01-14
forum: Programming Talk
---

### Post by Tununias on 2013-01-14
I'm sorry if this isn't in the right section or if this has already been resolved. I've looked through several forums and none of them helped me.

I'm a Computer Science major at a 2 year college. I've used Eclipse for my Java classes and loved it, but when I tried it with C++, I get an error when using "using namespace std;". I consider myself a beginner, but this isn't my first time using C++. I know my code is all correct and even compiled and ran it via terminal.
I also have the C++ development tools installed in Eclipse and the GNU C++(g++) compiler installed.

This is my code I typed. > #include <iostream>
using namespace std;

The std has a red underline that displays "Symbol 'std' could not be resolved" when I put my cursor over the text.
I'm not sure what else to put. I'm using Ubuntu 12.10 and Eclipse 3.8.0. I know this isn't much info, but I'm not sure what else to put that would be helpful. 

I'd much rather use Eclipse if someone could help me, but if all else fails, I'll install Code::Blocks and just use that.

---

### Post by wheadom on 2013-07-05
Hello,

It sounds like you have already tried this, but anyway I have just had what seems like a similar problem with CDT (though I am using Ubuntu 13.04). I had installed gcc from the software centre and got this problem. I then went and installed g++ (which I didn't have installed). Then I deleted my 'hello world' CPP project, restarted Eclipse (though these steps may not have been necessary), then created the CPP hello world project again, and it all seemed to work. Like you, I have used Java a lot, and written Visual C++ and C (C/400 actually). but not done C++ in Eclipse.

Mark W.

---

