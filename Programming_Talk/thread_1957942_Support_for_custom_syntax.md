---
title: "Support for custom syntax"
date: 2012-04-13
forum: Programming Talk
---

### Post by Vaphell on 2012-04-13
does anybody know how to plug custom syntax into the symbol browser in gedit (symbol browser plugin) or into geany or whatever.
I've spend quite some time googling and i am still in the dark.

I work with UI-related in-house language which is somewhat C-ish in its appearance and supports inheritance and stuff. Normally i use gedit, but in case of bloated project finding files with grep and scanning 1000-line long files with CTRL+F is tiresome in the long run.
Unfortunately the authors chose not to mimick any existing language to describe top level structures and that makes it painful to get software help with mundane stuff.
Afaik most editors use hardcoded lexers with language definitions and it's not entirely clear if i can trick them to cooperate in my case.

structure definitions come in few flavors
gui A obj B { ... }
gui C exts B.A obj D { ... }
gui E exts B.A obj D def DEF { ... }

Anyone?

---

### Post by r-senior on 2012-04-13
I believe they both use gtksourceview for their code editing windows - I suspect they are both using v2 but I'm not sure. If you install the documentation you can view it in Devhelp.

```
libgtksourceview-3.0-doc - documentation for the GTK+ syntax highlighting widget
libgtksourceview2.0-doc - documentation for the GTK+ syntax highlighting widget

```

There are a couple of sections in there that look like what you need: Language Definition Tutorial and Language Definition Reference. To quote from the first paragraph of the tutorial:

> To describe the syntax of a language GtkSourceView uses an XML format which defines nested context to be highlighted. Each context roughly corresponds to a portion of the syntax which has to be highlighted (e.g. keywords, strings, comments), and can contain nested contexts (e.g. escaped characters.)

In this tutorial we will analyze a simple example to highlight a subset of C, based on the full C language definition.

What I'm not sure about is whether these definitions provide context-sensitive help or whether it's just syntax highlighting.

---

### Post by Vaphell on 2012-04-13
i think it's just highlighting. Gedit plugin uses ctags to populate its panel with stuff and geany uses scintilla to do the heavy lifting.

---

### Post by vanangamudi on 2012-04-13
> **Vaphell said:**
> i think it's just highlighting. Gedit plugin uses ctags to populate its panel with stuff and geany uses scintilla to do the heavy lifting.

Wat is Ctags and cud give some advice on building a code-completion plugin for gedit.

---

