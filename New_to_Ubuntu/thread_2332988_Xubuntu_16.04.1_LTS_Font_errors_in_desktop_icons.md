---
title: "Xubuntu 16.04.1 LTS Font errors in desktop icons"
date: 2016-08-06
forum: New to Ubuntu
---

### Post by chessmate99 on 2016-08-06
Hi all, I am getting black fonts that are misaligned in my desktop icon texts. this is a photo of it:
[IMG]http://i.imgur.com/6fJqmAL.png[/IMG]

How do i fix this? I just installed xubuntu 16.04.1 via usb boot.

---

### Post by ajgreeny on 2016-08-06
Perhaps this problem?
[https://ubuntuforums.org/showthread.php?t=2331783](https://ubuntuforums.org/showthread.php?t=2331783)

---

### Post by Dennis N on 2016-08-06
There is some additional discussion in this thread, including a link to the bug report:

[https://ubuntuforums.org/showthread.php?t=2332348](https://ubuntuforums.org/showthread.php?t=2332348)

---

### Post by chessmate99 on 2016-08-06
The solution doesn't seem to work though. i set the textstyle to 0 at the required line and file but it still appears. I'm using a vertex theme. Other themes give the same problem too. Reading further, the solutions maximally solves the shadow problem but doesn't make the alignment correct for the white text.

---

### Post by Dennis N on 2016-08-06
You need to log out and log back in after a theme change to see any change in the Desktop icon text. Did you do that? I also have seen this in some other themes, not just Numix.

As to the textstyle = 0 idea, I thought that it was not satisfactory because it removed the shadow under the white text, making it hard to see when it is sitting over a light area of the background. So I ended up using Graybird theme which is not affected.

---

### Post by mook765 on 2016-08-06
I tried i out just right now and have same appearance.
So i compared the gtkrc files for numix and greybird theme.
I deleted the lines 531 and 532 in the gtkrc file from numix theme, that brought success.
you are invited to try it yourself.
If you have the patience, you can try to play with the values in these lines to get better effect.
But could take long time, as we don't know, how the murrine engine works....
Have a nice weekend...
> 
[URL="https://wiki.ubuntu.com/Artwork/Documentation/Murrine"]https://wiki.ubuntu.com/Artwork/Documentation/Murrine
[/URL]

---

### Post by Dennis N on 2016-08-06
> I deleted the lines 531 and 532 in the gtkrc file from numix theme, that brought success. you are invited to try it yourself.

I did, but I get the same result as using textstyle = 0 in line 531 and leaving 532 as-is (the previous suggestion taken from the bug report). That is, white text, centered, but no text shading (shadow) which is what the dark under-text should provide.     

Back to Greybird.

---

### Post by mook765 on 2016-08-06
@Dennis
I think you are right, i supposed the trick didn't work for chessmate.
Now i think, chessmate edited the configuration-file for the numix-theme following the instructions in that thread, but s/he wrote that s/he use a vertex theme...

---

### Post by Dennis N on 2016-08-06
The best solution is for the person(s) responsible for creating the package that caused these problems to fix it and release a new package a soon as possible, instead of us trying to fix it on the receiving end. Let's hope that fix is in progress. I know it only happened after some updates we received.

---

### Post by xubuntu84 on 2016-09-12
> **Dennis N said:**
> The best solution is for the person(s) responsible for creating the package that caused these problems to fix it and release a new package a soon as possible, instead of us trying to fix it on the receiving end. Let's hope that fix is in progress. I know it only happened after some updates we received.

I 100% agree. Taking the time to troubleshoot this on the user end is not worth it, IMO.

Wanted to +1 this issue, see attachment.

---

