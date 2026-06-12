---
title: "Linking errors when compiling an OpenCV program..."
date: 2011-11-16
forum: Packaging and Compiling Programs
---

### Post by someoney3000 on 2011-11-16
So, I'm working with an opencv application that I'm developing... when I go to compile I get this:

```

/usr/bin/ld: warning: libavcodec.so.52, needed by /usr/local/lib/libhighgui.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libavformat.so.52, needed by /usr/local/lib/libhighgui.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libavutil.so.49, needed by /usr/local/lib/libhighgui.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libswscale.so.0, needed by /usr/local/lib/libhighgui.so, not found (try using -rpath or -rpath-link)

```

And the program doesn't compile.

I followed this guide:

[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

Really, I just copy and pasted the commands.

Is there libraries still missing?  Or is the package just broken?

---

### Post by searchfgold6789 on 2011-11-17
You can use "apt-file" to look for packages that have those files you're missing. :popcorn:

---

### Post by someoney3000 on 2011-11-18
> **searchfgold6789 said:**
> You can use "apt-file" to look for packages that have those files you're missing. :popcorn:

Eh, I eventually installed everything from source.

That worked.

Thanks for the suggestion.

---

