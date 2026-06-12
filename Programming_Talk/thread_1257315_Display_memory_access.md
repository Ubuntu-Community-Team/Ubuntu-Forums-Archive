---
title: "Display memory access"
date: 2009-09-03
forum: Programming Talk
---

### Post by pashdown on 2009-09-03
Can someone give me a pointer on how to access the display memory directly?  I am looking to send the RGB components of a screen section to another device, and although it appears there are libraries and methods for screenshotting or copying it, I'd like to just be able to access the RGB memory directly.  Is this possible?

Thanks in advance.

---

### Post by jpkotta on 2009-09-03
I don't know how easy it would be, but it's possible.  I once worked on a project with an LCD screen.  I needed to draw to it from userspace, but obviously I needed to expose it to userspace from the kernel.  I wrote a driver that was basically a minimal framebuffer driver that allocated a page of physical memory at a known address.  In userspace I could mmap() that page and read/write to it.  

Now, all of this was on an ARM single board computer, and the way the LCD was actually accessed was through two memory mapped addresses, so the stuff I did just made it look like a framebuffer.  From what I understand, on x86, there is a BIOS interface to the display memory, which is how DOS used to display graphics.  You might be able to access this through the framebuffer kernel interface (e.g. /dev/fbX).  

I'm not sure how all this applies to X11, but it is probably completely different there.

---

### Post by soltanis on 2009-09-04
I think this is what DRI is for, although I know no specifics.

---

