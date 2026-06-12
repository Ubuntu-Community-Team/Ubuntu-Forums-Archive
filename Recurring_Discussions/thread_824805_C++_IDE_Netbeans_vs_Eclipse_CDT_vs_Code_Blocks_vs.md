---
title: "C++ IDE: Netbeans vs Eclipse CDT vs Code Blocks vs ?"
date: 2008-06-10
forum: Recurring Discussions
---

### Post by kung fu buntu on 2008-06-10
I have replaced xemacs (1) with kdevelop (2) for my C++ project and now I wish to replace it with something "smarter". And by that I mean **code completion** and any other nice features like: **memory leaks detection, debugger integration with gdb, makefiles, doxygen documentation support, custom version control**, etc.

(1) one reason was the lame window cycle shortcut
(2) because it doesn't support code completion nor bzr integration (it's hard coded to subversion)

I never used Netbeans, or Eclipse CDT, or Code Blocks but google told me they seem to be good. Well, at least they all have code completion.

The purpose of this thread isn't to get replies like "IDE x rocks!" but to get constructive messages like &quot;I use X because it supports this feature which other IDEs don't."

I give more importance to features than to speed.

As for code completion, it should support both the standard libraries, as well as what is included in the header files.
Example, if I have:
  #include <bar/openbar.h>
  #include "../my_includes/foo.h"
The IDE should understand both header files and provide proper code completion.
And it would be great if it showed corresponding documentation as well.

---

### Post by Npl on 2008-06-10
im looking for a good C++ IDE myself (well, one that isnt Visual Studio :)). So far I can say that Eclipse + CDT plugin is horrible, its cleary an afterthougt, indexing (the thing that should give you autocompletion) is inacceptably slow and quite weird.
It has some nice things like code-templates tho, but I cant recommend it at all.

Code::Blocks looks very nice, be sure to get a nightly version they are typically better than the (pre)releases. I still dint spend much time on it, but its very promising so far

---

### Post by KingTermite on 2008-06-10
I'm planning on evaluating as well. 

I came across this which helped narrow down the ones I'd try/play with.
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)


KDevelop and Code::Blocks seemed to be the two most featureful options.

---

### Post by kung fu buntu on 2008-06-10
The wikipedia article isn't of much help. It doesn't compare features.

Another thing I would like to see is customizable SCM, which kdevelop doesn't support (it's stuck to subversion).

---

### Post by KingTermite on 2008-06-10
> **kung fu buntu said:**
> The wikipedia article isn't of much help. It doesn't compare features.

Another thing I would like to see is customizable SCM, which kdevelop doesn't support (it's stuck to subversion).

You asked about debuggers, it mentioned that.

No it doesn't go in to specific features, which I'd like to see too.

---

### Post by kung fu buntu on 2008-06-10
Updates on kdevelop:
- doesn't provide a shortcut for toggling breakpoints (IMO this sucks)
- "supports" nice auto completion features, but is not working for me :(
I type **string_variable.** and nothing happens.

---

### Post by janfsd on 2008-06-11
Don't forget to try Anjuta too. Since I am not too much into coding I can't tell you which one is better. I just remember that Code::Blocks wasn't stable for me, sometimes it crashed and I lose the latest code I wrote... However it could've changed. Long time ago I didn't use it.

---

### Post by rnodal on 2008-06-11
Even thought Code blocks is (at least in my opinion) still very immature I think is one of the best tools out there. One feature I depend a lot is in code completion and Code Block has it. It also supports a great number of compilers and debuggers. It has a plug-in that lets you profile your code. About memory leaks, I recommend valgrind([http://valgrind.org/]("http://valgrind.org/")). Netbeans and Eclipse and any java based program to me is a waste of time when it comes to applications that are big because they tend to consume a lot of ram and slow down your computer. So I recommend Code Blocks. 

-r

---

### Post by dynamethod on 2008-06-11
NetBeans 6.1 is far superior than codeblocks or eclipse imo

---

### Post by antler on 2008-06-30
I faced this little dilemma as well. I really wanted to like CodeBlocks because it was simplistic and had all the features that I'd wanted. However, it's quite buggy. Over a 2hr evaluation on a Ubuntu machine, it crashed no less than 4 times. It also had problems with window bordering on the window that displayed the values of variables during debugging. I couldn't even close this window down or get to the main menu once I'd opened it.

So, I'm sticking with Netbeans. Although it can be a bit heavier than CodeBlocks, it's very stable. Also, Java programs function extremely well on Linux machines in comparison to Windows. It was very snappy. Must be the better memory management and process scheduling in Linux :-D

---

