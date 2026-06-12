---
title: "[Gtkmm] Get string width using Cairo and C++"
date: 2010-02-24
forum: Programming Talk
---

### Post by kahumba on 2010-02-24
Hi,
can anyone provide a snippet (in C++) please?
The official docs either provide Python or C versions and can't figure out how to translate that into C++ (using Gtkmm).

---

### Post by kahumba on 2010-02-24
Never mind, I finally figured out.

```

Cairo::RefPtr<Cairo::Context> cr = ...;
Glib::ustring str = "my string";
Cairo::TextExtents ext;
cr->get_text_extents(str, ext);
std::cout << "string width: " << ext.width << std::endl;

```

---

