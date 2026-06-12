---
title: "[SDL] Creating a Smaller Executable"
date: 2011-03-02
forum: Packaging and Compiling Programs
---

### Post by dodle on 2011-03-02
I thought that I could make the output executable smaller by including sub-headers instead of the main "SDL.h", but the executable comes out to be the same size. Am I mistaken?

[php]#include <SDL/SDL.h>[/php]

vs.

[php]#include <SDL/SDL_video.h>
#include <SDL/SDL_events.h>[/php]

Shouldn't the latter create a smaller executable?

---

### Post by TenPlus1 on 2011-03-02
Wont the compiler only pull in what headers it needs/uses anyway, hence the same size executable ?

---

### Post by MadCow108 on 2011-03-02
the number of headers have no impact on the size of the executable.
they just contain information needed by the compiler to produce the executable from the source code (usually in .c/.cpp files)
information provided by an header which is not needed does not flow into the final output.

they only impact compilation time if you use an excessive amount of very large headers.

to decrease executable size you can compile with -Os (which may make the program slower) and strip unneeded strings and debugging symbols from it with the strip command.

---

### Post by dodle on 2011-03-02
Okay, I thought that when "#include" was used it just added everything from the header files to the source code. I didn't realize that the compiler was smart enough to pull only what it needed.

---

### Post by eerror on 2011-03-02
It's not that it "pulls what it needs".  Header files are needed only during the compilation process (like MadCow108 said above) and they don't  end up in the executable. 

Happy compiling!

---

### Post by dodle on 2011-03-02
Nvm

I don't know how to delete a post.

---

### Post by Aikar on 2011-03-06
as said above, it does affect compile time.

basically it pulls every thing in, then the linker runs an optimizer that goes over and finds any 'dead' code thats not referenced by anything and removes it.

---

