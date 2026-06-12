---
title: "J2ME WTK acting differently on Hardy and Lucid"
date: 2010-11-12
forum: Programming Talk
---

### Post by Irihapeti on 2010-11-12
Has anyone come across this problem and have a solution for it?

I have two installations. One (main PC) is Lucid. I also have Hardy on a USB drive.

Both installations have Sun JDK 1.6.0_22 from the repositories. Both have Sun WTK 2.5.2

I'm finding that a MIDlet (not my code) will run/compile on the Hardy system, but throws a java.lang.NullPointerException  error when I attempt to do this on Lucid.

To add to the confusion, I also have Eclipse (different versions) installed on both systems, using the WTK as emulator in both cases. AND the same MIDlet will run/compile successfully on both systems.

So, what might be missing on the Lucid install that's causing the WTK to complain when it's used on its own?

---

