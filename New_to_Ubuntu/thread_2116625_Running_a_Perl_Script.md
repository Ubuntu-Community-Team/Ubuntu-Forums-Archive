---
title: "Running a Perl Script"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by swirlyglasses on 2013-02-16
Hi everyone,
I am very new to using Linux so forgive me for my noobness.

I want to run a Perl script in the Terminal, but I get 'command not found' or 'permission denied.'

I have combed through previous threads and found that a sudo command that fixes permissions, but it still doesn't work.

I have Linux booted from my USB drive.

I don't know much else, I am not using Linux to create scripts only run them:tongue:

Thanks

---

### Post by codemaniac on 2013-02-16
Hello swirlyglasses,

Welcome to Ubuntuforums !!

You can try turning on the executable bits and then run your script. Something like below.

```
chmod +x yourscript.pl

./yourscript.pl
```

Best of luck.

---

### Post by swirlyglasses on 2013-02-16
Yay, that worked thank you so much!:D

---

