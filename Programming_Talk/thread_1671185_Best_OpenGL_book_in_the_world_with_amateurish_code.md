---
title: "Best OpenGL book in the world with amateurish code"
date: 2011-01-19
forum: Programming Talk
---

### Post by t1497f35 on 2011-01-19
Hi,
this is _**not**_ a rant, it's just the more I learn from [the 5th edition]("http://www.starstonesoftware.com/OpenGL/") the more I'm asking myself "how come the source code is so sloppy?" (but the book itself is (very) good).
I tried figuring out a decent excuse like "the author(s) didn't have enough time", but realized that it doesn't cut it.
Any ideas why?

There are many examples proving this, here's a few:
1) The function "bool LoadTGATexture()" returns a bool (true on success, false on failure) but the author doesn't check the return value. I thought to myself "*that's stupid, if there's an error loading the TGA texture the code won't handle it gracefully*", and what do you think? I just happened! - see point 2.
2) The author apparently doesn't know that Linux (as many Unixes in general) are case sensitive, and the TGA files he provides are called i.e. "MoonLike.tga", but from the C++ code he calls it "moonlike.tga"! Furthermore, the other file is called with lower case "L", thus "Marslike.tga", so he's not even consistent in naming his resource files - IMO only amateurish programmers in a hurry do such stuff.
3).. ok the post should be short so I'll stop here, again, it's not a rant, I'm just really surprised since this book on OpenGL is touted (for beginners) as the best in the world, and it is really cool but I wonder how can one ship such amateurish source code & resources.. Btw the source code is a recent snapshot of his svn repo.

---

