---
title: "Customizing Gedit for Web Development"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by mvalviar on 2008-11-21
I'm trying too customize Gedit for web development by following this guide > [http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html"). But none of my actions made anything different to my gedit. I noticed that when I run gedit on the command line I get:

```
(gedit:6833): GtkSourceView-WARNING **: could not load style scheme file '/usr/share/gtksourceview-2.0/styles/gedit_php_highlight.xml': unexpected element 'gconfentryfile'

(gedit:6833): GtkSourceView-WARNING **: could not load style scheme file '/usr/share/gtksourceview-2.0/styles/gedit_php_highlight.xml': unexpected element 'gconfentryfile'
```

About the command:

```
gconftool-2 --load=gedit_php_highlight.xml /apps/gedit-2/preferences/syntax_highlighting/PHP
```

Shoudn't it be:

```
gconftool-2 --load=gedit_php_highlight.xml ~/.gconf/apps/gedit-2/preferences/syntax_highlighting/PHP
```

Because I can't find any apps directory under root.

Please help me out. Thanks in advance.

---

### Post by mvalviar on 2008-11-21
*bump*

---

