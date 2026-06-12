---
title: "conky doesn't load lua background"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by editheraven on 2012-01-05
I have a lua call in my conky config file.nautilus

```
lua_load /home/editheraven/scripts/draw_bg.lua
lua_draw_hook_pre draw_bg
```

and my draw_bg is this

```
--[[
Background by londonali1010 (2009)
 
This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.
 
To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
    lua_load ~/scripts/draw_bg.lua
    lua_draw_hook_pre
 
Changelog:
+ v1.0 -- Original release (07.10.2009)
]]
 
-- Change these settings to affect your background.
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.
 
corner_r=0
 
-- Set the colour and transparency (alpha) of your background.
 
bg_colour=0x000000
bg_alpha=0.4
 
require 'cairo'
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function conky_draw_bg()
    if conky_window==nil then return end
    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)
 
    cairo_move_to(cr,corner_r,0)
    cairo_line_to(cr,w-corner_r,0)
    cairo_curve_to(cr,w,0,w,0,w,corner_r)
    cairo_line_to(cr,w,h-corner_r)
    cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
    cairo_line_to(cr,corner_r,h)
    cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
    cairo_line_to(cr,0,corner_r)
    cairo_curve_to(cr,0,0,0,0,corner_r,0)
    cairo_close_path(cr)
 
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
    cairo_fill(cr)
end
```

This worked fine until i started to get this error on libGL.so file

```
Conky: llua_load: error loading module 'cairo' from file '/usr/lib/conky/libcairo.so':
    /usr/lib/i386-linux-gnu/mesa/libGL.so.1: undefined symbol: xcb_glx_set_client_info_2arb

Conky: llua_do_call: function conky_draw_bg execution failed: attempt to call a nil value
```

I didn't removed any libraries lately, so what is the problem?

---

### Post by editheraven on 2012-01-05
Anyone?

---

### Post by Sector11 on 2012-01-21
> **editheraven said:**
> Anyone?

I don't use nautilus . Try asking in the [mega conky thread]("http://ubuntuforums.org/showthread.php?t=281865")!

---

