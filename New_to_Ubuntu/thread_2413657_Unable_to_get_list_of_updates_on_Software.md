---
title: "Unable to get list of updates on Software"
date: 2019-02-28
forum: New to Ubuntu
---

### Post by riazufila on 2019-02-28
[url=http://i.imgur.com/D1AWITg.png]
  [img]http://imgur.com/D1AWITgl.png[/img]
[/url]

I get this error whenever I check for updates on Ubuntu (Xubuntu)'s Software. Any ideas how to fix this?

---

### Post by jdeca57 on 2019-02-28
My eyes are not stong enough to read exactly what the error message is but it seems to be a program in de home directory and steam so most likely in /etc/apt/sources.list there are (steam) entries that are in error. Comment them out putting a # in front of them and try again. Of course, the game won't be updated.

---

### Post by riazufila on 2019-03-01
Sorry for the inconvenience I caused. Should've made that easier for you. And the problem is solved. Thank you!

---

