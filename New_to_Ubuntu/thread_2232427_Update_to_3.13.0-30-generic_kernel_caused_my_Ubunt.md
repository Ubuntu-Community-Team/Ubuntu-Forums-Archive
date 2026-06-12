---
title: "Update to 3.13.0-30-generic kernel caused my Ubuntu 14.04 to boot into black screen"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by zoso2 on 2014-07-01
Booting into previous kernel version via GRUB works just fine. Booting into 3.13.0-30-generic kernel produces a black screen where I should get the Ubuntu logo with the little dots going around in a circle instead.

How do I troubleshoot/debug/fix this and is there anywhere else I should be reporting this? Thanks in advance.

---

### Post by squakie on 2014-07-02
Press ctrl/alt/F1 when the screen is black (wait a couple of minutes after the boot).  Do you get a text login screen?  If so:

enter in your normal userid and press enter

enter in your normal password and press enter (nothing is echoed to the screen while you do this)

You should get to a prompt (<your userid>@<your pc name>$ )

type:

startx <press enter>

Do any error messages come up?  If so, copy those and post them back here so we can see.

If no error messages, press ctrl/alt/F7

Do you see a gui'd screen?

It's also quite possible you need to add nomodeset as a boot option.  You can do this from the grub menu entry for that kernel.

---

### Post by zoso2 on 2014-07-02
> type:

startx <press enter>

Do any error messages come up?  If so, copy those and post them back here so we can see.

"Module fglrx not found," I believe, is the offending error. Seems to be an issue with my ATI video card. Halp?

---

### Post by squakie on 2014-07-02
While in that text windows, try:

sudo apt-get install fglrx <press ener>

BTW - you need an internet connection to do that!

---

### Post by zoso2 on 2014-07-02
That fixed it, thanks.

---

### Post by squakie on 2014-07-02
Your welcome - just glad it working for you now! 

if you haven't already done so, please use the "Thread Tools" option above the first post and mark the thread as solved.  That way others with a similar problem can be helped as well.

---

