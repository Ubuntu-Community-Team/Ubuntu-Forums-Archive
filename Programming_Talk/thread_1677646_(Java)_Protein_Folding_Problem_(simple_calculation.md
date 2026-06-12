---
title: "(Java) Protein Folding Problem (simple calculation fail)"
date: 2011-01-29
forum: Programming Talk
---

### Post by Max_Mackie on 2011-01-29
solved :)
Thank you.

---

### Post by Max_Mackie on 2011-01-29
bump

---

### Post by unknownPoster on 2011-01-29
> **Max_Mackie said:**
> bump


You're only supposed to bump once every 24 hours. Patience is a key thing in this forum. That being said, just from the code you have provided. The "grid" elements are never initialized. Your if statements will always fail b/c grid[i][j] will never be 'h' or 'p' or maybe they are initialized to whatever namearray is. You need to provide more code.

---

### Post by Max_Mackie on 2011-01-29
Pardon me for the early bump :)
What do you mean by initializing each element? I initialize the matrix at the beginning (char[][] grid = new char[51][51];). I'm saying if the string contains an 'h', put it in this grid square.

Thanks for your reply

---

### Post by TheCivilian on 2011-01-29
Hi Max_Mackie,

just by looking at a section of your code it is difficult to analyze the entirety of the problem. There may be a problem within another part of your code and it would be wise to provide more of your code. The method that you have provided from the website seems to have other parts that may be affecting your code. Before attacking the question, it would be wise on my part to not jump to a conclusion before seeing the other class files.

Best regards,

TheCivilian

---

### Post by Max_Mackie on 2011-01-29
Hey thanks for answering :)
I've uploaded a .zip file with my classes.
Thanks for offering to help.

---

