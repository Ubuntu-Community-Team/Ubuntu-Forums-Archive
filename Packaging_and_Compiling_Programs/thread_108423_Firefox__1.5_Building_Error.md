---
title: "Firefox  1.5 Building Error ?"
date: 2005-12-26
forum: Packaging and Compiling Programs
---

### Post by gtdj on 2005-12-26
Building Error after ```
[COLOR="Blue"]make -f client.mk build[/COLOR]
```

```
nsFontMetricsXft.cpp:(.text+0x1c7): undefined reference to `XftDefaultSubstitute'
nsFontMetricsXft.cpp:(.text+0x1f9): undefined reference to `XftFontOpenPattern'
nsFontMetricsXft.cpp:(.text+0x259): undefined reference to `XftTextExtents8'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::DrawUnknownGlyph(unsigned int, int, int, _XftColor*, _XftDraw*)':
nsFontMetricsXft.cpp:(.text+0x412): undefined reference to `XftDrawRect'
nsFontMetricsXft.cpp:(.text+0x437): undefined reference to `XftDrawRect'
nsFontMetricsXft.cpp:(.text+0x461): undefined reference to `XftDrawRect'
nsFontMetricsXft.cpp:(.text+0x48a): undefined reference to `XftDrawRect'
nsFontMetricsXft.cpp:(.text+0x4fa): undefined reference to `XftDrawString8'
nsFontMetricsXft.cpp:(.text+0x53b): undefined reference to `XftDrawString8'
nsFontMetricsXft.cpp:(.text+0x58b): undefined reference to `XftDrawString8'
nsFontMetricsXft.cpp:(.text+0x5ba): undefined reference to `XftDrawString8'
nsFontMetricsXft.cpp:(.text+0x5f4): undefined reference to `XftDrawString8'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o):nsFontMetricsXft.cpp:(.text+0x62d): more undefined references to `XftDrawString8' follow
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXft::~nsFontXft()':
nsFontMetricsXft.cpp:(.text+0x950): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXft::~nsFontXft()':
nsFontMetricsXft.cpp:(.text+0x9c0): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXft::~nsFontXft()':
nsFontMetricsXft.cpp:(.text+0xa31): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXft::GetXftFont()':
nsFontMetricsXft.cpp:(.text+0xac6): undefined reference to `XftFontOpenPattern'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXft::GetTextExtents32(unsigned int const*, unsigned int, _XGlyphInfo&)':
nsFontMetricsXft.cpp:(.text+0xb20): undefined reference to `XftTextExtents32'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXft::CharToGlyphIndex(unsigned int)':
nsFontMetricsXft.cpp:(.text+0xb48): undefined reference to `XftCharIndex'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXftCustom::~nsFontXftCustom()':
nsFontMetricsXft.cpp:(.text+0xc01): undefined reference to `XftUnlockFace'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXftCustom::~nsFontXftCustom()':
nsFontMetricsXft.cpp:(.text+0xc41): undefined reference to `XftUnlockFace'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXftCustom::~nsFontXftCustom()':
nsFontMetricsXft.cpp:(.text+0xc81): undefined reference to `XftUnlockFace'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXftCustom::CharToGlyphIndex(unsigned int)':
nsFontMetricsXft.cpp:(.text+0xdbd): undefined reference to `XftCharIndex'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXftCustom::SetFT_FaceCharmap()':
nsFontMetricsXft.cpp:(.text+0xde7): undefined reference to `XftLockFace'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsAutoDrawSpecBuffer::Flush()':
nsFontMetricsXft.cpp:(.text+0xe66): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0xeb1): undefined reference to `XftDrawGlyphFontSpec'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::GetWidth(char const*, unsigned int, int&, nsRenderingContextGTK*)':
nsFontMetricsXft.cpp:(.text+0xf07): undefined reference to `XftTextExtents8'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::SetupFCPattern()':
nsFontMetricsXft.cpp:(.text+0x12ff): undefined reference to `XftDefaultSubstitute'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::PrepareToDraw(nsRenderingContextGTK*, nsDrawingSurfaceGTK*, _XftDraw**, _XftColor&)':
nsFontMetricsXft.cpp:(.text+0x177e): undefined reference to `XftDrawSetClipRectangles'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXftCustom::GetTextExtents32(unsigned int const*, unsigned int, _XGlyphInfo&)':
nsFontMetricsXft.cpp:(.text+0x2711): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0x275a): undefined reference to `XftTextExtents32'
nsFontMetricsXft.cpp:(.text+0x27af): undefined reference to `XftLockFace'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXft::DrawStringSpec(unsigned int*, unsigned int, void*)':
nsFontMetricsXft.cpp:(.text+0x3458): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0x350d): undefined reference to `XftDrawGlyphFontSpec'
nsFontMetricsXft.cpp:(.text+0x3535): undefined reference to `XftGlyphExtents'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontXftCustom::DrawStringSpec(unsigned int*, unsigned int, void*)':
nsFontMetricsXft.cpp:(.text+0x3643): undefined reference to `XftLockFace'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsAutoDrawSpecBuffer::Draw(int, int, _XftFont*, unsigned int)':
nsFontMetricsXft.cpp:(.text+0x36c8): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0x3743): undefined reference to `XftDrawGlyphFontSpec'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::DrawString(char const*, unsigned int, int, int, int const*, nsRenderingContextGTK*, nsDrawingSurfaceGTK*)':
nsFontMetricsXft.cpp:(.text+0x4229): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0x427b): undefined reference to `XftDrawGlyphFontSpec'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::DrawString(unsigned short const*, unsigned int, int, int, int, int const*, nsRenderingContextGTK*, nsDrawingSurfaceGTK*)':
nsFontMetricsXft.cpp:(.text+0x460a): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0x465c): undefined reference to `XftDrawGlyphFontSpec'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::CacheFontMetrics()':
nsFontMetricsXft.cpp:(.text+0x489c): undefined reference to `XftLockFace'
nsFontMetricsXft.cpp:(.text+0x4d43): undefined reference to `XftUnlockFace'
nsFontMetricsXft.cpp:(.text+0x4e22): undefined reference to `XftTextExtents16'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::~nsFontMetricsXft()':
nsFontMetricsXft.cpp:(.text+0x526b): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::~nsFontMetricsXft()':
nsFontMetricsXft.cpp:(.text+0x53db): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::~nsFontMetricsXft()':
nsFontMetricsXft.cpp:(.text+0x554b): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::~nsDrawingSurfaceGTK()':
nsDrawingSurfaceGTK.cpp:(.text+0x53): undefined reference to `XftDrawDestroy'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::GetXftDraw()':
nsDrawingSurfaceGTK.cpp:(.text+0x3e3): undefined reference to `XftDrawCreate'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::~nsDrawingSurfaceGTK()':
nsDrawingSurfaceGTK.cpp:(.text+0x623): undefined reference to `XftDrawDestroy'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::~nsDrawingSurfaceGTK()':
nsDrawingSurfaceGTK.cpp:(.text+0x693): undefined reference to `XftDrawDestroy'
collect2: ld returned 1 exit status
make[4]: *** [firefox-bin] Error 1
make[4]: Leaving directory `/home/bpasu/makefirefox/mozilla/hui-opt-static/browser/app'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/bpasu/makefirefox/mozilla/hui-opt-static/browser'
make[2]: *** [tier_99] Error 2
make[2]: Leaving directory `/home/bpasu/makefirefox/mozilla/hui-opt-static'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/bpasu/makefirefox/mozilla/hui-opt-static'
make: *** [build] Error 2
```


This is my .mozconfig
```
. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/hui-opt-static
ac_add_options --enable-optimize=-O3
ac_add_options --disable-debug
ac_add_options --enable-static
ac_add_options --disable-shared

```

---

### Post by bdk6m2007 on 2007-08-27
I realize this is more than 2 1/2 years old, but did you by chance ever figure this out and what did you do?  I'm getting the same problem......

---

