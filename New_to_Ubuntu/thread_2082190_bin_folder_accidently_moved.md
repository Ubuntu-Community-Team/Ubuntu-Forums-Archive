---
title: "bin folder accidently moved"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by win22lin on 2012-11-08
Hi

Sorta new to Ubuntu.  I have a few issues, while one issue slowed my computer to a crawl, I was using my mouse to push open windows around.  Nothing happened, kinda locked up, then once it resumed working a window popped up indicating that a "bin" folder was being moved to the desktop, of course I didn't want this to occur.

So now I have to move it back and don't know where it goes.  It has around 1900 files in it, please tell me where it goes in my directory. I have ubuntu natty narwhal, 11.04 I believe.  Thanks for any help.

---

### Post by Calinou on 2012-11-08
Unless you started Nautilus using gksudo, you're probably fine (you can only edit files in your home directory as a normal user).

edit: 11.04 is EOL now, too, remember.

---

### Post by win22lin on 2012-11-08
Hi

I have rebooted twice and the "bin" folder is still on the desktop.  Should I just delete it.  I really can't remember if the indicator note said moving or copying.

---

### Post by DogMatix on 2012-11-08
bin goes in the top level of your file system

open a terminal and run 

```
ls /
```

and see if bin is listed. I expect it still will be. Are you sure it wasn't just copied to your desktop?

EDIT: If you have rebooted and everything seems OK you are likely to have copied not moved bin

---

### Post by win22lin on 2012-11-08
I performed a file search for a file I thought was unique in the bin folder on my desktop and found the matching file in a matching folder under /usr/bin/  .  So I just deleted the desktop "bin" folder, thanks for the help.

---

### Post by newb85 on 2012-11-08
There are three folders named "bin":
/bin
/usr/bin
/usr/local/bin

Of course, without root or superuser privileges, none of these can be edited or removed, so you should be fine.

---

