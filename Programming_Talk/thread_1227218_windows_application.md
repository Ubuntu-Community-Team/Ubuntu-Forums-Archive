---
title: "windows application"
date: 2009-07-30
forum: Programming Talk
---

### Post by alimooghashang on 2009-07-30
i have written an application in windows with delphi
now i want to convert it and bring it into ubuntu
how can i do that?
is it possible?

---

### Post by JordyD on 2009-07-30
Yes. Figure out where any Windows-specific stuff is in your code and change it to either cross-platform or Linux-specific code.

If you don't think you have any Windows-specific code, then just bring it over to your Ubuntu machine and try to compile it (if that's what you do with Delphi). Figure out and fix any errors during compilation.

---

### Post by alimooghashang on 2009-08-01
> **JordyD said:**
> Yes. Figure out where any Windows-specific stuff is in your code and change it to either cross-platform or Linux-specific code.

If you don't think you have any Windows-specific code, then just bring it over to your Ubuntu machine and try to compile it (if that's what you do with Delphi). Figure out and fix any errors during compilation.
hi,
i'm not using special component of windows.
just Tbitmap, and Tbotton, Tlabel and...
are these supported in linux?

---

### Post by JordyD on 2009-08-01
> **alimooghashang said:**
> hi,
i'm not using special component of windows.
just Tbitmap, and Tbotton, Tlabel and...
are these supported in linux?

What is Tbitmap, Tbutton and Tlabel? What are these from?

---

### Post by wrtpeeps on 2009-08-01
They're delphi objects. GUI objects. 

Borland Delphi is along the same lines as Microsoft C#.

---

### Post by alimooghashang on 2009-08-01
> **JordyD said:**
> What is Tbitmap, Tbutton and Tlabel? What are these from?
these are in StdCtrls unit of delphi.



{*******************************************************}
{                                                       }
{       Borland Delphi Visual Component Library         }
{                                                       }
{  Copyright (c) 1995-2002 Borland Software Corporation }
{                                                       }
{*******************************************************}

unit StdCtrls;

---

### Post by JordyD on 2009-08-01
> **alimooghashang said:**
> these are in StdCtrls unit of delphi.



{*******************************************************}
{                                                       }
{       Borland Delphi Visual Component Library         }
{                                                       }
{  Copyright (c) 1995-2002 Borland Software Corporation }
{                                                       }
{*******************************************************}

unit StdCtrls;

Well, I don't use Delphi, but if they're part of Delphi itself, then it's probably portable to any platform supporting Delphi.

Just try to compile you program on Linux and see if it works.

---

### Post by wrtpeeps on 2009-08-01
Might work. Delphi is pish so wouldn't be surprised if they don't.

---

### Post by jero3n on 2009-08-01
As far as I know, Lazarus is the closest alternative of Delphi in Linux.

[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

I've never used it, so just give a try.

---

