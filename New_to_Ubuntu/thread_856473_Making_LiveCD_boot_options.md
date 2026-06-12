---
title: "Making LiveCD boot options"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by johnverxon on 2008-07-11
Hi

I tried the LiveCD for the first time today, I want to keep playing with it for a while before I actually install Ubuntu.

Initially it didn't work; I got put into busybox with some "revalidation" errors saying ATA1 errno -5. Adding all_generic_ide after pressing F6 did the trick though.

However, I don't want to type this every time I start up. Also, I want the keyboard to be set to en-GB by default.

Is there an initialization file I can edit that will remember these changes to the default?

Thanks,
John

---

### Post by avtolle on 2008-07-11
See this as to how to make the all_generic_ide permanent: [https://help.ubuntu.com/community/BootOptions#Making%20Permanent%20changes](https://help.ubuntu.com/community/BootOptions#Making%20Permanent%20changes) (this is for post-installation).

On the keyboard, when you install, you have options there; select the correct one at the appropriate step (sorry, I don't remember which one).

AFAIK, while using the Live CD, you will need to manually enter the boot option each time.

---

### Post by aimpau on 2008-07-11
For the liveCD. definitely won't work (i think) but making a Live Boot environment from something else, lets say a thumb drive is quite plausible. I know I have read somewhere here on how to make a consistent live boot environment. Sorry if I wasn't able to help that much.

---

