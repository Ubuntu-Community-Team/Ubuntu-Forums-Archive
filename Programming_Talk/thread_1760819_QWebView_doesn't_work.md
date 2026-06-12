---
title: "QWebView doesn't work"
date: 2011-05-17
forum: Programming Talk
---

### Post by nidzo732 on 2011-05-17
Im trying to use the webview widget in qt but it won't compile, here's a screenshot:
[[img]http://www.dodaj.rs/t/3i/du/4VTLcUGs/screenshot-mainwindowui-.jpg[/img]](http://www.dodaj.rs/?3i/du/4VTLcUGs/screenshot-mainwindowui-.png)
What am i doing wrong

---

### Post by benson444 on 2011-05-18
QWebView is a class in the QtWebKit module. Have you added the module to the .pro file?

```
QT += webkit
```

---

