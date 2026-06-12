---
title: "Help installing codeblocks"
date: 2010-03-18
forum: Programming Talk
---

### Post by scared0o0rabbit on 2010-03-18
I'm trying to install the SVN of CodeBlocks from the jenbrody repository (deb [http://apt.jenslody.de/](http://apt.jenslody.de/) any main) but I'm having trouble getting it to run.

I have it running on another computer, but I'm having some trouble on this computer.  When I run codeblocks from a command line I get this error message:

codeblocks: relocation error: /usr/lib/libcodeblocks.so.0: symbol _Z18wxSafeConvertWX2MBPKw, version WXU_2.8.2 not defined in file libwx_baseu-2.8.so.0 with link time reference

I'm not really sure what's causing this and how I can fix it.  I wasn't sure if I should post this here or one of the other help sections, so I'm sorry if this is the wrong place.

---

### Post by scared0o0rabbit on 2010-03-18
So I removed that source and removed codeblocks svn 6188 and then installed codeblocks 8.02 and it works fine, but as soon as I try and install the svn 6188 again I get the same error.  Any tips?

---

### Post by kellemes on 2010-05-04
> **scared0o0rabbit said:**
> So I removed that source and removed codeblocks svn 6188 and then installed codeblocks 8.02 and it works fine, but as soon as I try and install the svn 6188 again I get the same error.  Any tips?

Same here.. version 8.02 is old, very old..
You need the latest nightly, I'll be trying to get it running today and report back.
Didn't get the nighties running from Lucid for some reason..

---

### Post by kellemes on 2010-05-04
delete

---

