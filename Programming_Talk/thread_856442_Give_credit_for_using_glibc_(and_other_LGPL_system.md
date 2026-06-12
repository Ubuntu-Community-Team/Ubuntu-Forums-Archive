---
title: "Give credit for using glibc (and other LGPL system libs)"
date: 2008-07-11
forum: Programming Talk
---

### Post by nvteighen on 2008-07-11
Hi everyone!

As you all know, glibc is licensed under LGPLv2.1+. So, my question is: if I distribute my program in binary form, dynamically linked to glibc, but not redistributing the library itself, should I still give credit or not?

```

(LGPL-2.1 Section 6 Paragraph 1)

You must give prominent notice with each copy of the work that the
Library is used in it and that the Library and its use are covered by
this License.  You must supply a copy of this License.  If the work
during execution displays copyright notices, you must include the
copyright notice for the Library among them, as well as a reference
directing the user to the copy of this License.  Also, you must do one
of these things:

```

LGPL-3 requires the same in Sections 3a, 4a & 5a for each distribution case.

But, I don't see any program that does such a thing! Take nano or even GNU utilities... Nobody mentions the Standard Library, but they do give credit to other libs. Is this because glibc is a "System Library" (as defined in GPL and LGPL)?? But "System Library" is related to what source code you have to redistribute, nothing else... or at least that's what I understand!

Thanks! Surely I'm misreading something; it can't be possible that the whole FOSS community is not complying the LGPL...

EDIT: Of course, giving credit just to be sure wouldn't harm...

---

### Post by kknd on 2008-07-11
Good question. I've never readed this paragraphs before. The proprietary applications that I know and use LGPL libraries don't even mention the libraries that they are using.

I'm confused now.

---

### Post by nvteighen on 2008-07-11
But (L)GPL'ed programms don't either.

GNU nano doesn't mention neither the GNU C Standard Library nor ncurses in /usr/share/doc/nano/copyright, where usually this kind of information is placed. (compare with /usr/share/doc/coreutils/copyright, for example).

GTK+ applications usually don't credit GTK+...

Firefox credits people that don't want credit. (type about:license#optional-notices)

---

