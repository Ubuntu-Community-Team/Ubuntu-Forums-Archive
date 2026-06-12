---
title: "Java:Blank Panel"
date: 2007-01-04
forum: Packaging and Compiling Programs
---

### Post by serlex on 2007-01-04
Sorry guys, i searched for this problem could not find a solution.

Don't know what i'm going but, every time i run a Jpanel program, it comes out blank!

any ideas?

---

### Post by hod139 on 2007-01-05
What version of Java do you have installed?  I suggest using Sun's version [available in the repos]("http://ubuntuforums.org/showthread.php?t=201378").  Also, can you post some code.  Lastly, you might want to ask a mod to move this thread into the main Programming Talk section, not as many people poke their heads in this sub-forum.

---

### Post by serlex on 2007-01-07
hmm, i did a search around, it might be because of beryl, i havent actually tested it without beryl, cause im lazy

---

### Post by YourFriendlyGopher on 2007-01-09
Oops, double post. :(

---

### Post by YourFriendlyGopher on 2007-01-09
I have this problem as well, turns out it was Beryl as you've already figured out. One way I get around it is to temporarily set your window manager to metacity (via beryl manager) and then launch the program again. Another thing that doesn't work for me but may for you is to set some environmental variables, outlined here:

[http://ubuntuforums.org/showthread.php?t=316398]("http://ubuntuforums.org/showthread.php?t=316398")

Hope this helps.

---

### Post by Seine on 2007-01-10
export AWT_TOOLKIT=MToolkit should fix this.

---

