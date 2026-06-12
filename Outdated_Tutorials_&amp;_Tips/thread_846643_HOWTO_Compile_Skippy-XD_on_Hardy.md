---
title: "HOWTO: Compile Skippy-XD on Hardy"
date: 2008-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2008-07-01
Skippy-XD is "best described as a full-screen task-switcher for X11." It is similar to Apple's Expose and the Scale plugin for Compiz Fusion. It privides live views of your windows (such as video playback).

I had a big issue when compiling it, though: I didn't want Xinerama support. If you need it, then just install the dependencies, make, and make install. If you don't, I will show you how to disable it before compiling.



1. DEPENDENCIES:

Here is what you need to install before compiling skippy:

```
sudo apt-get install libxft-dev libxrender-dev libxcomposite-dev libxdamage-dev libxfixes-dev libxmu-dev
```Depending what you already have installed, you may or may not need to install other packages.



2. SOURCE:

You can get the skippy-xd source package here: [http://thegraveyard.org/files/skippy-xd-0.5.0.tar.bz2](http://thegraveyard.org/files/skippy-xd-0.5.0.tar.bz2)

Extract it and open the directory containing the source files.



3. PATCH FILES:

This step is ONLY to compile skippy-xd without Xinerama support. If you want Xinerama support, skip this step.You need to edit the following files:

mainwin.c
mainwin.h
Makefile

If you don't want to edit them yourself, I have posted the patched files at the bottom. Also, try using them if you get errors with step 4.

Open mainwin.c with a text editor. Create a new line between line after line 69 and paste this in line 70:
```
     int event_base;
``` Save the file.

Open mainwin.h with a text editor. Scroll down to line 58. Replace this section:

```
#ifdef XINERAMA
    int xin_screens;
    int event_base;
    XineramaScreenInfo *xin_info, *xin_active;
#endif  /* XINERAMA */
```with this:
```
/* #ifdef XINERAMA
    int xin_screens;
    int event_base;
    XineramaScreenInfo *xin_info, *xin_active;
#endif  XINERAMA */ 
```(You are just commenting this section out.) Save the file.

Open Makefile with a text editor. Put a # in front of lines 13 and 14 to comment them out. Save and exit.



4. COMPILE

Open a terminal and 'cd' to the folder containing the source files. Type 'make' to build skippy-xd. If you get any errors, do not proceed to the next step. If you can't resolve the errors, post them here and I will try to help.



5. INSTALL

If you didn't get any error messages with step 4, type 'sudo make install' to install skippy-xd. Now go back the the folder containing the source code. Copy the file 'skippy-xd.rc-default' to your home folder and rename it to '.skippy-xd.rc'. This file contains skippy-xd's settings. You may edit it to your liking. You can then launch skippy with this command:
```
skippy-xd
```

6. CONFIGURATION

The file "skippy-xd.rc-default" in the source tarball is the default config file. Copy it to ~/.skippy-xd.rc and edit to your liking. The options are explained in the file. 

7. FILES

Here are the patched files, in case you need them.

mainwin.c:
```
/* Skippy - Seduces Kids Into Perversion
 *
 * Copyright (C) 2004 Hyriand <hyriand@thegraveyard.org>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
 */

#include "skippy.h"

/* from 'uncover': */
static Visual *
find_argb_visual (Display *dpy, int scr)
{
    XVisualInfo        *xvi;
    XVisualInfo        template;
    int            nvi;
    int            i;
    XRenderPictFormat    *format;
    Visual        *visual;
    
    template.screen = scr;
    template.depth = 32;
    template.class = TrueColor;
    xvi = XGetVisualInfo (dpy, 
              VisualScreenMask |
              VisualDepthMask |
              VisualClassMask,
              &template,
              &nvi);
    if (!xvi)
    return 0;
    visual = 0;
    for (i = 0; i < nvi; i++)
    {
    format = XRenderFindVisualFormat (dpy, xvi[i].visual);
    if (format->type == PictTypeDirect && format->direct.alphaMask)
    {
        visual = xvi[i].visual;
        break;
    }
    }

    XFree (xvi);
    return visual;
}

MainWin *
mainwin_create(Display *dpy, dlist *config)
{
    const char *tmp;
    double tmp_d;
    XColor exact_color;
    XSetWindowAttributes wattr;
    XWindowAttributes rootattr;
    XRenderPictureAttributes pa;
    XRenderColor clear;
    int error_base;
    int event_base;
#ifdef XINERAMA
    int event_base;
#endif /* XINERAMA */
    
    MainWin *mw = (MainWin *)malloc(sizeof(MainWin));
    
    mw->dpy = dpy;
    mw->screen = DefaultScreen(dpy);
    mw->root = RootWindow(dpy, mw->screen);
    mw->lazy_trans = (strcasecmp(config_get(config, "general", "lazyTrans", "false"), "true") == 0) ? True : False;
    if(mw->lazy_trans)
    {
        mw->depth  = 32;
        mw->visual = find_argb_visual(dpy, DefaultScreen(dpy));
        if(! mw->visual)
        {
            fprintf(stderr, "WARNING: Couldn't find argb visual, disabling lazy transparency.\n");
            mw->lazy_trans = False;
        }
    }
    if(! mw->lazy_trans)
    {
        mw->depth = DefaultDepth(dpy, mw->screen);
        mw->visual = DefaultVisual(dpy, mw->screen);
    }
    mw->colormap = XCreateColormap(dpy, mw->root, mw->visual, AllocNone);
    mw->bg_pixmap = None;
    mw->background = None;
    mw->format = XRenderFindVisualFormat(dpy, mw->visual);
#ifdef XINERAMA
    mw->xin_info = mw->xin_active = 0;
    mw->xin_screens = 0;
#endif /* XINERAMA */
    
    mw->pressed = mw->focus = 0;
    mw->tooltip = 0;
    mw->cod = 0;
    mw->key_up = XKeysymToKeycode(dpy, XK_Up);
    mw->key_down = XKeysymToKeycode(dpy, XK_Down);
    mw->key_left = XKeysymToKeycode(dpy, XK_Left);
    mw->key_right = XKeysymToKeycode(dpy, XK_Right);
    mw->key_enter = XKeysymToKeycode(dpy, XK_Return);
    mw->key_space = XKeysymToKeycode(dpy, XK_space);
    mw->key_escape = XKeysymToKeycode(dpy, XK_Escape);
    mw->key_q = XKeysymToKeycode(dpy, XK_q);
    
    XGetWindowAttributes(dpy, mw->root, &rootattr);
    mw->x = mw->y = 0;
    mw->width = rootattr.width;
    mw->height = rootattr.height;
    
    wattr.colormap = mw->colormap;
    wattr.background_pixel = wattr.border_pixel = 0;
    wattr.event_mask = VisibilityChangeMask |
                       ButtonReleaseMask;
    
    mw->window = XCreateWindow(dpy, mw->root, 0, 0, mw->width, mw->height, 0,
                               mw->depth, InputOutput, mw->visual,
                               CWBackPixel|CWBorderPixel|CWColormap|CWEventMask, &wattr);
    if(mw->window == None) {
        free(mw);
        return 0;
    }
    
#ifdef XINERAMA
# ifdef DEBUG
    fprintf(stderr, "--> checking for Xinerama extension... ");
# endif /* DEBUG */
    if(XineramaQueryExtension(dpy, &event_base, &error_base))
    {
# ifdef DEBUG
        fprintf(stderr, "yes\n--> checking if Xinerama is enabled... ");
# endif /* DEBUG */
        if(XineramaIsActive(dpy))
        {
# ifdef DEBUG
            fprintf(stderr, "yes\n--> fetching Xinerama info... ");
# endif /* DEBUG */
            mw->xin_info = XineramaQueryScreens(mw->dpy, &mw->xin_screens);
# ifdef DEBUG            
        fprintf(stderr, "done (%i screens)\n", mw->xin_screens);
# endif /* DEBUG */
        }
# ifdef DEBUG
        else
            fprintf(stderr, "no\n");
# endif /* DEBUG */
    }
# ifdef DEBUG
    else
        fprintf(stderr, "no\n");
# endif /* DEBUG */
#endif /* XINERAMA */
    
    if(! XDamageQueryExtension (dpy, &mw->damage_event_base, &error_base))
    {
        fprintf(stderr, "FATAL: XDamage extension not found.\n");
        exit(1);
    }
    
    if(! XCompositeQueryExtension(dpy, &event_base, &error_base))
    {
        fprintf(stderr, "FATAL: XComposite extension not found.\n");
        exit(1);
    } 
    
    if(! XRenderQueryExtension(dpy, &event_base, &error_base))
    {
        fprintf(stderr, "FATAL: XRender extension not found.\n");
        exit(1);
    }
    
    if(! XFixesQueryExtension(dpy, &event_base, &error_base))
    {
        fprintf(stderr, "FATAL: XFixes extension not found.\n");
        exit(1);
    }
    
    XCompositeRedirectSubwindows (mw->dpy, mw->root, CompositeRedirectAutomatic);
    
    tmp_d = strtod(config_get(config, "general", "updateFreq", "10.0"), 0);
    if(tmp_d != 0.0)
        mw->poll_time = (1.0 / tmp_d) * 1000.0;
    else
        mw->poll_time = 0;
    
    tmp = config_get(config, "normal", "tint", "black");
    if(! XParseColor(mw->dpy, mw->colormap, tmp, &exact_color))
    {
        fprintf(stderr, "Couldn't look up color '%s', reverting to black", tmp);
        mw->normalTint.red = mw->normalTint.green = mw->normalTint.blue = 0;
    }
    else
    {
        mw->normalTint.red = exact_color.red;
        mw->normalTint.green = exact_color.green;
        mw->normalTint.blue = exact_color.blue;
    }
    mw->normalTint.alpha = MAX(0, MIN(strtol(config_get(config, "normal", "tintOpacity", "0"), 0, 0) * 256, 65535));
    
    tmp = config_get(config, "highlight", "tint", "#101020");
    if(! XParseColor(mw->dpy, mw->colormap, tmp, &exact_color))
    {
        fprintf(stderr, "Couldn't look up color '%s', reverting to #101020", tmp);
        mw->highlightTint.red = mw->highlightTint.green = 0x10;
        mw->highlightTint.blue = 0x20;
    }
    else
    {
        mw->highlightTint.red = exact_color.red;
        mw->highlightTint.green = exact_color.green;
        mw->highlightTint.blue = exact_color.blue;
    }
    mw->highlightTint.alpha = MAX(0, MIN(strtol(config_get(config, "highlight", "tintOpacity", "64"), 0, 0) * 256, 65535));
    
    pa.repeat = True;
    clear.alpha = MAX(0, MIN(strtol(config_get(config, "normal", "opacity", "200"), 0, 10) * 256, 65535));
    mw->normalPixmap = XCreatePixmap(mw->dpy, mw->window, 1, 1, 8);
    mw->normalPicture = XRenderCreatePicture(mw->dpy, mw->normalPixmap, XRenderFindStandardFormat(mw->dpy, PictStandardA8), CPRepeat, &pa);
    XRenderFillRectangle(mw->dpy, PictOpSrc, mw->normalPicture, &clear, 0, 0, 1, 1);
    
    clear.alpha = MAX(0, MIN(strtol(config_get(config, "highlight", "opacity", "255"), 0, 10) * 256, 65535));
    mw->highlightPixmap = XCreatePixmap(mw->dpy, mw->window, 1, 1, 8);
    mw->highlightPicture = XRenderCreatePicture(mw->dpy, mw->highlightPixmap, XRenderFindStandardFormat(mw->dpy, PictStandardA8), CPRepeat, &pa);
    XRenderFillRectangle(mw->dpy, PictOpSrc, mw->highlightPicture, &clear, 0, 0, 1, 1);
    
    tmp = config_get(config, "general", "distance", "50");
    mw->distance = MAX(1, strtol(tmp, 0, 10));
    
    if(! strcasecmp(config_get(config, "tooltip", "show", "true"), "true"))
        mw->tooltip = tooltip_create(mw, config);
    
    return mw;
}

void
mainwin_update_background(MainWin *mw)
{
    Pixmap root = wm_get_root_pmap(mw->dpy);
    XRenderColor black = { 0, 0, 0, 65535};
    XRenderPictureAttributes pa;
    
    if(mw->bg_pixmap)
        XFreePixmap(mw->dpy, mw->bg_pixmap);
    if(mw->background)
        XRenderFreePicture(mw->dpy, mw->background);
    
    mw->bg_pixmap = XCreatePixmap(mw->dpy, mw->window, mw->width, mw->height, mw->depth);
    pa.repeat = True;
    mw->background = XRenderCreatePicture(mw->dpy, mw->bg_pixmap, mw->format, CPRepeat, &pa);
    
    if(root == None)
        XRenderFillRectangle(mw->dpy, PictOpSrc, mw->background, &black, 0, 0, mw->width, mw->height);
    else
    {
        Picture from = XRenderCreatePicture(mw->dpy, root, XRenderFindVisualFormat(mw->dpy, DefaultVisual(mw->dpy, mw->screen)), 0, 0);
        XRenderComposite(mw->dpy, PictOpSrc, from, None, mw->background, mw->x, mw->y, 0, 0, 0, 0, mw->width, mw->height);
        XRenderFreePicture(mw->dpy, from);
    }
    
    XSetWindowBackgroundPixmap(mw->dpy, mw->window, mw->bg_pixmap);
    XClearWindow(mw->dpy, mw->window);
}

void
mainwin_update(MainWin *mw)
{
#ifdef XINERAMA
    XineramaScreenInfo *iter;
    int i;
    Window dummy_w;
    int root_x, root_y, dummy_i;
    unsigned int dummy_u;
    
    if(! mw->xin_info || ! mw->xin_screens)
    {
        mainwin_update_background(mw);
        return;
    }
    
# ifdef DEBUG
    fprintf(stderr, "--> querying pointer... ");
# endif /* DEBUG */
    XQueryPointer(mw->dpy, mw->root, &dummy_w, &dummy_w, &root_x, &root_y, &dummy_i, &dummy_i, &dummy_u);
# ifdef DEBUG    
    fprintf(stderr, "+%i+%i\n", root_x, root_y);
    
    fprintf(stderr, "--> figuring out which screen we're on... ");
# endif /* DEBUG */
    iter = mw->xin_info;
    for(i = 0; i < mw->xin_screens; ++i)
    {
        if(root_x >= iter->x_org && root_x < iter->x_org + iter->width &&
           root_y >= iter->y_org && root_y < iter->y_org + iter->height)
        {
# ifdef DEBUG
            fprintf(stderr, "screen %i %ix%i+%i+%i\n", iter->screen_number, iter->width, iter->height, iter->x_org, iter->y_org);
# endif /* DEBUG */
            break;
        }
        iter++;
    }
    if(i == mw->xin_screens)
    {
# ifdef DEBUG 
        fprintf(stderr, "unknown\n");
# endif /* DEBUG */
        return;
    }
    mw->x = iter->x_org;
    mw->y = iter->y_org;
    mw->width = iter->width;
    mw->height = iter->height;
    XMoveResizeWindow(mw->dpy, mw->window, iter->x_org, iter->y_org, mw->width, mw->height);
    mw->xin_active = iter;
#endif /* XINERAMA */
    mainwin_update_background(mw);
}

void
mainwin_map(MainWin *mw)
{
    wm_set_fullscreen(mw->dpy, mw->window, mw->x, mw->y, mw->width, mw->height);
    mw->pressed = 0;
    XMapWindow(mw->dpy, mw->window);
    XRaiseWindow(mw->dpy, mw->window);
}

void
mainwin_unmap(MainWin *mw)
{
    if(mw->tooltip)
        tooltip_unmap(mw->tooltip);
    if(mw->bg_pixmap)
    {
        XFreePixmap(mw->dpy, mw->bg_pixmap);
        mw->bg_pixmap = None;
    }
    XUnmapWindow(mw->dpy, mw->window);
}

void
mainwin_destroy(MainWin *mw)
{
    if(mw->tooltip)
        tooltip_destroy(mw->tooltip);
    
    if(mw->background != None)
        XRenderFreePicture(mw->dpy, mw->background);
    
    if(mw->bg_pixmap != None)
        XFreePixmap(mw->dpy, mw->bg_pixmap);
    
    if(mw->normalPicture != None)
        XRenderFreePicture(mw->dpy, mw->normalPicture);
    
    if(mw->highlightPicture != None)
        XRenderFreePicture(mw->dpy, mw->highlightPicture);
    
    if(mw->normalPixmap != None)
        XFreePixmap(mw->dpy, mw->normalPixmap);
    
    if(mw->highlightPixmap != None)
        XFreePixmap(mw->dpy, mw->highlightPixmap);
    
    XDestroyWindow(mw->dpy, mw->window);
    
#ifdef XINERAMA
    if(mw->xin_info)
        XFree(mw->xin_info);
#endif /* XINERAMA */
    
    free(mw);
}

void
mainwin_transform(MainWin *mw, float f)
{
    mw->transform.matrix[0][0] = XDoubleToFixed(1.0 / f);
    mw->transform.matrix[0][1] = 0.0;
    mw->transform.matrix[0][2] = 0.0;
    mw->transform.matrix[1][0] = 0.0;
    mw->transform.matrix[1][1] = XDoubleToFixed(1.0 / f);
    mw->transform.matrix[1][2] = 0.0;
    mw->transform.matrix[2][0] = 0.0;
    mw->transform.matrix[2][1] = 0.0;
    mw->transform.matrix[2][2] = XDoubleToFixed(1.0);
}

int
mainwin_handle(MainWin *mw, XEvent *ev)
{
    switch(ev->type)
    {
    case KeyPress:
        if(ev->xkey.keycode == XKeysymToKeycode(mw->dpy, XK_q))
            return 2;
        break;
    case ButtonRelease:
        return 1;
        break;
    case VisibilityNotify:
        if(ev->xvisibility.state && mw->focus)
        {
            XSetInputFocus(mw->dpy, mw->focus->mini.window, RevertToParent, CurrentTime);
            mw->focus = 0;
        }
        break;
    default:
        ;
    }
    return 0;
}
```mainwin.h:
```
/* Skippy - Seduces Kids Into Perversion
 *
 * Copyright (C) 2004 Hyriand <hyriand@thegraveyard.org>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
 */

#ifndef SKIPPY_MAINWIN_H
#define SKIPPY_MAINWIN_H

struct _Tooltip;

struct _MainWin
{
    Display *dpy;
    int screen;
    Visual *visual;
    Colormap colormap;
    int depth;
    Window root;
    int damage_event_base;
    
    int poll_time;
    Bool lazy_trans;

    int event_base;
    
    Window window;
    Picture background;
    Pixmap bg_pixmap;
    int x, y;
    unsigned int width, height, distance;
    XRenderPictFormat *format;
    XTransform transform;
    
    XRenderColor normalTint, highlightTint;
    Pixmap normalPixmap, highlightPixmap;
    Picture normalPicture, highlightPicture;
    
    ClientWin *pressed, *focus;
    dlist *cod;
    struct _Tooltip *tooltip;
    
    KeyCode key_act, key_up, key_down, key_left, key_right, key_enter, key_space, key_q, key_escape;
    
/* #ifdef XINERAMA
    int xin_screens;
    int event_base;
    XineramaScreenInfo *xin_info, *xin_active;
#endif  XINERAMA */
};
typedef struct _MainWin MainWin;

MainWin *mainwin_create(Display *, dlist *config);
void mainwin_destroy(MainWin *);
void mainwin_map(MainWin *);
void mainwin_unmap(MainWin *);
int mainwin_handle(MainWin *, XEvent *);
void mainwin_update_background(MainWin *mw);
void mainwin_update(MainWin *mw);
void mainwin_transform(MainWin *mw, float f);

#endif /* SKIPPY_MAINWIN_H */
```Makefile:
```
PREFIX = /usr/local
BINDIR = ${PREFIX}/bin

X11PREFIX = /usr/X11R6

CFLAGS += -I${X11PREFIX}/include `pkg-config xft xrender xcomposite xdamage xfixes --cflags` -g -pedantic -Wall
LDFLAGS += -L${X11PREFIX}/lib -lX11 -lm `pkg-config xft xrender xcomposite xdamage xfixes --libs`

# Disable post-processing effects
# CFLAGS += -DNOEFFECTS

# Comment these out to disable Xinerama support
#CFLAGS += -DXINERAMA
#LDFLAGS += -lXext -lXinerama

# Uncomment this for Xinerama debugging
#CFLAGS += -DDEBUG

EXESUFFIX =

SOURCES = skippy.c wm.c dlist.c mainwin.c clientwin.c layout.c focus.c config.c tooltip.c
HEADERS = skippy.h wm.h dlist.h mainwin.h clientwin.h layout.h focus.h config.h tooltip.h

all: skippy-xd${EXESUFFIX}

skippy-xd${EXESUFFIX}: Makefile ${SOURCES} ${HEADERS}
    gcc ${CFLAGS} -o skippy-xd${EXESUFFIX} ${SOURCES} ${LDFLAGS}

clean:
    rm -f skippy-xd${EXESUFFIX}

install:
    install -d ${DESTDIR}${BINDIR}
    install -m 755 skippy-xd$(EXESUFFIX) ${DESTDIR}${BINDIR}/skippy-xd${EXESUFFIX}
```

---

### Post by marktechey on 2008-07-16
If you get an error output like this:

X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  74
  Current serial number in output stream:  74

You already have a command assigned to the default key (F11). To fix this edit ~/.skippy-xd.rc and change F11 to another key (I used F7)

---

### Post by matija_kc on 2008-07-16
this looks like grat app but on my fluxbox it is very slow. after pressing key seconds will pass untill screens are shown. how can i speed this up? computer: gf6600gt ant athlon64 3000 + 1gb ddr. ubuntu hardy 32bit

---

### Post by dbbolton on 2008-07-16
> **matija_kc said:**
> this looks like grat app but on my fluxbox it is very slow. after pressing key seconds will pass untill screens are shown. how can i speed this up? computer: gf6600gt ant athlon64 3000 + 1gb ddr. ubuntu hardy 32bit
You could try regular skippy. It might be a little faster.

[http://ubuntuforums.org/showthread.php?t=30510](http://ubuntuforums.org/showthread.php?t=30510)

---

### Post by matija_kc on 2008-07-16
i found solution. skippy-xd needs xcompmgr to work well. but i don't really like xompmgr so.. no skippy for me. thanks anyway;)

---

### Post by dbbolton on 2008-07-16
> **matija_kc said:**
> i found solution. skippy-xd needs xcompmgr to work well. but i don't really like xompmgr so.. no skippy for me. thanks anyway;)
Again, I don't think regular Skippy requires a composite manager. If you want to give it a try, I posted a link for the howto in my previous post.

---

### Post by dbbolton on 2009-02-09
> **marktechey said:**
> If you get an error output like this:

X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  74
  Current serial number in output stream:  74

You already have a command assigned to the default key (F11). To fix this edit ~/.skippy-xd.rc and change F11 to another key (I used F7)
I had to end up using "Scroll_Lock"

---

### Post by hemantborole on 2009-03-04
I compiled skippy with xinerma support i.e. did not change anything in the source code. I am using 2 virtual desktops ( or heads ). My hot key is F7. But Shift-F7 does not show windows on all the heads.
I have showall = true in the ~/.skippy-xd.rc. Any idea how to fix this.
I am using fluxbox on ubuntu.

---

### Post by dbbolton on 2009-03-04
> **hemantborole said:**
> I compiled skippy with xinerma support i.e. did not change anything in the source code. I am using 2 virtual desktops ( or heads ). My hot key is F7. But Shift-F7 does not show windows on all the heads.
I have showall = true in the ~/.skippy-xd.rc. Any idea how to fix this.
I am using fluxbox on ubuntu.
Do you get any error output when you launch skippy-xd from a terminal then press F7?

---

### Post by binbash on 2009-03-05
Works fine here, thanks

---

### Post by dilidon on 2009-08-20
> **binbash said:**
> Works fine here, thanks

Same here. These instructions did the trick. Thanks.
I was always able to compile skippy but never skippy-xd. The rewrite of those files helped. Other sources only suggested modifying the Makefile, which was only useful for the regular Skippy.
PS. For a neat trick regarding invoking skippy or skippy-xd by using the mouse in any corner of the screen see [http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/](http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/)
Just started using the solution on my #!Crunchbang linux (based on Ubuntu) on Aspire One.

---

