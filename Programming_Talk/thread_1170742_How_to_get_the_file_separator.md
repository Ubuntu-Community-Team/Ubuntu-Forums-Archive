---
title: "How to get the file separator"
date: 2009-05-26
forum: Programming Talk
---

### Post by cl333r on 2009-05-26
Hi,
Is it possible to get it through glib or Gtk? (or glibmm & gtkmm)

For example in Java I have java.io.File.separator which is "/" in Linux and "\" in windows.

---

### Post by crdlb on 2009-05-26
G_DIR_SEPARATOR or (G_DIR_SEPARATOR_S for a string version), but g_build_filename should be used whenever possible.

---

### Post by cl333r on 2009-05-26
Thanks! works indeed:

```

Glib::ustring sep = G_DIR_SEPARATOR_S;
cout << "separator: " << sep << endl;

```

> 
separator: /


---

### Post by DocForbin on 2009-05-26
Just curious, but is it not safe to always use / these days? I know it works fine on XP+ windows.

---

### Post by crdlb on 2009-05-26
> **DocForbin said:**
> Just curious, but is it not safe to always use / these days? I know it works fine on XP+ windows.

I still use g_build_filename because it feels cleaner and more correct: it makes the code more self-documenting and makes it possible to support a future platform GLib adds support for. It also prevents situations where you might forget or duplicate the separator when concatenating two parts.

---

### Post by soltanis on 2009-05-26
> **crdlb said:**
> It also prevents situations where you might forget or duplicate the separator when concatenating two parts.

Also prevents situations where Microsoft changes this compatibility for the sole purpose of screwing you up. Oh, you know they'd do it.

---

