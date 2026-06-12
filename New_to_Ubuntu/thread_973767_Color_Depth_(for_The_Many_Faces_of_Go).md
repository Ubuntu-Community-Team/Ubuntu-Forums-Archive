---
title: "Color Depth (for The Many Faces of Go)"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by DavidVS on 2008-11-07
I am trying to use The Many Faces of Go through Wine.

I also encounter a [problem]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1682") where the images for the stones have a "layer" behind them of a black square.  This is very ugly.

The program is known to do this if the color depth is set for 256 colors.  How do I set color depth in Wine?  I assumed I was at 16 bit or 32 bit colors by default.

Thanks!

---

### Post by saru411 on 2008-11-07
Hi!
     It's nice to see another Go player on the forums. I don't know the answer to your problem but I do think you could find more information at [http://www.winehq.org/](http://www.winehq.org/) or post on their forums. Hope you get it working.

---

### Post by Steve H on 2008-11-29
I'm having the same problem and tracked this script down:
```

diff --git a/dlls/winex11.drv/palette.c b/dlls/winex11.drv/palette.c
index bb6d493..8039bf3 100644
--- a/dlls/winex11.drv/palette.c
+++ b/dlls/winex11.drv/palette.c
@@ -48,6 +48,9 @@ WINE_DEFAULT_DEBUG_CHANNEL(palette);
  * http://premium.microsoft.com/msdn/library/techart/f30/f34/f40/d4d/sa942.htm
  */

+#undef MIN
+#define MIN(x, y) ( ((x)<(y))?(x):(y) )
+
 #define NB_RESERVED_COLORS     20   /* number of fixed colors in system palette */

 #define PC_SYS_USED            0x80 /* palentry is used (both system and logical) */
@@ -1223,6 +1226,37 @@ UINT X11DRV_GetSystemPaletteEntries( X11DRV_PDEVICE *physDev, UINT start,
UINT c
 {
     UINT i;

+    /*in non-palette mode report palette size of 256 and set reserved colors*/
+    if (X11DRV_PALETTE_PaletteFlags & X11DRV_PALETTE_VIRTUAL)
+    {
+        if (!entries) return 256;
+
+        if (start >= 256) return 0;
+        if (start + count >= 256) count = 256 - start;
+
+        if (start < NB_RESERVED_COLORS/2)
+        {
+            GetPaletteEntries( GetStockObject(DEFAULT_PALETTE), start,
+                MIN(NB_RESERVED_COLORS/2 - start, count), entries);
+        }
+
+        if (start >= 256 - NB_RESERVED_COLORS/2)
+        {
+            GetPaletteEntries( GetStockObject(DEFAULT_PALETTE),
+                NB_RESERVED_COLORS/2 + start - (256 - NB_RESERVED_COLORS/2),
+                count, entries);
+        }
+        else if (start + count > 256 - NB_RESERVED_COLORS/2)
+        {
+            GetPaletteEntries( GetStockObject(DEFAULT_PALETTE),
+                NB_RESERVED_COLORS/2,
+                start + count - (256 - NB_RESERVED_COLORS/2),
+                entries + (256 - NB_RESERVED_COLORS/2) - start);
+        }
+
+        return count;
+    }
+
     if (!entries) return palette_size;
     if (start >= palette_size) return 0;
     if (start + count >= palette_size) count = palette_size - start;


diff --git a/dlls/gdi32/tests/palette.c b/dlls/gdi32/tests/palette.c
index 40e6c7c..15fba1a 100644
--- a/dlls/gdi32/tests/palette.c
+++ b/dlls/gdi32/tests/palette.c
@@ -40,6 +40,31 @@ static const PALETTEENTRY logpalettedata[8] = {
     { 0x80, 0x90, 0xA0, PC_NOCOLLAPSE },
 };

+static const PALETTEENTRY static_colors[20] = {
+/* 0..9 */
+    { 0x00, 0x00, 0x00, 0 },
+    { 0x80, 0x00, 0x00, 0 },
+    { 0x00, 0x80, 0x00, 0 },
+    { 0x80, 0x80, 0x00, 0 },
+    { 0x00, 0x00, 0x80, 0 },
+    { 0x80, 0x00, 0x80, 0 },
+    { 0x00, 0x80, 0x80, 0 },
+    { 0xC0, 0xC0, 0xC0, 0 },
+    { 0xC0, 0xDC, 0xC0, 0 },
+    { 0xA6, 0xCA, 0xF0, 0 },
+/* 246..255 */
+    { 0xFF, 0xFB, 0xF0, 0 },
+    { 0xA0, 0xA0, 0xA4, 0 },
+    { 0x80, 0x80, 0x80, 0 },
+    { 0xFF, 0x00, 0x00, 0 },
+    { 0x00, 0xFF, 0x00, 0 },
+    { 0xFF, 0xFF, 0x00, 0 },
+    { 0x00, 0x00, 0xFF, 0 },
+    { 0xFF, 0x00, 0xFF, 0 },
+    { 0x00, 0xFF, 0xFF, 0 },
+    { 0xFF, 0xFF, 0xFF, 0 }
+    };
+
 static void test_DIB_PAL_COLORS(void) {
     HDC hdc = GetDC( NULL );
     HDC memhdc = CreateCompatibleDC( hdc );
@@ -51,6 +76,8 @@ static void test_DIB_PAL_COLORS(void) {
     PLOGPALETTE logpalette = (PLOGPALETTE)logpalettebuf;
     HPALETTE hpal, hpalOld;
     COLORREF setColor, chkColor, getColor;
+    UINT nentries;
+    PALETTEENTRY syspalentries[256];
     int i;

     /* Initalize the logical palette with a few colours */
@@ -117,6 +144,27 @@ static void test_DIB_PAL_COLORS(void) {
     SelectObject( memhdc, hbmpOld );
     DeleteObject( hbmp );
     DeleteDC( memhdc );
+
+    memset(syspalentries, 0x01, sizeof(syspalentries));
+    SetLastError(0);
+    nentries = GetSystemPaletteEntries(hdc, 0, 256, syspalentries);
+    /* According to MSDN, it is supposed to return number of copied
+       entries and zero return value indicates a failure; On Windows XP it
+       always returns 0, although it does fill entries; On Windows 98 it
+       correctly returns 256 in most graphics modes; It can also return 16 on
+       W98 - when called in 16 color / VGA mode */
+    ok( (nentries == 0 || nentries == 256 || nentries == 16) && GetLastError()==0,
+        "nentries=%u error=%d\n", nentries, GetLastError());
+    if (nentries == 16) skip("will not check reserved colors (VGA mode?)\n");
+    else {
+        /* Test if 20 static(reserved) colors are present */
+        ok( !memcmp(static_colors, syspalentries, sizeof(PALETTEENTRY) * 10),
+            "system palette low 10 static colors are wrong\n");
+        ok( !memcmp(static_colors + 10, syspalentries + 256 - 10,
+            sizeof(PALETTEENTRY) *10),
+            "system palette high 10 static colors are wrong\n");
+    }
+
     ReleaseDC( NULL, hdc );
 }
```

It was posted [here]("http://article.gmane.org/gmane.comp.emulators.wine.devel/54403)") Now I haven't run it yet as I don't know how to?!?!?!

I have no idea if it works but the forums on WINEHQ link to it as a workaround for the messed up transparency problems.

If you know how to run it let me know...I'll keep on hunting for another answer.

---

