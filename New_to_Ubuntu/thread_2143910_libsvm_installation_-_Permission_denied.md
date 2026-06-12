---
title: "libsvm installation - Permission denied"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by Maik20 on 2013-05-10
Hi,

i am new to linux. I installed libsvm ([http://www.csie.ntu.edu.tw/~cjlin/libsvm/](http://www.csie.ntu.edu.tw/~cjlin/libsvm/)) to my pc. I downloaded the file and run "make". Then i tried to run libsvm:

```
~/Download/libsvm: svm-scale -l -1 -u 1 -s range1 train.1 > train.1.scale$1

```

but i got:
```
Permission denied
```

What permission do i have to set?

Thanks

---

### Post by Perfect Storm on 2013-05-10
Try with;
```
./svm-scale -l -1 -u 1 -s range1 train.1 > train.1.scale$1
```
If you compiled the application without installing it systemwide.

---

