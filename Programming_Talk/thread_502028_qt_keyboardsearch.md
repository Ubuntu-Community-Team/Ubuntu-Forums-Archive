---
title: "qt keyboardsearch"
date: 2007-07-16
forum: Programming Talk
---

### Post by aquavitae on 2007-07-16
Does anyone know how to use the keyboardSearch function for QAbstractItemView in Qt?  The documentation doesn't say anything and I can't make much sense of the source.  What I want is a to do a vi type search - press '/' and type.  Is this even the right function to use - its the only one I can find that does any sort of search.

---

### Post by aquavitae on 2007-07-16
Just answered my own question - I am using the wrong function.  The one I want is QAbstractItemModel::match().  I just have to implement the '/' part myself... not too difficult!

---

