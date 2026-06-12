---
title: "getAppletContext().showDocument"
date: 2011-10-02
forum: Programming Talk
---

### Post by vineeth v s on 2011-10-02
Hi,
i created japplet class, which is supposed to launch html page from local file s/m
so i signed jars and everything, but when i lauch my applet downloaded from
remote server, getAppletContext().showdocument(url) doesn't work if url is a
link to local file, like: '/home/vineeth/somdir/file.html'. when i set url to
'http://google.com', it works ok.

there is no exception or error code( showdocument returns void), and local
page doesn't load. when i lauch applet from local system, it works correct.

](*,)](*,)
pls help

---

### Post by Smart Viking on 2011-10-02
Try *file///home/vineeth/somdir/file.html*

---

