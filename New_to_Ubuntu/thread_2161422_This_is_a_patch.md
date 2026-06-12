---
title: "This is a patch?"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by Akkaid on 2013-07-10
hey all,

trying to fix a primus issue.  Found some similar threads on the web, in one of them the Primus writer said to apply the following patch-

> 
diff --git a/libglfork.cpp b/libglfork.cpp index 6f07053..d2ffbe9 100644 --- a/libglfork.cpp +++ b/libglfork.cpp @@ -528,12 +528,16 @@ static GLXPbuffer lookup_pbuffer(Display *dpy, GLXDrawable draw, GLXContext ctx)      di.window = draw;      note_geometry(dpy, draw, &di.width, &di.height);    } -  else if (di.kind == di.XWindow && ctx && di.fbconfig != primus.contexts[ctx].fbconfig) +  else if (ctx && di.fbconfig != primus.contexts[ctx].fbconfig)    { -    // Recreate the backing PBuffer when a different FBConfig is used -    primus_warn("recreating incompatible pbuffer\n"); -    primus.drawables.erase(draw); -    return lookup_pbuffer(dpy, draw, ctx); +    if (di.pbuffer) +    { +      primus_warn("recreating incompatible pbuffer\n"); +      di.reap_workers(); +      primus.afns.glXDestroyPbuffer(primus.adpy, di.pbuffer); +      di.pbuffer = 0; +    } +    di.fbconfig = primus.contexts[ctx].fbconfig;    }    if (!di.pbuffer)      di.pbuffer = create_pbuffer(di);

Well....I have no clue how to 'run' that.   Hope someone does lol.

---

### Post by newb85 on 2013-07-10
It looks to me like one really long terminal command, probably intended to be copied and pasted into the terminal.  But I'm not familiar with the syntax, and have no idea what it's supposed to do, so I can't recommend running it.  (Actually, "--git" isn't listed as an option in the man page for diff, so I really don't know what's going on.)

---

### Post by steeldriver on 2013-07-10
It's a git-specific patch produced with the git-diff -p command I think - it's rally only useful if you are building the application from a git repo

[https://www.kernel.org/pub/software/scm/git/docs/git-diff.html](https://www.kernel.org/pub/software/scm/git/docs/git-diff.html)  

> 
What the -p option produces is slightly different from the traditional diff format:

   It is preceded with a "git diff" header that looks like this: 
   
diff --git a/file1 b/file2 



---

