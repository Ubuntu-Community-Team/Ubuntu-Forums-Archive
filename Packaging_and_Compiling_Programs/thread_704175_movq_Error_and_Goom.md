---
title: "movq Error and Goom"
date: 2008-02-22
forum: Packaging and Compiling Programs
---

### Post by Grosquick_ on 2008-02-22
Hello,

I'm trying to build VLC on my Ubuntu 7.10 and I have the following error when i build the goom2k4 contrib. :(

```

/tmp/ccL2mZWX.s:232: Error: suffix or operands invalid for `movq'
/tmp/ccL2mZWX.s:233: Error: suffix or operands invalid for `movq'

```

Does anyone have an idea?
Thanks for your help.  ;)

Solution : Bad version of gcc

---

### Post by untoldone on 2008-02-26
any chance you could go into more details with your solution?  I just ran into the same error compiling VLC extras in ubuntu 7.10

---

### Post by untoldone on 2008-02-29
I got past this in a different way (still yet to find out if this will cause problems or not).  My error happened while trying to do a make in the extras/contrib folder of vlc's source.  I cd into the src/<insert package name here> and configured/built the package that previously error-ed out using ubuntu's dev packages instead of its regular build mechanism.  This worked fine for compiling Goom and libgcrypt so far.

---

