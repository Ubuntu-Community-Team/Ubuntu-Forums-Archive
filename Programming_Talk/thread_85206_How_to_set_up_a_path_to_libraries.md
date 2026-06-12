---
title: "How to set up a path to libraries?"
date: 2005-11-02
forum: Programming Talk
---

### Post by Zingam on 2005-11-02
Hi,

I want to include libsdl, libglew and other libs in my application. I want to put them in a subdirectory. The reason to do this is because I don't want to force the user to install these libraries to run my application.

Any ideas how can I do that?

---

### Post by ngms27 on 2005-11-02
That depends on the Langauge you are using, but generally they will look in the directory where the app is launched from for missing dependancies.

JonnyT

---

### Post by toojays on 2005-11-02
<post removed due to  being redundant>

---

### Post by toojays on 2005-11-02
It's not clear to me what JonnyT's post is meaning.

Probably the easiest way to get the result you want is to link your application statically. If you don't want to do that (perhaps for licensing reasons), you can use the GNU linker's "rpath" argument. If that won't work (you don't know where the application will be installed), you will need to use dlopen.

---

### Post by Zingam on 2005-11-02
LD_LIBRARY_PATH

What about setting this variable? NWN uses it but I couldn't make it work for me?

---

### Post by toojays on 2005-11-02
Yeah, LD_LIBRARY_PATH should work as well.

---

