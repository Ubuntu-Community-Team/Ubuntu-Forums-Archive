---
title: "streaming movies in Flash"
date: 2008-01-03
forum: Programming Talk
---

### Post by sdmike on 2008-01-03
I see on sites like ebaumsworld and spikedhumor.com where they stream their video clips through flash. They also have their title on the bottom movie corner too. 

How do I stream video clips through flash with a custom title?

---

### Post by Wybiral on 2008-01-04
[FlowPlayer]("http://flowplayer.org/") is the best free flash video player I've found. They have compiled SWF's that are also skinable. It also supports callbacks to Javascript functions for events (such as onClipChanged, which is probably what you want) that you can use to set the title when a new video starts.

---

