---
title: "Mono Cairo just don't work"
date: 2006-09-05
forum: Programming Talk
---

### Post by max littlemore on 2006-09-05
Has anyone got mono working, and in particular been able to get Cairo going?

I've been trying for a while now, and I'm getting a bit dispondant.

I want to write my own widgets and they have to be .net (available for MS, OSX and happy penguin ppl:)

The following line refuses to compile in monodevelop:

Cairo.Context g = Gdk.Context.CreateDrawable (win);

It complains about Context not being valid in Gdk, but according to all the mono docs i can find, and the examples, this code should work.

when I try compiling from the shell, I get:
Unhandled Exception: System.DllNotFoundException: libgdk-x11-2.0.so
But I have the said library. I've turned debug on for mcs and still found nothing useful.

The only reference to this problem I have found through google is someone having the same problem with breezy. I'm on Dapper, but if the same person (wmaxfield at gmail.com) solved the problem, can you please post the fix here - there was no resolution on the site I found.

If anyone else has been able to get a Cairo.Context working in Dapper using monodevelop, please help.

---

### Post by kikuman on 2006-12-02
Ok, read [http://www.mono-project.com/Drawing]("http://www.mono-project.com/Drawing")
e.g I just included :

[DllImport("libgdk-x11-2.0.so")]
internal static extern IntPtr gdk_cairo_create (IntPtr raw);
 
public static Cairo.Graphics CreateDrawable (Gdk.Drawable drawable)
{
    Cairo.Graphics g = new Cairo.Graphics (gdk_cairo_create (drawable.Handle));
    if (g == null) 
        throw new Exception ("Couldn't create Cairo Graphics!");
 
    return g;
}

In my class and it works, don't forget :
using System.Runtime.InteropServices;

I forgot and wondered , what wrong >.<

:-D

---

### Post by kikuman on 2006-12-02
Ok, found a neatier solution imo to get Cairo.Context:
Gdk.CairoHelper.Create
>.<

---

