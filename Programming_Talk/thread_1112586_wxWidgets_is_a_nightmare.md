---
title: "wxWidgets is a nightmare"
date: 2009-03-31
forum: Programming Talk
---

### Post by yahn on 2009-03-31
My experience with Ubuntu has been relatively great for the past year or so.  In my opinion, development was actually easier on Ubuntu than on Windows.  However, wxWidgets is out of control.

I've been fooling around with wxWidgets for 3 straight days and I'm getting nowhere.  So, hopefully someone can help me out or I'm going to have to use a different library or something.

It all starts when I include <wx/wx.h>, which is technically <wx-2.8/wx/wx.h>.  I got an error about setup.h.  After hours of scratching my head, I finally (maybe) found out what to do with setup.h.  Then I find out that in defs.h I get the error that there is no target and I should compile with wx-config.  After a few more hours of scratching my head, I figure out what exactly that means.  So, I run wx-config --cppflags, get the flags and set them as linker information only to find that I'm still getting the same error and there are about 10,000 more pending.

Every other library I have ever used "just worked."  Maybe I'm spoiled; maybe I'm stupid; maybe something is wrong with my system, but I cannot figure this out without some help.

Can anyone please help?

Thank you

---

### Post by dwhitney67 on 2009-03-31
Since you know where the header files are located at, just indicate to gcc (or g++) this information using the -I (uppercase i) option.

```

gcc -I/usr/include/wx-2.8 file.c ...

```

Your source code should include wxWidget header file(s) such as:
```

#include <wx/wx.h>
...

```

I have never used wxWidgets; I presume there is a shared- or static-library that you must use to link your application.  If so, use the -l (lowercase el) option to specify the appropriate library.  For example, maybe -lwx.

---

### Post by yahn on 2009-03-31
Uh, I'm a little confused.  I'm using code::blocks and I don't think that will work.  The error telling me to use wx-config will still persist.

---

### Post by Jacks0n on 2009-03-31
Try using the Ubuntu guide on the wxWidgets site. That's the one I used a while back and it works fine. [http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu](http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu)

You need to make a symbolic link from /usr/include/wx to /usr/include/wx-2.8/wx, as it says on the guide. Or you could do... "#include <wx-2.8/wx/wx.h>"

Apparently with Code::Blocks you need to use `wx-config --cxxflags` in your build options, and `wx-config --libs` with your linker options. I'm guessing you didn't set the linker options.

[http://wiki.wxwidgets.org/Code::Blocks](http://wiki.wxwidgets.org/Code::Blocks)

Hope that helps!

Jackson

---

### Post by yahn on 2009-04-01
Thanks, I got it to work.

I wish that that would have shown up when I searched Google.

---

### Post by WitchCraft on 2009-04-01
> **Jacks0n said:**
> 
`wx-config --libs`



Warning: This is a very bad idea.

You should use
`wx-config --version=2.8 --static=no --cxxflags --libs`

If you don't, you will run into problems as soon as you have two different version of wxWidgets installed (e.g wxPython, which still uses 2.6).

---

### Post by Simian Man on 2009-04-01
If you think it's ad on Linux, Windows users actually have to compile wxWidgets manually to program with it!

---

### Post by WitchCraft on 2009-04-03
> **Simian Man said:**
> If you think it's ad on Linux, Windows users actually have to compile wxWidgets manually to program with it!
 
You also need to compile it on Linux if you want to have it link statically.

---

