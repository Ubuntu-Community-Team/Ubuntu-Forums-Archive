---
title: "How to pause downloads in terminal ?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by rams123 on 2008-11-24
I  have slow internet. So when I'm install big softwares I need pause downloads. Is there any way to pause ?

---

### Post by nothingspecial on 2008-11-24
Yes use wget with the -c option so -

```
wget http://file
```

To pause the download press Ctrl+C

To resume the download -
```

wget -c http://file
```

In the same directory of course.

---

### Post by philinux on 2008-11-24
One way to do this is by using firefox download manager.

Find your app in here
[http://packages.ubuntu.com/intrepid/](http://packages.ubuntu.com/intrepid/)
At the bottom of the page is a link to show all. You can then use ctrl F to find your app if need be. Choose your app from the list. At the bottom of the page is the download version option 386 or x64. Then choose your mirror. Download dialog pops up to save the deb file.
This can now be paused and resumed.

Also up one level. [http://packages.ubuntu.com/intrepid/](http://packages.ubuntu.com/intrepid/)

[edit] more than one way eh

---

