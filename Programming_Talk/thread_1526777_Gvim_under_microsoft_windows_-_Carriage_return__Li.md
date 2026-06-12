---
title: "Gvim under microsoft windows - Carriage return / Line Feed"
date: 2010-07-08
forum: Programming Talk
---

### Post by adit on 2010-07-08
I am using gvim under microsoft windows in my office and under ubuntu in my home.  When I use gvim under microsoft windows, it adds Carriage Return / Line Feed at the end of each line.  This is the default configuration.  I want gvim to insert only linefeed characters (linux line ending) even if I am using it under windows.
There are tools to strip the extra CR characters.  But I don't want to run these programs every time.  I want gvim to start automatically in linux line ending mode (by modifying _vimrc file).  How to do that?

---

### Post by trent.josephsen on 2010-07-08
set fileformat=unix

---

