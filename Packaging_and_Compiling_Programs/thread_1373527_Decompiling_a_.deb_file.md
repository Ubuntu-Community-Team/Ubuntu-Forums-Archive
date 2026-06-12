---
title: "Decompiling a .deb file"
date: 2010-01-05
forum: Packaging and Compiling Programs
---

### Post by beastrace91 on 2010-01-05
Is there a simple/easy way I can decompile a .deb file to get back to the source code so I can recompile it again with say different parameters?

Thanks,
~Jeff

---

### Post by Umang on 2010-01-06
You can download the source that was used to compile for any ubuntu package from Ubuntu Package. (In Firefox Ctrl+K, Alt+Down, 'U' and then search for package name, or visit it directly: [http://packages.ubuntu.com/](http://packages.ubuntu.com/))

On the right hand side, you will see three files. e.g (for gtg you will see gtg_0.1.2-1.dsc , gtg_0.1.2.orig.tar.gz, gtg_0.1.2-1.diff.gz)

ALTERNATIVE: I have not tried doing an apt-get source, but you could try that if you put source repositories in your sources.list also.

apt-get source package-name

Hope this is what you were looking for.

---

### Post by beastrace91 on 2010-01-06
> **Umang said:**
> Hope this is what you were looking for.

Not quite - I knew of both of these. I am looking to decompile a deb package back to source as I stated in the first post.

Anyone know how to do this?

~Jeff

---

### Post by Queue29 on 2010-01-07
> **beastrace91 said:**
> Not quite - I knew of both of these. I am looking to decompile a deb package back to source as I stated in the first post.

Anyone know how to do this?

~Jeff

You can't just decompile compiled source code (unless it was written in an interpreted language like python or C#).

---

### Post by iponeverything on 2010-01-07
> **beastrace91 said:**
> Not quite - I knew of both of these. I am looking to decompile a deb package back to source as I stated in the first post.

Anyone know how to do this?

~Jeff

I think that you think that you are being clear, but you actually not. You can break open a .deb in to all of its component pieces. You know, the preinstall, postinstall scripts, the man pages and the binaries. But, if you want to get the source to the binaries from from the binary .deb, the simple answer is that you can't, because they are not there. But, the source .deb for your binary .deb is exactly what your looking for. It is the exact same source with patches what was used to create the binary .deb and can be used to easily recreate it.

---

### Post by beastrace91 on 2010-01-07
> **Queue29 said:**
> You can't just decompile compiled source code (unless it was written in an interpreted language like python or C#).

Ahh, thank you much. I guess I should have figured that out.

Thanks,
~Jeff

---

