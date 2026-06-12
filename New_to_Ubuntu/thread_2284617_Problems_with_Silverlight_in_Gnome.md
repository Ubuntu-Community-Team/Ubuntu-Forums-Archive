---
title: "Problems with Silverlight in Gnome"
date: 2015-06-30
forum: New to Ubuntu
---

### Post by anbu-s on 2015-06-30
One of my regular websites require Microsoft silverlight installed - I've done the pipelight installation and enabled silverlight.

sudo pipelight-plugin --enable silverlight

But I'm still getting install silverlight message in firefox. It is installed and enabled.

How do i fix this?

---

### Post by deadflowr on 2015-07-01
Have you tried switching silverlight versions?
```
sudo pipelight-plugin --disable silverlight5.1 --enable silverlight5.0
```
from here
[http://pipelight.net/cms/plugin-silverlight.html](http://pipelight.net/cms/plugin-silverlight.html)

---

### Post by monkeybrain20122 on 2015-07-01
Silverlight 5.1 is ok, don't need to disable it and enable 5.0.

Probably Firefox hasn't updated its plugin yet. Close Firefox and run

```
sudo pipelight-plugin --create-mozilla-plugins
```

It should work now.

---

### Post by anbu-s on 2015-07-02
> **monkeybrain20122 said:**
> Silverlight 5.1 is ok, don't need to disable it and enable 5.0.

Probably Firefox hasn't updated its plugin yet. Close Firefox and run

```
sudo pipelight-plugin --create-mozilla-plugins
```

It should work now.

That worked..thanks
But after login to the website, i'm not able to download any files that are posted there. Must be something to do with the way plugin works on that site. In windows, when i right click on a file , it gives you the option to download and when clicked, the file is downloaded.
In ubuntu, i get the same option - but when i click download, it errors out.

---

### Post by monkeybrain20122 on 2015-07-03
> **anbu-s said:**
> That worked..thanks
But after login to the website, i'm not able to download any files that are posted there. Must be something to do with the way plugin works on that site. In windows, when i right click on a file , it gives you the option to download and when clicked, the file is downloaded.
In ubuntu, i get the same option - but when i click download, it errors out.

What site is that? It may check for platform. In that case use user-agent-overrider to spoof it. [https://addons.mozilla.org/En-us/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/En-us/firefox/addon/user-agent-overrider/)

---

