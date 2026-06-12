---
title: "monodevelop build failure"
date: 2009-03-24
forum: Packaging and Compiling Programs
---

### Post by col48 on 2009-03-24
I have installed monodevelop and mono but vbnc is acting up.  [It has never got further than this, so I suspect there is something else I need to install/download].  Can anyone shed some light, please?

This is what I get when I try to build a simple program.  It does not seem to matter what the program is.
```

Building Solution tstvb2

Building Project: tstvb2 (Debug)
Performing main compilation...
vbnc -out:"/home/aa_test/tstvb2/tstvb2/bin/Debug/tstvb2.exe" -nologo -utf8output -target:exe 

Build failed. ApplicationName='vbnc', CommandLine='"@/tmp/tmp2d6e043b.tmp"', CurrentDirectory='.', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'

```

---

### Post by directhex on 2009-03-24
Do you have the mono-vbnc package actually installed?

---

### Post by col48 on 2009-03-30
> **directhex said:**
> Do you have the mono-vbnc package actually installed?

I don't think so.  Looks like an obvious one, doesn't it?

I can't find it in Synaptic.  Do you know where I can find it?

---

### Post by directhex on 2009-03-30
> **col48 said:**
> I don't think so.  Looks like an obvious one, doesn't it?

I can't find it in Synaptic.  Do you know where I can find it?

In Jaunty. You could try going to packages.debian.org and grabbing the debs from there, they ought to install in Intrepid

---

### Post by col48 on 2009-03-31
Thanks, directhex.  One of these days, I'll get the hang of who does what with Linux, but then the whole point (I exaggerate only slightly) is that it isn't all done by M@@@@@@@@.

I'm still using Hardy, but I thought it worth a try anyway.

That's moved it on somewhat.  It now says a couple of files are an obsolete version but I'll see if I can sort that myself.

---

### Post by directhex on 2009-03-31
> **col48 said:**
> Thanks, directhex.  One of these days, I'll get the hang of who does what with Linux, but then the whole point (I exaggerate only slightly) is that it isn't all done by M@@@@@@@@.

I'm still using Hardy, but I thought it worth a try anyway.

That's moved it on somewhat.  It now says a couple of files are an obsolete version but I'll see if I can sort that myself.

For Hardy, go to [http://directhex.mfgames.com](http://directhex.mfgames.com)

---

### Post by col48 on 2009-04-03
A couple of days "fun" sorting out an urgent problem with burning a DVD, but now...

Thanks directhex once again.  That was the solution.
All(?) I need now is to get my head around the language.

---

### Post by danielt998 on 2009-05-13
I installed vbnc from packages.debian.org and it works now but I tried to compile a program I've written and it can't open my resources file it says " Description=Unable to open resource file '/home/daniel/Desktop/Monoply/Form8.resources': Stream is not a valid .resources file!  It was possibly truncated.(VBNC31509)]"

---

### Post by directhex on 2009-05-13
> **danielt998 said:**
> I installed vbnc from packages.debian.org and it works now but I tried to compile a program I've written and it can't open my resources file it says " Description=Unable to open resource file '/home/daniel/Desktop/Monoply/Form8.resources': Stream is not a valid .resources file!  It was possibly truncated.(VBNC31509)]"

Is /home/daniel/Desktop/Monoply/Form8.resources a valid .resources file?

---

