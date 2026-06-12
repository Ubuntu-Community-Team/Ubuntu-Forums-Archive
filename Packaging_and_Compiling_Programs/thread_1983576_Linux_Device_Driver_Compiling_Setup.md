---
title: "Linux Device Driver Compiling Setup"
date: 2012-05-20
forum: Packaging and Compiling Programs
---

### Post by vanangamudi on 2012-05-20
I'm getting started with device driver development in linux. Ubuntu 12.04 to be precise. Linux Kernel 3.2.0 rev 20 to be more specific.

I reading LDD3. but how do I compile the source codes examples.

 gcc throws fatal error: linux/module.h file not found.

What are the list of packages I have to install before I start compiling and how do I include them in source, compilation and linking. God please any one help. I was starring at IRC channel for 9 hours. But it is of no use. I'm exhausted.

Thanx in advance...

---

### Post by gr@ss_h@pper on 2012-05-20
I think you need some package like linux-headers-p.q.r-x installed. Here p, q, r, x should be specific to the kernel version your are using. May be something like 3.2.0-20.
Go to synaptic package manager and search for "headers" or "kernel header". Hopefully from there you would be able to install kernel headers specific to your kernel version. Then you should be able to see directories like linux-headers-p.q.r-z in your /usr/src. 
The module.h would be in this directory under 
/usr/src/linux-headers-<version>/include/linux/module.h
I think after this, you should be able to compile your basic LLD3 examples using a simple makefile.

A sample simple makefile should be like:

obj-m += <your-new-driver-name>.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

HTH,
-g

---

### Post by vanangamudi on 2012-05-21
I did installing the linux headers. Now I got a new problem. 

here is the output for this following command:

COMMAND: gcc -C -ohello hello.c -I/usr/src/linux-headers-3.2.0-20/include/


OUTPUT:
```

In file included from /usr/src/linux-headers-3.2.0-20/include/linux/list.h:4:0,
                 from /usr/src/linux-headers-3.2.0-20/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-3.2.0-20/include/linux/types.h:13:2: warning: #warning "Attempt to use kernel headers from user space, see http://kernelnewbies.org/KernelHeaders" [-Wcpp]
In file included from /usr/src/linux-headers-3.2.0-20/include/linux/module.h:9:0,
                 from hello.c:2:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:24:42: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:24:42: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘INIT_LIST_HEAD’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:26:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:27:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:39:17: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘__list_add’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:41:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:42:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:43:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:44:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:60:59: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_add’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:62:28: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:62:2: warning: passing argument 1 of ‘__list_add’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:37:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:62:2: warning: passing argument 2 of ‘__list_add’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:37:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:74:64: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_add_tail’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:76:22: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:76:2: warning: passing argument 1 of ‘__list_add’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:37:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:76:2: warning: passing argument 3 of ‘__list_add’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:37:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:86:63: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘__list_del’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:88:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:89:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:99:44: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘__list_del_entry’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:101:18: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:101:31: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:104:36: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_del’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:106:18: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:106:31: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:107:7: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:108:7: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:123:12: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_replace’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:125:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:125:17: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:126:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:127:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:127:17: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:128:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:132:13: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_replace_init’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:134:2: warning: passing argument 1 of ‘list_replace’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:122:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:134:2: warning: passing argument 2 of ‘list_replace’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:122:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:135:2: warning: passing argument 1 of ‘INIT_LIST_HEAD’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:24:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:142:41: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_del_init’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:144:2: warning: passing argument 1 of ‘__list_del_entry’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:99:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:145:2: warning: passing argument 1 of ‘INIT_LIST_HEAD’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:24:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:153:61: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_move’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:155:2: warning: passing argument 1 of ‘__list_del_entry’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:99:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:156:2: warning: passing argument 1 of ‘list_add’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:60:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:156:2: warning: passing argument 2 of ‘list_add’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:60:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:165:14: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_move_tail’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:167:2: warning: passing argument 1 of ‘__list_del_entry’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:99:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:168:2: warning: passing argument 1 of ‘list_add_tail’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:74:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:168:2: warning: passing argument 2 of ‘list_add_tail’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:74:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:177:18: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_is_last’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:179:13: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:43: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_empty’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:188:13: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:204:51: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_empty_careful’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:206:31: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:207:40: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:214:44: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_rotate_left’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:218:2: warning: passing argument 1 of ‘list_empty’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:19: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:219:15: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:220:3: warning: passing argument 1 of ‘list_move_tail’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:164:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:220:3: warning: passing argument 2 of ‘list_move_tail’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:164:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:228:49: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_is_singular’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:230:2: warning: passing argument 1 of ‘list_empty’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:19: note: expected ‘const struct list_head *’ but argument is of type ‘const struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:230:35: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:230:49: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:234:34: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘__list_cut_position’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:236:37: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:237:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:237:19: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:238:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:239:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:240:7: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:241:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:242:11: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:260:34: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_cut_position’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:262:2: warning: passing argument 1 of ‘list_empty’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:19: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:264:2: warning: passing argument 1 of ‘list_is_singular’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:228:19: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:265:8: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:268:3: warning: passing argument 1 of ‘INIT_LIST_HEAD’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:24:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:270:3: warning: passing argument 1 of ‘__list_cut_position’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:233:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:270:3: warning: passing argument 2 of ‘__list_cut_position’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:233:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:270:3: warning: passing argument 3 of ‘__list_cut_position’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:233:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:275:13: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘__list_splice’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:277:32: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:278:31: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:280:7: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:281:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:283:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:284:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:293:12: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_splice’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:295:2: warning: passing argument 1 of ‘list_empty’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:19: note: expected ‘const struct list_head *’ but argument is of type ‘const struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:296:33: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:296:3: warning: passing argument 1 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘const struct list_head *’ but argument is of type ‘const struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:296:3: warning: passing argument 2 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:305:12: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_splice_tail’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:307:2: warning: passing argument 1 of ‘list_empty’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:19: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:308:27: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:308:3: warning: passing argument 1 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:308:3: warning: passing argument 3 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:319:16: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_splice_init’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:321:2: warning: passing argument 1 of ‘list_empty’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:19: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:322:33: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:322:3: warning: passing argument 1 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:322:3: warning: passing argument 2 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:323:3: warning: passing argument 1 of ‘INIT_LIST_HEAD’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:24:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:336:14: warning: ‘struct list_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘list_splice_tail_init’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:338:2: warning: passing argument 1 of ‘list_empty’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:186:19: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:339:27: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:339:3: warning: passing argument 1 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘const struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:339:3: warning: passing argument 3 of ‘__list_splice’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:273:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:340:3: warning: passing argument 1 of ‘INIT_LIST_HEAD’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:24:20: note: expected ‘struct list_head *’ but argument is of type ‘struct list_head *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:570:43: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘INIT_HLIST_NODE’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:572:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:573:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:576:47: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_unhashed’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:578:11: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:581:44: warning: ‘struct hlist_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_empty’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:583:11: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:586:39: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘__hlist_del’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:588:29: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:589:31: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:592:7: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:595:37: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_del’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:597:2: warning: passing argument 1 of ‘__hlist_del’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:586:20: note: expected ‘struct hlist_node *’ but argument is of type ‘struct hlist_node *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:598:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:599:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:602:42: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_del_init’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:604:2: warning: passing argument 1 of ‘hlist_unhashed’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:576:19: note: expected ‘const struct hlist_node *’ but argument is of type ‘struct hlist_node *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:605:3: warning: passing argument 1 of ‘__hlist_del’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:586:20: note: expected ‘struct hlist_node *’ but argument is of type ‘struct hlist_node *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:606:3: warning: passing argument 1 of ‘INIT_HLIST_NODE’ from incompatible pointer type [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:570:20: note: expected ‘struct hlist_node *’ but argument is of type ‘struct hlist_node *’
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:610:64: warning: ‘struct hlist_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:610:64: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_add_head’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:612:30: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:613:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:615:8: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:615:20: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:616:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:617:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:617:15: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:622:13: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_add_before’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:624:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:624:17: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:625:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:626:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:626:18: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:627:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:631:13: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_add_after’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:633:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:633:16: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:634:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:635:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:635:18: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:637:9: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:638:7: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:638:29: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:642:42: warning: ‘struct hlist_node’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_add_fake’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:644:3: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:644:15: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:652:15: warning: ‘struct hlist_head’ declared inside parameter list [enabled by default]
/usr/src/linux-headers-3.2.0-20/include/linux/list.h: In function ‘hlist_move_list’:
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:654:5: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:654:18: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:655:9: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:656:6: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:656:27: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-3.2.0-20/include/linux/list.h:657:5: error: dereferencing pointer to incomplete type
In file included from /usr/src/linux-headers-3.2.0-20/include/linux/module.h:12:0,
                 from hello.c:2:
/usr/src/linux-headers-3.2.0-20/include/linux/cache.h: At top level:
/usr/src/linux-headers-3.2.0-20/include/linux/cache.h:5:23: fatal error: asm/cache.h: No such file or directory
compilation terminated.
arulmozhi@ubuntu:~/Desktop/May/DD/helo$ 


```

---

### Post by gr@ss_h@pper on 2012-05-22
I am not very sure about compiling a module with gcc directly. Never did it. Would surely try to find out.

Meanwhile if you can use Makefile to compile, that can solve your problem.

Put hello.c and Makefile in a folder. Copy the following code in that Makefile:
#Makefile start

obj-m := hello.o
KVERSION = $(shell uname -r)
all:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean

#Makefile end

Just be sure of two things.
1. Under all and clean... the line "make -C..." should start with a "tab" space. Not giving any tab or spacing through space bar would again cause errors in make. This is strange, but make behaves this way. It needs some special formatting like this and not following this would show you errors like - "make: Nothing to be done for `all'."

2. I found that the name of the makefile should be "Makefile", not anything else (say makefile or something). Otherwise make might not work.

Now you can run make. It would generate .ko file for you. You can insmod this file to your kernel.

-g

---

### Post by vanangamudi on 2012-05-22
> **gr@ss_h@pper said:**
> I am not very sure about compiling a module with gcc directly. Never did it. Would surely try to find out.

Meanwhile if you can use Makefile to compile, that can solve your problem.

Put hello.c and Makefile in a folder. Copy the following code in that Makefile:
#Makefile start

obj-m := hello.o
KVERSION = $(shell uname -r)
all:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean

#Makefile end

Just be sure of two things.
1. Under all and clean... the line "make -C..." should start with a "tab" space. Not giving any tab or spacing through space bar would again cause errors in make. This is strange, but make behaves this way. It needs some special formatting like this and not following this would show you errors like - "make: Nothing to be done for `all'."

2. I found that the name of the makefile should be "Makefile", not anything else (say makefile or something). Otherwise make might not work.

Now you can run make. It would generate .ko file for you. You can insmod this file to your kernel.

-g
I have used the make file to compile the driver module. it works properly. But It is still seems strange for me that compiling modules with gcc directly is not working. thanks for the @grass_hopper

---

### Post by AbtZ on 2012-06-12
I am working on improving the Sentelic touchpad driver, and I would like to be able to test changes without the need of recompiling the whole kernel every time (it takes too long).

I have tried compiling it as a module, but when using insmod to load it I get this error:
```
insmod: error inserting 'sentelic.ko': -1 Unknown symbol in module
```

Is there something I'm missing?

---

### Post by vanangamudi on 2012-06-22
> **AbtZ said:**
> I am working on improving the Sentelic touchpad driver, and I would like to be able to test changes without the need of recompiling the whole kernel every time (it takes too long).

I have tried compiling it as a module, but when using insmod to load it I get this error:
```
insmod: error inserting 'sentelic.ko': -1 Unknown symbol in module
```Is there something I'm missing?


What I understand is that, your module requires some symbols tat are not currently present in the kernel symbol table. i.e ur module depends upon other modules which not already loaded into the kernel. 

try installing ur module into any of the standard location and use 'modprobe' for loading instead if 'insmod'

---

### Post by brian2kathleen on 2012-06-25
> **AbtZ said:**
> I am working on improving the Sentelic touchpad driver, and I would like to be able to test changes without the need of recompiling the whole kernel every time (it takes too long).

I have tried compiling it as a module, but when using insmod to load it I get this error:
```
insmod: error inserting 'sentelic.ko': -1 Unknown symbol in module
```Is there something I'm missing?

Anyone make any headway on this? I've got an SN10E1 Hannspree Hannsnote (ne' MSI Wind U100) with a Sentelic Touchpad. Most of the problems I've seen regarding this touchpad with Linux revolved around advanced features like two-finger scrolling and such. 

In my case, using a variety of Ubuntu derivatives over the past couple of years (Ubuntu, Mint, SimplyMepis, Xubuntu, Bohdi, etc.), my Sentelic touchpad either works or it doesn't. My Logitech wireless mouse consistently works, but not the Sentelic touchpad. All of the basic "Sentelic has already provided a driver for that" solutions have not fixed my touchpad because those solutions assume that your touchpad has basic functionality. If I have to reboot (Ubuntu seems to freeze up every couple of days) the touchpad might be recognized first time around, or it might take 10 reboots to get it recognized. 

Any ideas would be appreciated!

---

### Post by ruwan2 on 2013-04-20
I do not understand the previous reply: *1. Under all and clean... the line "make -C..." should start with a "tab" space. Not giving any tab or spacing through space bar would again cause errors in make. This is strange, but make behaves this way. It needs some special formatting like this and not following this would show you errors like - "make: Nothing to be done for `all'."               Especially [/U]*"*Under all and clean... the line "make -C..." should start with a "tab" space. *" Could you help me on that? Thanks,

---

