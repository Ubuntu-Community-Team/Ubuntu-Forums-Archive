---
title: "How do I know if its DirectX compatable?"
date: 2008-08-09
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-08-09
hi

so im learning basic C++ DirectX programming from a book and ive had it with my microsoft compiler/IDE (what would you expect)...

but i read that not all compilers are compatable with DirectX and i need to know how i would test this/find out

---

### Post by geenux on 2008-08-09
DirectX is not made for GNU/Linux. It's only available in Windows.
So you can't make a directX project on Linux. Look at opengl, which is multi-platform.

---

### Post by jimi_hendrix on 2008-08-09
> **geenux said:**
> DirectX is not made for GNU/Linux. It's only available in Windows.


which is the reason i am not asking for an IDE but a way to know...is there a way i can tell or do i simply have to trial and error until i found out

---

### Post by hessiess on 2008-08-09
dont bother with directX, learn OpenGL then you can run your programs on practily any platform/OS.

---

### Post by LaRoza on 2008-08-09
> **jimi_hendrix said:**
> hi

so im learning basic C++ DirectX programming from a book and ive had it with my microsoft compiler/IDE (what would you expect)...

but i read that not all compilers are compatable with DirectX and i need to know how i would test this/find out
You are using a proprietary Microsoft Library so you have to use their compiler.

---

### Post by nrs on 2008-08-09
> **LaRoza said:**
> You are using a proprietary Microsoft Library so you have to use their compiler.
You have to use their platform. but I'm pretty sure you can use other compilers -- like MingW.I'm pretty sure I've done it, or at least compiled other Win32 apps with it.

---

### Post by nrs on 2008-08-09
> **jimi_hendrix said:**
> hi

so im learning basic C++ DirectX programming from a book and ive had it with my microsoft compiler/IDE (what would you expect)...

but i read that not all compilers are compatable with DirectX and i need to know how i would test this/find out

You download another compiler -- try MingW -- and try compiling/linking  it :-P You're absolutely screwed when it comes to non-Windows platforms though.

---

### Post by Ademan on 2008-08-09
Ok, well, the right way to go about things is to learn OpenGL.  However, there is a way to develop DirectX applications on linux, it's called winelib, and it's apparently pretty good.  *BUT* really, really, really, you should be learning OpenGL instead!

---

### Post by LaRoza on 2008-08-09
> **jimi_hendrix said:**
> but i read that not all compilers are compatable with DirectX and i need to know how i would test this/find out
Check the documentation for the compiler in question?

---

