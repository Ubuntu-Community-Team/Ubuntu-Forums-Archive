---
title: "[SOLVED] compiz --replace"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-07-03
I think I asked this wrong in another posting.  The results of code: compiz --replace brings up the following:
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

What and how do I change the value path so it will be read.  Also, what is meant by the warning No 8 bit GLX pixmap format, disabling YV12 image format.  Do I need this ??

---

### Post by sayakb on 2008-07-04
Press Alt+F2 and type in [B]gconf-editor
[/B]Navigate to /apps/compiz/plugins/scale/allscreens/options/initiate_edge and remove any string that value has. Try running compiz again.

---

### Post by gettinoriginal on 2008-07-04
Wow, there is no value there, only the brackets that usually hold the value "[]".  Does anyone have any idea what value is supposed to be there ??

---

