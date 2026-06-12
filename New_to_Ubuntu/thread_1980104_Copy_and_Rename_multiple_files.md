---
title: "Copy and Rename multiple files"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by larmet on 2012-05-14
I am doing the following:

cp 2012_-05-0019^H001.dd /mnt/windowshare/2012-05-0019/image.001
cp 2012_-05-0019^H002.dd /mnt/windowshare/2012-05-0019/image.002
...
cp 2012_-05-0019^H128.dd /mnt/windowshare/2012-05-0019/image.128

Is there an easier way to do this??

---

### Post by HiImTye on 2012-05-14
```
rename -n 's|2012\_\-05\-0019\^H(\d+)\.dd|image.$1|' *.dd
```
to make sure that it will output what you want (the -n doesn't perform an actual rename)
then
```
rename -v 's|2012\_\-05\-0019\^H(\d+)\.dd|image.$1|' *.dd; cp image.* /mnt/windowshare/2012-05-0019/
```

---

