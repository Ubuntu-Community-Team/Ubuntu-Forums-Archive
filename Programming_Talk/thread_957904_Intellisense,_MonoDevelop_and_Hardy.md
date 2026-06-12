---
title: "Intellisense, MonoDevelop and Hardy"
date: 2008-10-24
forum: Programming Talk
---

### Post by Devineman on 2008-10-24
Hello all,

I'm having some problems setting up MonoDevelop in Hardy 8.04.  It seems that Intellisense seems to be missing/invisible to me. I have checked that Auto-completion is turned on in Edit->Preferences->Enable Code Completion and the Ctrl-Space is set in the Show Completion Window.

I have tried this in a C++ project, C# project and VB.NET project, and Intellisense is missing from all of them.  I know how to use the dot notation and when to use it.  Also, in C++ files, the namespace accessor ( :: ) doesn't produce any results.

Can somebody help me please?

---

### Post by snova on 2008-10-24
Well, I can't help in figuring out why is isn't working (that could be a number of things), but please understand that IntelliSense is a Visual Studio thing. It isn't a generic term to be applied to all implementations of code completion.

---

### Post by Devineman on 2008-10-24
> **snova said:**
> Well, I can't help in figuring out why is isn't working (that could be a number of things)

Perhaps you could name a few of them for me to try then as this is annoying me a little.

P.S. Intellisense is shorter to type and people understand the phrase. Like Hoover.

---

### Post by snova on 2008-10-24
Maybe, but Hoover doesn't have a monopoly (that I know of). It's dull anyway. How about "AutoCode"?

I haven't used MonoDevelop in a long time. Perhaps it simply hasn't indexed your code yet? Maybe it doesn't know the locations of the libraries. I think there's also a pause before it does anything.

---

### Post by Devineman on 2008-10-24
> **snova said:**
> Maybe, but Hoover doesn't have a monopoly (that I know of). It's dull anyway. How about "AutoCode"?

AutoCode's great :) I always hated the Intellisense word anyway, feels like one of those buzzwords that marketing types come up with that don't mean anything.


> 
I haven't used MonoDevelop in a long time. Perhaps it simply hasn't indexed your code yet? Maybe it doesn't know the locations of the libraries. I think there's also a pause before it does anything.

Hope so, this is really messing with my productivity and I've got schedules to keep! Constantly referring to a (half complete) Mono documentation, MSDN and scouring my memory isn't exactly proving the best solution to finding class members, etc.  Guess AutoCode has made me lazy, but for some reason, I can live without it in C/C++, its just the managed languages where I seem to use it as a crutch.

Oh well, if anybody has any ideas, please let me know.

---

### Post by snova on 2008-10-25
Perhaps a different IDE would work better? Dunno how many have good C# support, though...

As for the incomplete Mono docs, it's annoying, but I think Mono should be compatible with Microsoft's .NET (at least for most of it), so why not use their documentation for now?

And when I suggested AutoCode, I was thinking more about what a better IDE would call it... Eh.

To be quite honest, I've never found an IDE with *really* good code completion. Microsoft might come up with undescriptive names for things, but they may have had an excuse.

---

### Post by james.king@4act.com on 2008-12-12
There is a repository where you can get all of the required packages to compile the latest version of monodevelop. 

[http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html)


If you build from svn I know code completion works amazingly well on c#. VB is supposed to work I believe, but I have not been as successful with that.

---

