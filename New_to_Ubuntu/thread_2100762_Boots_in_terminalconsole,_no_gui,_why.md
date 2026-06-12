---
title: "Boots in terminal/console, no gui, why?"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by Fnugus on 2013-01-02
I use Ubuntu 12.04 LTS desktop.

It worked very well until I tried to boot today, where, instead of the usual graphical login screen, I'm stuck with a text-only interface, as the terminal. No graphics, no desktop, or anything.

As far as I can see, it put a new file in my desktop folder: nvidia-bug-report.log.gz. I suspect that there is some information in that file as to why my graphics fail, but I don't really know how to open the file, and much less what to do to fix things.

---

### Post by lykwydchykyn on 2013-01-02
If you log in and type:
```

startx

```

It will attempt to launch the graphics and desktop, and if it fails you should see some errors that will help you (or people here) debug the problem.

The error lines will start with "[EE]".

---

### Post by Fnugus on 2013-01-02
Thank you.

Well, it fired up the graphical desktop, but without any of the menus (neither top nor bottom bars are visible).

Further, it complains that compiz closed unexpectedly, and prompted me whether to try to relaunch it or leave it be closed.

---

### Post by lykwydchykyn on 2013-01-02
Ok, the other option is to run this command to find your errors:

```

grep EE /var/log/Xorg.0.log

```

I take it you have an nvidia graphics chip?

---

### Post by Fnugus on 2013-01-02
> **lykwydchykyn said:**
> I take it you have an nvidia graphics chip?
Yes, although I am unsure which one. This is a very old computer with a lot of different parts replaced at some point. 

That command resulted in 
 (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    [  2271.856] (II) Loading extension MIT-SCREEN-SAVER

---

### Post by steeldriver on 2013-01-02
you should be able to look at the contents of the nvidia-bug-report.log.gz file in the console by doing

```
less < <(gzip -dc ~/Desktop/nvidia-bug-report.log.gz)
```

page through with SPACE - back with b - quit with q

---

### Post by Fnugus on 2013-01-02
> **steeldriver said:**
> you should be able to look at the contents of the nvidia-bug-report.log.gz file in the console by doing

```
less < <(gzip -dc ~/Desktop/nvidia-bug-report.log.gz)
```page through with SPACE - back with b - quit with q

Yes, that got it open. I have no idea how to deduct anything remotely useful from the contents, though.

---

### Post by steeldriver on 2013-01-02
is it absolutely huge? if not you could maybe use pastebinit and post the url back here

[https://help.ubuntu.com/community/Pastebinit](https://help.ubuntu.com/community/Pastebinit)

---

