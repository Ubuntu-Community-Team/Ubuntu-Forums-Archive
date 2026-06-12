---
title: "Startup Freeze"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by AdrenalineJunkie on 2008-09-24
Okay, well I have installed Ubuntu after following the steps in a previous thread [Link]("http://ubuntuforums.org/showthread.php?t=927958").

It installed after a while.

But now when I start up, with the splash screen (Ubuntu) and the progress bar, it freezes like a fraction of the way along the progress bar.

Any Ideas?

Thanks

---

### Post by yragrelluf on 2008-09-24
you might have a bad installation. did you verify the cd? you probably will have to reinstall.

---

### Post by Tatty on 2008-09-24
At the grub screen, select your ubuntu entry and then press "e".  Scroll to the line which begins "kernel" and press "e" again.

Now delete the words "quiet splash" from the end of that line.  Press enter then press "b" to boot.

See this link for screenshots: [http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/)

This will boot without a splash screen and with a lot of progress messages.  Take note of any messages it seems to hang on, and particularly error messages.

---

### Post by AdrenalineJunkie on 2008-09-24
ohh ok. Il try that when i get home.

---

