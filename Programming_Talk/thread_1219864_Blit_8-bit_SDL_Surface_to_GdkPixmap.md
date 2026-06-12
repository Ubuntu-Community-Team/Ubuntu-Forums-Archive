---
title: "Blit 8-bit SDL_Surface to GdkPixmap?"
date: 2009-07-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-07-22
My code does not work. It renders a constantly black surface. 24 and 32-bit surfaces work fine.

```

GdkRgbCmap palette = {
    (guint32 *)surf->format->palette->colors,
    (gint) surf->format->palette->ncolors
};

GdkGC *gc = gdk_gc_new( drawable );

gdk_draw_indexed_image( drawable, 0, 0, surf->w, surf->h, GDK_RGB_DITHER_NONE, (guchar*) surf->pixels, surf->pitch, &palette );

```

I looked up all this so you don't have to. Just tell me how to convert SDL_Palette to GdkRgbCmap.
```

typedef struct SDL_Surface {
    Uint32 flags;                           /* Read-only */
    SDL_PixelFormat *format;                /* Read-only */
    int w, h;                               /* Read-only */
    Uint16 pitch;                           /* Read-only */
    void *pixels;                           /* Read-write */
    SDL_Rect clip_rect;                     /* Read-only */
    int refcount;                           /* Read-mostly */

  /* This structure also contains private fields not shown here */
} SDL_Surface;

```
```

typedef struct {
  SDL_Palette *palette;
  Uint8  BitsPerPixel;
  Uint8  BytesPerPixel;
  Uint8  Rloss, Gloss, Bloss, Aloss;
  Uint8  Rshift, Gshift, Bshift, Ashift;
  Uint32 Rmask, Gmask, Bmask, Amask;
  Uint32 colorkey;
  Uint8  alpha;
} SDL_PixelFormat;

```
```

typedef struct{
  int ncolors;
  SDL_Color *colors;
} SDL_Palette;

```
```

typedef struct {
  guint32 colors[256];
  gint n_colors;
} GdkRgbCmap;

```
```

void                gdk_draw_indexed_image              (GdkDrawable *drawable,
                                                         GdkGC *gc,
                                                         gint x,
                                                         gint y,
                                                         gint width,
                                                         gint height,
                                                         GdkRgbDither dith,
                                                         const guchar *buf,
                                                         gint rowstride,
                                                         GdkRgbCmap *cmap);

```

---

### Post by crazyfuturamanoob on 2009-07-26
100% legit bump after 4 days.

---

