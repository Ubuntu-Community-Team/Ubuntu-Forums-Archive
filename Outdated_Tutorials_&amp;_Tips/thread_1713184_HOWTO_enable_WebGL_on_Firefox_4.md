---
title: "HOWTO enable WebGL on Firefox 4"
date: 2011-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2011-03-23
Hi,
yesterday I've installed FF 4 on my Lucid box.
I've found that webgl on my old intel card it is not supported giving me this message on webgl sites "This Browser does not support WebGL"

Here the steps to enable it:

1) First istall libsosmesa
```
sudo apt-get install libosmesa6
```

2) Type **about:config** on FF address bar

3) Search for value **webgl.osmesalib**

4) And as string type: **/usr/lib/libOSMesa.so.6**

5) Restart FF, done!

To check the enabled webgl feature go to
[https://demos.mozilla.org/en-US/](https://demos.mozilla.org/en-US/)
and play 360° Video

Or go to [http://bodybrowser.googlelabs.com/](http://bodybrowser.googlelabs.com/)

Be careful because browsing with webgl (at least with my poor i915 intel card) is very eager of resources

---

### Post by Irony on 2011-03-24
Thanks for this, it worked!

---

### Post by Anduu on 2011-04-22
Just ran across this...figured it could use a bump ;)

Works in Natty too.

---

