---
title: "Custom Gedit Syntax Highlighting"
date: 2013-01-27
forum: Programming Talk
---

### Post by uMinded on 2013-01-27
I'm running Ubuntu 12.04 with gnome-session-fallback.

I am trying to add some javascript like syntax highlighting to gedit. I have coppied the javascript.lang file from "/usr/share/gtksourceview-3.0/language-specs" and renamed it to modjs.lang

Below is the only changed I have done to that file: (I removed the mimetypes property too)
```

<language id="mjs" _name="ModJS" version="1.0" _section="Scripts">
<property name="globs">*.mjs</property>
....
<!--main context-->
<context id="mjs" class="no-spell-check">

```

However when I load up a javascript file and select ModJS from the Scripts menu I do not get any highlighting at all! 

Any idea why it wouldn't work? If I select javascript it highlights and my ModJS is the exact same content...

---

