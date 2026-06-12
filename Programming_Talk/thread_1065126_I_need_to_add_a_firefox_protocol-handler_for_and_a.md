---
title: "I need to add a firefox protocol-handler for and application when it gets installed"
date: 2009-02-09
forum: Programming Talk
---

### Post by Yuzem on 2009-02-09
What I am trying to do is to add a protocol handler for firefox when my application gets installed.
The application is called climdb

So far I am copying a file called climdb.js to /etc/firefox-3.0/pref

The file looks like this:
```
pref("network.protocol-handler.app.climdb","/usr/bin/climdb");
pref("network.protocol-handler.warn-external.climdb",false);
pref("network.protocol-handler.external.climdb",true);
```

From firefox's about:config page I can see the three values correctly configured but when trying it: climdb://somthing
Nothing happens...

Is this a bug or I am doing something wrong?

---

