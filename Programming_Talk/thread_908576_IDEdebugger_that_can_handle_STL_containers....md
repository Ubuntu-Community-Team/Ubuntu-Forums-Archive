---
title: "IDE/debugger that can handle STL containers..."
date: 2008-09-02
forum: Programming Talk
---

### Post by GenPFault on 2008-09-02
Is there an IDE or debugger that handles C++ STL containers in a sane manner? I've tried the following:

KDevelop
Eclipse
Netbeans
DDD
Kdbg
Insight
Nemiver
Code::Blocks

...but they all give me the same _M_impl (std::vector) or _M_dataplus (std::string) nonsense.

---

### Post by LaRoza on 2008-09-02
What debugger's have you used? As far as I can tell, you used the same on in all those IDE's.

---

### Post by GenPFault on 2008-09-02
> **LaRoza said:**
> What debugger**s** have you used? As far as I can tell, you used the same on**e** in all those IDE's.
Good point.  That should probably read 'GDB frontends' instead of 'IDEs or debuggers' :)

---

### Post by GenPFault on 2008-09-02
Looks like Xcode can sorta do it, at least for std::strings and simple std::vectors.  Stumbles on vector< vector<string> > though.  Also kinda a non-starter for Ubuntu.

So it's at least possible for a GDB frontend to do the right thing.

---

### Post by Zugzwang on 2008-09-03
> 
...but they all give me the same _M_impl (std::vector) or _M_dataplus (std::string) nonsense.

Note that that's not nonsense - It's the internal structure of the STL libraries. 

If you are fed-up with jumping into all these nested functions again and again, you might try [this script]("http://ubuntuforums.org/showpost.php?p=4368203&postcount=8") which you apply to your executable in the last step of building it. It will kill most of the debug symbols of these containers to allow debugging in a sane manner - But then the calls to STL libraries are simply not taken into account, which may or may not be what you want.

---

### Post by GenPFault on 2008-09-05
> **Zugzwang said:**
> Note that that's not nonsense - It's the internal structure of the STL libraries. 

If you are fed-up with jumping into all these nested functions again and again, you might try [this script]("http://ubuntuforums.org/showpost.php?p=4368203&postcount=8") which you apply to your executable in the last step of building it. It will kill most of the debug symbols of these containers to allow debugging in a sane manner - But then the calls to STL libraries are simply not taken into account, which may or may not be what you want.
I'll have to keep that in mind when it comes up; no progress on the structured display problem though :(

---

### Post by Zugzwang on 2008-09-05
> **GenPFault said:**
> I'll have to keep that in mind when it comes up; no progress on the structured display problem though :(

Ok, so this is what I've found. If you are using "GDB" or the more user-friendly "DDD", then you *can* at least look into the containers. But I doubt that it will work if you use my trick. More details are written [here]("http://sourceware.org/ml/gdb/2007-06/msg00136.html").

---

### Post by Hindol on 2012-07-08
This is kind of an old thread but Google still returns this page so I would like to add that,

Qt Creator supports such kind of debugging. Just try it. It lists only the members and not _M_impl and other nonsense.

---

