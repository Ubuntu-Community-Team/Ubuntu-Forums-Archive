---
title: "Problem using Mono, Cairo and Svg"
date: 2007-06-06
forum: Programming Talk
---

### Post by vloris on 2007-06-06
Hello all!

I'm not sure if anyone is able to help me here, but I will ask it anyway. Maybe someone can point me in the right direction.

My problem:
I'm experimenting in mono (using monodevelop, but problem exists too when using commandline gmcs compiler) with Cairo as graphics engine to render some graphics in a gnome application.
So far, so good. But, now, I would like to include some svg graphics in between the other things I draw.

In the mono documentation there is information about the class [Cairo.SvgSurface](http://www.go-mono.com/docs/monodoc.ashx?tlink=0@ecma%3a40%23SvgSurface%2f). That's perfect, exactly what I need. Only, I don't seem to have that functionality:
```
Blaat.cs(18,19): error CS0234: The type or namespace name `SvgSurface' does not exist in the namespace `Cairo'. Are you missing an assembly reference?

```

The documentation states you need at least cairo 1.2. Checking, I seem to have two cairo libraries for mono: libmono-cairo1.0-cil (1.0.5000.0) and libmono-cairo2.0-cil (2.0.0.0)
Both versions complain in the same way, class SvgSurface does not exist.

I'm pretty sure the cairo library installed on my system does have svg functionality, at least /usr/include/cairo-svg.h has a large number of functions.


**My question:** Is my assumption correct and is this a problem in the mono cairo bindings? Or is there something else I can do to load the correct version.
Or, is the correct version even available in ubuntu (feisty fawn)?

---

### Post by rekahsoft on 2007-06-06
when you compile do you pass the library to gmcs? i know for gtk-sharp you compile like so:```
gmcs file.cs -pkg:gtk-sharp-2.0
```...i asume it would be the same just with the cario lib package. I do not knot the name of the package but if i come across it i will let you know...hope this gets u going in the right direction.

---

### Post by PandaGoat on 2007-06-06
Mono uses assemblies.  In Monodevelop you have to right click on "References" in the project and add the assembly for Cairo.  I'm not sure how to do that using the command line though.

---

### Post by rekahsoft on 2007-06-06
lol sorry...i am not good with the terminology of C# yet...i am pretty new to it...but to use an assembly from terminal you would use the "-pkg:assembly-name"

---

### Post by PandaGoat on 2007-06-07
Oh, I thought that may be what that was for.  Yeah :p

---

### Post by vloris on 2007-06-07
Ok. Some more information. Cairo is working, only the SvgSurface stuff does not seem to be there, so I guess I'm using the wrong version.
I have this simple test-program:
```
using System;
using Cairo;

public class Blaat
{
    public static void Main() {
        Cairo.SvgSurface surface = null;
        Cairo.Context context = null;
    }
}

```

This is how I compile it:
```

vloris@ilias:~/Projects/Cairo2Blaat/Cairo2Blaat$ gmcs -nowarn:0219 -reference:Mono.Cairo Blaat.cs 
Blaat.cs(7,15): error CS0234: The type or namespace name `SvgSurface' does not exist in the namespace `Cairo'. Are you missing an assembly reference?
Compilation failed: 1 error(s), 0 warnings

```

If I comment out the line about SvgSurface, there are no errors. The Cairo namespace is found, and even the class Context therein. Just SvgSurface seems to be missing.  (The -nowarn:0219 parameter is to let gmcs shut up about variables being assigned but not being used)

The suggestion of using -pkg:<some packagename> only works with packages/assemblies that have an associated .pc file for pkgconfig. Indeed, gtk-sharp has one, but libmono-cairo2.0-cil has not.

---

