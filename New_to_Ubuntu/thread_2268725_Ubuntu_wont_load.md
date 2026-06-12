---
title: "Ubuntu wont load"
date: 2015-03-11
forum: New to Ubuntu
---

### Post by mike302 on 2015-03-11
Hi,

Could you please look into this - [http://paste.ubuntu.com/10578526/](http://paste.ubuntu.com/10578526/)

How do I repair this?

Thanks!

---

### Post by sandyd on 2015-03-11
Partition is corrupted, possibly caused by hardware failure
```

fsck -fyM /dev/sda2
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
```

Can you post the output of```

dmesg
```

---

