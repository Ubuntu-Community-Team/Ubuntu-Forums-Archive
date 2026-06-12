---
title: "[SOLVED] Alphabetize Nautilus Bookmarks?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by safetycopy on 2008-07-29
Hi,

Is it possible to have Nautilus automatically alphabetise bookmarks? If that's not possible, how about changing the order manually?

---

### Post by philinux on 2008-07-29
Yes just go to your home folder or bookmarks.

Choose Bookmarks. Then select edit bookmarks.

You can then drag and drop the bookmarks to order them as you choose.

---

### Post by safetycopy on 2008-07-29
Ah, that's great - thanks!

---

### Post by halitech on 2008-07-29
you can also click bookmarks, then right click the list and select 'sort by name'

---

### Post by safetycopy on 2008-07-31
Hmmm... Whenever I right-click an item in my bookmarks list I get taken to the directory... Where should I be clicking 'bookmarks' to have the 'sort by name' option?

---

### Post by halitech on 2008-07-31
I usuaaly click right on a folder and it gives me a menu that has sort by name in it

---

### Post by philinux on 2008-07-31
> **halitech said:**
> I usuaaly click right on a folder and it gives me a menu that has sort by name in it

That only happens, for me, in firefox bookmarks not Places>Bookmarks.

---

### Post by halitech on 2008-07-31
d'oh, I was thinking firefox, not nautilus and I've never had enough bookmarks to worry about trying to organize my nautilus book marks

---

### Post by safetycopy on 2008-08-01
Okey doke - thanks for the input guys - I don't have tons of Bookmarks, so a manual sort is fine :-)

---

### Post by Brucevdk on 2008-09-26
One of these days Nautilus (see [LP Bug #35347](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/35347)) will implement perhaps the [Freedesktop.org menu spec](http://standards.freedesktop.org/menu-spec/latest/) (as used by the applications menu). Actually, let me clarify. One of these days the Nautilus bookmarks system will be more like Firefox's. Not that Firefox's is ideal or anything, but the current functionality of Nautilus's system is quite ridiculous (no hierachy, single file for storing bookmarks).

Don't interpret this as simply whining though, I'll probably end up coding this myself once I free up some time.

On-topic, since Nautilus uses the file ~/.gtk-bookmarks to store the bookmarks you can use a variety of tools to sort that file. The following should work:

```

sort ~/.gtk-bookmarks -o ~/.gtk-bookmarks

```

---

### Post by booksnmore4you on 2010-01-14
Thanks!

However, how does one get the places to restore for all accounts after they've been deleted?

---

