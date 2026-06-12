---
title: "Why is it so %#$&amp;! hard to compile anything with Qt4?"
date: 2008-11-16
forum: Programming Talk
---

### Post by Envergure on 2008-11-16
I know I have all the needed includes for Qt4 because i installed LMMS from source.  But how is it done???

Is there a way to just compile it with Geany (i.e. without using QMake)?

BTW it doesn't work with QMake anyway.

---

### Post by snova on 2008-11-16
I'm trying to stay patient...

How are you compiling it? The command line you're using? What kind of error are you getting?

---

### Post by drubin on 2008-11-17
Take a look at my sig for asking questions. Please try and be more specific it really helps us to understand what is going on in order to help you.

---

### Post by Envergure on 2008-11-17
OK, I'll have to applologise for this one:  First, I shouldn't have been trying to learn a new GUI framework late at night on a day that already just wouldn't end.  Secondly, it's good if you code and compile in the same folder.  And thirdly, whining is not a good way to make friends.

So once I compiled from the right directory it worked.  I now have the ability to spam myself with many little windows.  Yay!

It still bugs me having to use Qmake, though - especially because I always have things buried six directories deep and cd-ing all they way there is inconvinient.

I'll post back if I manage to compile anything directly from Geany.

---

### Post by scourge on 2008-11-17
> **Envergure said:**
> It still bugs me having to use Qmake, though - especially because I always have things buried six directories deep and cd-ing all they way there is inconvinient.

I think you're doing it wrong. The best place for the .pro file is in your project's root directory. You'll just have to use relative file paths in the project file, and you can build everything from the same directory.

---

### Post by nvteighen on 2008-11-18
There's a reason why this is so: because IIRC, Qt was developed in a time there was no STL in C++ so the Trolltech guys had to implement their own "STL" and therefore, to ease developer's life (well, that's what they probably thought... :p) they created QMake to not make people hassle with linking several libraries on their own... The issue is that there's a better STL and Qt still uses its own.

---

### Post by samjh on 2008-11-18
> **nvteighen said:**
> The issue is that there's a better STL and Qt still uses its own.

That's debatable.  The standard C++ STL is a bit limited.  Qt libraries are more powerful, even if C++ with Qt isn't "pure" C++. :p

I'd like to think of Qt as a platform more than just a library.  It's a platform for C++ development... arguably a very good one.

---

### Post by nvteighen on 2008-11-18
> **samjh said:**
> That's debatable.  The standard C++ STL is a bit limited.  Qt libraries are more powerful, even if C++ with Qt isn't "pure" C++. :p

I'd like to think of Qt as a platform more than just a library.  It's a platform for C++ development... arguably a very good one.
Ok, thanks... I don't know about the details, so maybe I spoke too much :p

---

