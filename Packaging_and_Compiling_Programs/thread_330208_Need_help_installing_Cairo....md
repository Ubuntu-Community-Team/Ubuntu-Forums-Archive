---
title: "Need help installing Cairo..."
date: 2007-01-02
forum: Packaging and Compiling Programs
---

### Post by geek_Man on 2007-01-02
Hey y'all, I wanted to install GTK so I could use it with Perl. So I downloaded the source and the other dependencies, but when I try to install the Cairo (library?), I get this stuff when I try to run make:```
cairo-font.c: In function '_cairo_toy_font_face_scaled_font_create':
cairo-font.c:424: error: 'CAIRO_SCALED_FONT_BACKEND_DEFAULT' undeclared (first use in this function)
cairo-font.c:424: error: (Each undeclared identifier is reported only once
cairo-font.c:424: error: for each function it appears in.)
make[3]: *** [cairo-font.lo] Error 1
make[3]: Leaving directory `/home/foo/Desktop/cairo-1.2.6/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/foo/Desktop/cairo-1.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/foo/Desktop/cairo-1.2.6'
make: *** [all] Error 2

```

This is my first go at compiling from source, so I have no idea of what to do.
<feebleVoice>help...</feebleVoice>

---

### Post by geek_Man on 2007-01-03
Update: I noticed when I run configure, it tells me that I need a font backend and to install Free Type and Fontconfig(?). I've downloaded and installed Free Type and I've downloaded Fontconfig, but THAT tells me I need libxml-2.0. I've looked in Synaptic and it says I have libxml2. Configure also tells me I could change the environment variable for PKG_CONFIG_PATH... or something like that. How would I go about changing that so I could install Fontconfig so I could install Cairo so I could install Gtk???

---

### Post by hod139 on 2007-01-03
You should be using synaptic (or apt or aptitude) to install these packages, it sounds like you are not.  For example, for the GTK development files, install the package libgtk2.0-dev,
```

sudo aptitude install libgtk2.0-dev

```


For freetype there is libfreetype6-dev.  Basically search for packages with the -dev suffix.

---

### Post by hod139 on 2007-01-03
Oh, an looking at your thread title, for Cairo you can install libcairo2 and if you want the development files, libcairo2-dev.

---

### Post by geek_Man on 2007-01-03
Sounds cool, I'll try it out. I'm guessing it doesn't matter if I've already install Pango, Glib, Free Type, and atk from source?

BTW, mucho thank you for the reply!

---

### Post by hod139 on 2007-01-04
You might get conflicts from the libs you installed by source with the ones installed by ubuntu.  I would recommend using the libs in the repositories unless you absolutely need a more recent version for something specific.

---

### Post by geek_Man on 2007-01-04
Is there a way to remove the libs installed by source?

Also, what's special about *-dev packages? Would I need them for something?

---

### Post by geek_Man on 2007-01-04
Okay, people, guess what? I already had Gtk installed, only it was Gtk2. Excuse me while I go kick myself to death...
...
...
...
Thanks!

---

### Post by hod139 on 2007-01-05
> **geek_Man said:**
> Is there a way to remove the libs installed by source?

If you're lucky the maintainers wrote an uninstall script, ```
sudo make uninstall
```.  If not you have to manually find the installed files and delete by hand.

> 
Also, what's special about *-dev packages? Would I need them for something?
the -dev packages install what is needed for building your own software against their libraries.  They usually consist of the headers and shared libraries.

---

### Post by geek_Man on 2007-01-05
Thanks, man!

---

### Post by Electronic Yoga on 2013-01-21
Hi!  Don't mind that you had GTK installed already geek_man. I found tremendous help in this thread, as I was going through some of the same pains as you, while NOT having GTK installed at all. Thanks hod139, for your help, its people like you that makes this forum valuable.

Im stoked at the difficulty of installing these much needed programs. Its amazing, just amazing...

Sometimes I think the Ubuntu architects, are intentionally hurting me. Like its a personal thing or something :) Then I discover, that nearly everybody has had the same problems as me. Its just that nobody cares fixing them in the first place...

---

