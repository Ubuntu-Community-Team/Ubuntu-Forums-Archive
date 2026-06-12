---
title: "statvfs"
date: 2011-10-20
forum: Programming Talk
---

### Post by sepoto on 2011-10-20
```

#include <sys/statvfs.h>
#include <iostream>
using namespace std;

int main() {
	int rv;
	const char *path = "/dev/sdb";
	struct statvfs fsdata;
	rv = statvfs(path, &fsdata);
	return 0;
	return 0;
}

```

```

Name : fsdata
	Details:{f_bsize = 4096, f_frsize = 4096, f_blocks = 496330, f_bfree = 496329, f_bavail = 496329, f_files = 496330, f_ffree = 495725, f_favail = 495725, f_fsid = 0, f_flag = 4096, f_namemax = 255, __f_spare = {0, 0, 0, 0, 0, 0}}
	Default:{...}
	Decimal:{...}
	Hex:{...}
	Binary:{...}
	Octal:{...}

```

My block size is returning 4096 and I have calculated the total size of /dev/sdb to be 1.9GB +-. That is totally wrong. I have already verified that /dev/sdb is 32GB in size. I also question the block size. /dev/sdb in this case happens to be an SD card which has mounted to /dev/sdb by my OS which is Ubuntu 11.1. Does anyone know what can be done to obtain an accurate reading?

Thanks!

---

### Post by gsmanners on 2011-10-20
Doesn't statvfs only work on mounted paths? In other words, a path like /var or /home rather than a /dev

---

### Post by sepoto on 2011-10-20
Perhaps you are correct and if that is the case what I need is another solution. Suggestions?

---

### Post by gsmanners on 2011-10-20
Is it even possible to stat a drive without mounting? Seems to me that you're making hardware-related assumptions if you can actually do that.

---

### Post by sepoto on 2011-10-20
I am not really sure what you are saying. I just want to be able to read and write to my SD card as close to the hardware level as possible. Is there a library. If Ubuntu performs these operations and it does then there is source code for those operations. Can you tell me where to find some? My sd card reader is USB. Does that answer any questions?

---

### Post by gsmanners on 2011-10-20
> **sepoto said:**
> I am not really sure what you are saying. I just want to be able to read and write to my SD card as close to the hardware level as possible. Is there a library. If Ubuntu performs these operations and it does then there is source code for those operations. Can you tell me where to find some? My sd card reader is USB. Does that answer any questions?

Reading and writing are also mounted-only functions, so I guess what you're really asking for is a way to find the mount point of your device, right?

If that's the case, then simply parsing through /etc/mtab will give you the mount point, and from that you can use statvfs to get the info you want.

---

### Post by sepoto on 2011-10-20
I'm not sure what you mean by parsing through /etc/mtab. Could you elaborate a bit more on that subject? Thanks!

---

