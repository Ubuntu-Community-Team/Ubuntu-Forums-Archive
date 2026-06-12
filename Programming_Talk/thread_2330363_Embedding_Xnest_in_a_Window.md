---
title: "Embedding Xnest in a Window"
date: 2016-07-11
forum: Programming Talk
---

### Post by jupiter82 on 2016-07-11
I'm trying to use the -parent flag to Xnest, and not having much luck
with it.  I'm using an xembed container in Qt (which works with
mplayer, source below), and I'm trying to run Xnest as

Xnest -parent <winid> :1

I've tried different variations on -class, -sss, -install, and other
things that don't make sense to me, but everything I try gives me the
error:

X Error of failed request:  BadAccess (attempt to access private
resource denied)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Serial number of failed request:  155
  Current serial number in output stream:  156

Just before Xnest exits, I see a flash of XScreenSaver in a grainy
black and white pattern.  Xnest works fine without the -parent flag,
aside from the fact that it isn't embedded that way.

Does anybody use Xnest in Xembed mode, and if so, can anybody lend me
a hand?  I've pasted the source for my simple Qt app, and attached the
output of an strace of my failed Xnest run.

---

