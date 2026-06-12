---
title: "[SOLVED] how do i delete the Jamendo catalogue?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by opendevlite on 2008-04-26
First when i clicked on Jamendo on Rhythymbox it loads the catalogue, after that it shows me thousands of artist,album and songs. Everything was ok.

I was just looking if Jamendo had an internet radio, but it didn't, so I decided to switch back to last.fm radio.

I was wondering, is there a way to remove the Jamendo catalogue that was loaded when i first clicked on Jamendo, it seems like a download from Jamendo to Rythmbox.

Is it just a file to delete or something else?

---

### Post by FredB on 2008-04-26
In a console type :

```
cd .gnome2/rhythmbox
rm -rf jamendo
```

---

