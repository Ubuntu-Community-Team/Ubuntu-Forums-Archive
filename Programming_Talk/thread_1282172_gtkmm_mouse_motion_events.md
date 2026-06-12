---
title: "gtkmm mouse motion events"
date: 2009-10-04
forum: Programming Talk
---

### Post by mdkess on 2009-10-04
Hi,

A couple of days ago, I upgraded to Karmic Alpha6, and (surprise!) I've been having one really strange problem. I'm using gtkmm, and suddenly mouse motion events are no longer firing. Does anyone know what I could possibly do to fix this? Button clicks get registered, it's just the mouse motion events that do not. I'm quite certain it's not a problem with my own code, as I tested it on 9.04 and 8.04 and it works as expected.

Thanks.

---

### Post by SledgeHammer_999 on 2009-10-04
Then maybe it's a problem with the gtkmm packages! Don't forget that you are using an alpha version. Try the beta that came out.

Also when you recompiled your program in karmic did the compiler throw any warnings?
Or do you having any warnings/errors during runtime?(in the terminal)

---

### Post by mdkess on 2009-10-04
> **SledgeHammer_999 said:**
> Then maybe it's a problem with the gtkmm packages! Don't forget that you are using an alpha version. Try the beta that came out.

Also when you recompiled your program in karmic did the compiler throw any warnings?
Or do you having any warnings/errors during runtime?(in the terminal)

Hey, thanks for the quick reply!

 No errors or warnings when compiling, alas. 

I'm not entirely convinced that it's gtkmm, since my mouse has been acting sort of strange since installing 9.10. Another problem with the mouse I've been having has been that clicks don't register in flash videos on Youtube in Firefox I've updated to the latest version of Ubuntu, with no success.

Another strange thing that's happened is in seemly all 3D games, when playing in fullscreen the mouse cursor jumps to the bottom right corner of the screen whenever I click. This is on Linux games, not stuff running in Wine. It might be a video drivers problem, but glxgears is giving 55k frames per 5 seconds, so something is working.

Oh dear, oh dear, oh dear.

---

### Post by mdkess on 2009-10-05
Turns out it was a bug related to gtk+2.0. The latest patch resolves this issue.

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/442078](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/442078)

EDIT: Nevermind, issue not resolved. The latest updates fixed a bunch of issues with Eclipse, so I assumed that my problems were no more, but this was a false assumption. This shows progress though, so perhaps the gtkmm people just have to update their bindings.

EDIT2: Running "export GDK_NATIVE_WINDOWS=true" fixes this. See [https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257](https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257)

---

