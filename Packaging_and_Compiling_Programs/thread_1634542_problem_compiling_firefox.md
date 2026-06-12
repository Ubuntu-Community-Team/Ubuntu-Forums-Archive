---
title: "problem compiling firefox"
date: 2010-11-30
forum: Packaging and Compiling Programs
---

### Post by termin on 2010-11-30
when trying to compile firefox i get this error:
../../layout/style/nsStyleStruct.h:1199: error: ‘NS_STYLE_DISPLAY_INLINE_GRID’ was not declared in this scope
../../layout/style/nsStyleStruct.h:1199: error: expected primary-expression before ‘||’ token
../../layout/style/nsStyleStruct.h:1200: error: ‘NS_STYLE_DISPLAY_INLINE_STACK’ was not declared in this scope
make[4]: *** [nsDOMWindowUtils.o] Error 1
make[4]: Leaving directory `/home/media/Desktop/mozilla-1.9.2/dom/base'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/media/Desktop/mozilla-1.9.2/dom'
make[2]: *** [libs_tier_gecko] Error 2
make[2]: Leaving directory `/home/media/Desktop/mozilla-1.9.2'
make[1]: *** [tier_gecko] Error 2
make[1]: Leaving directory `/home/media/Desktop/mozilla-1.9.2'
make: *** [default] Error 2


and the code inside the file with the error is like this:
 }

  PRBool IsBlockOutside() const {
    return NS_STYLE_DISPLAY_BLOCK == mDisplay ||
           NS_STYLE_DISPLAY_LIST_ITEM == mDisplay ||
           NS_STYLE_DISPLAY_TABLE == mDisplay;
  }

  PRBool IsInlineOutside() const {
    return NS_STYLE_DISPLAY_INLINE == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_BLOCK == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_TABLE == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_BOX == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_GRID == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_STACK == mDisplay;
  }

  PRBool IsFloating() const {
    return NS_STYLE_FLOAT_NONE != mFloats;
  }

  PRBool IsAbsolutelyPositioned() const {return (NS_STYLE_POSITION_ABSOLUTE == mPosition) ||
                                                (NS_STYLE_POSITION_FIXED == mPosition);}





any help? thanks!

---

### Post by rapidrocket7 on 2010-11-30
> **termin said:**
> when trying to compile firefox i get this error:
../../layout/style/nsStyleStruct.h:1199: error: ‘NS_STYLE_DISPLAY_INLINE_GRID’ was not declared in this scope
../../layout/style/nsStyleStruct.h:1199: error: expected primary-expression before ‘||’ token
../../layout/style/nsStyleStruct.h:1200: error: ‘NS_STYLE_DISPLAY_INLINE_STACK’ was not declared in this scope
make[4]: *** [nsDOMWindowUtils.o] Error 1
make[4]: Leaving directory `/home/media/Desktop/mozilla-1.9.2/dom/base'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/media/Desktop/mozilla-1.9.2/dom'
make[2]: *** [libs_tier_gecko] Error 2
make[2]: Leaving directory `/home/media/Desktop/mozilla-1.9.2'
make[1]: *** [tier_gecko] Error 2
make[1]: Leaving directory `/home/media/Desktop/mozilla-1.9.2'
make: *** [default] Error 2


and the code inside the file with the error is like this:
 }

  PRBool IsBlockOutside() const {
    return NS_STYLE_DISPLAY_BLOCK == mDisplay ||
           NS_STYLE_DISPLAY_LIST_ITEM == mDisplay ||
           NS_STYLE_DISPLAY_TABLE == mDisplay;
  }

  PRBool IsInlineOutside() const {
    return NS_STYLE_DISPLAY_INLINE == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_BLOCK == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_TABLE == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_BOX == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_GRID == mDisplay ||
           NS_STYLE_DISPLAY_INLINE_STACK == mDisplay;
  }

  PRBool IsFloating() const {
    return NS_STYLE_FLOAT_NONE != mFloats;
  }

  PRBool IsAbsolutelyPositioned() const {return (NS_STYLE_POSITION_ABSOLUTE == mPosition) ||
                                                (NS_STYLE_POSITION_FIXED == mPosition);}





any help? thanks!
Why exactly are you compiling it yourself? The .deb package is available from the firefox website and is also available through the repositories by either using Synaptic, Software Center or through terminal by using
```
sudo apt-get install firefox
```

---

### Post by wojox on 2010-11-30
[Compiling Firefox]("http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html")

---

### Post by termin on 2010-11-30
im compiling firefox to run faster with my sytem and to enable pgo and disable xulrunner. 
i did all of this in the ./configure part

now, how do i fix the error.
thanks. 
ps: sorry if that sounded rude i just wanted to fix the error fast.

---

### Post by MrQuincle on 2010-12-01
> **termin said:**
> im compiling firefox to run faster with my sytem and to enable pgo and disable xulrunner. 
i did all of this in the ./configure part

now, how do i fix the error.
thanks. 
ps: sorry if that sounded rude i just wanted to fix the error fast.

If you want to make sure everything compiles on your system use the source code that comes with the package and recompile it yourself.

First make sure you have actually the src repositories enabled, check your /etc/apt/sources.list file for lines like:

```
deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick universe
```

Then:
```

sudo apt-get build-dep firefox
apt-get source firefox
```

On my Ubuntu 10.10 system this results in a "mozilla-1.9.2-3.6.12+build1-source.tar.bz2" file in a "firefox-3.6.12+build1+nobinonly" directory that you need to untar yourself.

Then follow the usual directions at [https://developer.mozilla.org/En/Simple_Firefox_build](https://developer.mozilla.org/En/Simple_Firefox_build)

```

echo '. $topsrcdir/browser/config/mozconfig' > mozconfig
echo 'mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/objdir-ff-release' >> mozconfig
echo 'mk_add_options MOZ_MAKE_FLAGS="-j4"' >> mozconfig

make -f client.mk

```

Done. It at least compiles on my system. :-)

---

### Post by termin on 2010-12-01
thanks people! this did it for me, i have a good firefox build that is not on the bloated side. the whole main reason i was doing this is because i run and old system (planning to get windows7 laptop soon) and i need a good web browser. i know there is epiphany, but i just don't like the interface. i just needed something gecko based anyway.

---

