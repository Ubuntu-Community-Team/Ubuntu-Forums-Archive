---
title: "How to use bluetooth libraries in a program?"
date: 2009-12-15
forum: Programming Talk
---

### Post by kizofilax on 2009-12-15
SO i have this program written in c, its a text file called simplescan.c, it already hast executable permissions and everything. I can compile it with the following command

gcc -o simplescan simplescan.c -lbluetooth

After this an executable is created and I can run it with

./simplescan

It runs fine without any issue

So now I have been trying to use several IDE's like kdevelop and code:blocks.

I create a project (usually hello world) and then copy the contents of the simplescan.c into the main replacing the "hello world" code.

Now, how do I tell the IDE to use tht bluetooth library???

The headers of the simplescan.c file are 

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/socket.h>
#include <bluetooth/bluetooth.h>
#include <bluetooth/hci.h>
#include <bluetooth/hci_lib.h>

Specifically with code:blocks. So far it has been the only Linux IDE in which I have been able to run a simple "hello world" program...

Thanks

---

### Post by kizofilax on 2009-12-15
Never mind I just figured out how

---

### Post by Hellkeepa on 2009-12-15
HELLo!

Care to share, so that other with this problem can find out as well?

Happy codin'!

---

