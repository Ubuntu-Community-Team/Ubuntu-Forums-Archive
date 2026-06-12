---
title: "Vim Question - Single command to swap words"
date: 2012-01-05
forum: Programming Talk
---

### Post by Percivale on 2012-01-05
Hi, I'm working through Sobell's book *Linux Commands, Editors and Shell Programming*, and I'm stumped on one of his odd-numbered exercises (for which he does not publish the answers). It's chapter 6, exercise 15.

I'll quote it in its entirety:

*Which command would you use to swap the words hither and yon on any line with any number of words between them? (You need not worry about special punctuation, just uppercase and lowercase letters and spaces.)*

So it seems to mean this: what single command would swap two strings on any line in the file?

I really have no clue how to do this, especially considering that hither and yon might exist before or after one another on a given line (although it seems he's implying hither always comes before yon).

Any ideas?

Thanks

---

### Post by cgroza on 2012-01-05
I know that vim does not have a dedicated command for this one, but I know you can write a macro for it.

For the command line in general, Alt + t transposes 2 words.

---

