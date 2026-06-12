---
title: "Members of a structure not updating"
date: 2010-06-07
forum: Programming Talk
---

### Post by esmeco on 2010-06-07
I'm using Visual Studio and I'm having a strange problem: each time i try to access the members of a structure with the dot or -> notation,some members don't show up and in some even show up members that were there previously but then I decided to remove.
What could be the source of this problem?

---

### Post by Zugzwang on 2010-06-07
Autocompletion is a complicated thing. The IDE probably doesn't realize changes immediately. Look for something like a "rebuild index" function for autocompletion. "Rebuild all" could also resolve the issue, depending on how it is implemented. Finally, restarting the IDE might also do the trick. Finally, read the IDE's manual on the autocompletion feature.

---

### Post by esmeco on 2010-06-07
Unfortunately "Rebuild All" and and exiting the IDE didn't work.Maybe If I create another project and copy the header and cpps to the project...
There seems to be in the project folder a "Vc++ Intellisense Database" file.Is it possible to be messing with it and add what it's lacking?






Edit: It's working now!Closed Visual Studio then deleted the .ncb file and started Visual Studio again which created a new .ncb

---

