---
title: "Python: Sending Files!"
date: 2010-08-16
forum: Programming Talk
---

### Post by Sailor5 on 2010-08-16
Ahoy sailors!

So I'm using python twisted to send and receive some files, However some of the files may be about 500 kb which of course will mean implementing some new strategies.

The only way I could think of is to read the file into a variable then some how split it equally into several vars, To which then send each one by one.

But how could I split it up into certain amounts? Or is there a better way you can suggest?

Thanks Bye!

---

### Post by soltanis on 2010-08-16
You can't use any of the protocols which are designed for transmitting files, like FTP?

---

### Post by Sailor5 on 2010-08-17
> **soltanis said:**
> You can't use any of the protocols which are designed for transmitting files, like FTP?

Well only has a last resort, I'd quite like to use Twisted for this, I've already got it to perform this however I can only receive small archives.

---

### Post by DanielWaterworth on 2010-08-17
Are you using a stream-based protocol? ie tcp

---

### Post by hudsonl on 2010-08-17
Can you use the split command ? 

> split /?

---

### Post by wmcbrine on 2010-08-17
OK, I'm not familiar with Twisted. However, speaking on an HTTP level, there's no problem with sending arbitrarily large files from a browser to a server. You just have to use POST instead of GET.

---

