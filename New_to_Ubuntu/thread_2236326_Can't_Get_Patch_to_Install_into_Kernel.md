---
title: "Can't Get Patch to Install into Kernel"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by SMiller FTP on 2014-07-26
Greetings everyone.

I been having trouble trying to install a patch to fix another problem. But I can't seem to find out how to get the patch to install. I tried many sources from different websites and a few books with no succes. I've gottan as close to moving the patch to the /usr/src/ directory where I think the kernel is. But as I try to run command " patch < " to install it. I keep getting a message asking what file to patch. I thought that being the files in that particular directory, I tried all in it and the directory itself and kept getting this from what you see below.

```

User@User-GA-78LMT-S2P:~$ patch < /usr/src/0004-HID-kye-Add-support-for-3-tablets.patch
can't find file to patch at input line 23
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|From c4e9680f6c188b6923d7b792a2fcf5fc985ed289 Mon Sep 17 00:00:00 2001
|From: Nikolai Kondrashov <spbnick@gmail.com>
|Date: Tue, 28 Feb 2012 13:01:46 +0200
|Subject: [PATCH 4/4] HID: kye: Add support for 3 tablets
|
|Add support for three KYE tablets: EasyPen i405X, MousePen i608X, EasyPen M610X.
|Update Kconfig entry accordingly, remove EXPERT dependency.
|
|Signed-off-by: Nikolai Kondrashov <spbnick@gmail.com>
|Signed-off-by: Jiri Kosina <jkosina@suse.cz>
|---
| drivers/hid/Kconfig             |    9 +-
| drivers/hid/hid-core.c          |    3 +
| drivers/hid/hid-ids.h           |    3 +
| drivers/hid/hid-kye.c           |  399 +++++++++++++++++++++++++++++++++++++--
| drivers/hid/usbhid/hid-quirks.c |    2 +
| 5 files changed, 396 insertions(+), 20 deletions(-)
|
|diff --git a/drivers/hid/Kconfig b/drivers/hid/Kconfig
|index 7e0acf4..a0843e7 100644
|--- a/drivers/hid/Kconfig
|+++ b/drivers/hid/Kconfig
--------------------------
File to patch: /usr/src/   
File /usr/src/ is not a regular file -- refusing to patch
File /usr/src/ is read-only; trying to patch anyway
patch: **** Can't create temporary file /usr/src/.oKFxWfy : Permission denied
User@User-GA-78LMT-S2P:~$ 

```

The last four lines are what I keep getting no matter what.
I'm currently using Kubuntu 14.04 if that helps.
 
Thanks to all that replies.

---

