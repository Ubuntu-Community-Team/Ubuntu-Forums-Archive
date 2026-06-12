---
title: "monodevelop - executable not found"
date: 2008-05-23
forum: Programming Talk
---

### Post by muteXe on 2008-05-23
Hiya,
Created a new solution, not even added to it yet.  It's just the "hello world" example.  When i try to build this I get "Build failed.  Exexcutable not found: /usr/bin/gmcs".  I've cleary not installed something!
Any ideas?
thanks,
mute

---

### Post by muteXe on 2008-05-23
Hmm maybe i should have posted this in the packaging and compiling forum :)

---

### Post by Zugzwang on 2008-05-23
Well, if the executable wasn't found, why don't you just type "gmcs" in the terminal. You will get a message telling you which package is missing. Install it and there you go!

---

### Post by Death4Life on 2008-05-23
I just ran into this as well, 
just install the *mono-gmcs* package!

---

### Post by hiratayutaka on 2008-06-15
:guitar:
sudo apt-get install mono-gmcs

---

### Post by hiratayutaka on 2008-06-15
:popcorn:
sudo apt-get install mono-gmcs
sudo apt-get install automake

---

### Post by Hollonb on 2008-06-21
Just wanted to add my thanks, I've been trying to solve this same problem for several weeks.  This worked perfectly...

---

### Post by cavarl on 2008-07-12
That solved my problem, too.
Thank you!

---

### Post by stranger22 on 2008-09-17
> **Zugzwang said:**
> Well, if the executable wasn't found, why don't you just type "gmcs" in the terminal. You will get a message telling you which package is missing. Install it and there you go!

Thanks mate, it worked just fine. I can now run my C# programs.

---

### Post by quack on 2008-10-07
Just installed MonoDevelop and gotta say it looks it like a fantastic project.

But what's with the GMCS thing? Sure, I found this thread and solved my problem in 30 seconds but, if nothing will compile without it, shouldn't one of the other packages pull it in at install time?

---

### Post by directhex on 2008-10-08
gmcs is the CLI 2.0 compiler, mcs is the CLI 1.1 compiler. It's not a hard dependency of the package as MD may be used to target several languages (not just C#, and not just version 2 thereof) - but it's a Recommends on the basis that you probably want it anyway. Unfortunately, unlike Debian, not all the apt front-ends in Ubuntu pull in recommends by default - so I think Synaptic users will be missing it whereas Aptitude users are fine

---

### Post by quack on 2008-10-08
Thanks for the info - that makes a lot of sense. And yes, I installed through Synaptic.

Agree it would be too strong to make gmcs a hard dependency... but it is likely the first thing that a new user will want to do. Maybe worth adding a special-case error message or something in the system which will catch newbie users tripping over this and point them in the right direction.

---

### Post by directhex on 2008-10-08
> **quack said:**
> Thanks for the info - that makes a lot of sense. And yes, I installed through Synaptic.

Agree it would be too strong to make gmcs a hard dependency... but it is likely the first thing that a new user will want to do. Maybe worth adding a special-case error message or something in the system which will catch newbie users tripping over this and point them in the right direction.

Good idea. How about some kind of "not found" message, like "executable not found: /usr/bin/gmcs"? ;)

---

### Post by true_friend on 2008-10-08
Basically it should be added as a dependancy in MonoDevelop package so that it installs with MD.

---

### Post by directhex on 2008-10-09
> **true_friend said:**
> Basically it should be added as a dependancy in MonoDevelop package so that it installs with MD.

What if you're only using MD to develop Python or C or somesuch?

---

### Post by true_friend on 2008-10-09
I think there are better alternatives available for C and Python apart from MD. In my opinion people use MD to develop C# 90+ percent.

---

### Post by directhex on 2008-10-09
> **true_friend said:**
> I think there are better alternatives available for C and Python apart from MD. In my opinion people use MD to develop C# 90+ percent.

You're right, which is why it's a Recommends: - the big difference as far as most package managers are concerned is that you can remove a Recommends but keep the package there (e.g. remove mono-gmcs but keep monodevelop), whilst the same is not true of a Depends:

The unfortunate odd man out is Synaptic on pre-Intrepid Ubuntu, which does not install Recommends by default. It's Synaptic's failing, not the package's.

---

### Post by jlawson on 2008-10-09
Thanks guys,  worked for me too!

---

### Post by nazgul42 on 2008-10-14
Thanks a lot, but it is kinda obvious now that I think about it...

---

### Post by mrinvader on 2009-08-05
Hi all!

Installing mono-gmcs worked great for running ./configure on xfx-screensaver-settings-0.3.0 under Jaunty with one change. mono-gmcs installs /usr/bin/gmcs2 instead of /usr/bin/gmcs. To fix this I had to do :
```

ln -s /usr/bin/gmcs2 /usr/bin/gmcs

```
as root.

:D

---

### Post by directhex on 2009-08-05
> **mrinvader said:**
> Hi all!

Installing mono-gmcs worked great for running ./configure on xfx-screensaver-settings-0.3.0 under Jaunty with one change. mono-gmcs installs /usr/bin/gmcs2 instead of /usr/bin/gmcs. To fix this I had to do :
```

ln -s /usr/bin/gmcs2 /usr/bin/gmcs

```
as root.

:D

Or install mono-devel

---

