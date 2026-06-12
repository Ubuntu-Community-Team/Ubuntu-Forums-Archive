---
title: "[SOLVED] Error: &amp;quot;Unsupported Kernel Version&amp;quot;?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by duckfeet on 2008-07-26
In trying to resolve my insanely fast mouse-wheel, I googled around, and found that some were using the app hidpoint1-0.bin ... so I downloaded it, and at first couldn't open it, but changed permissions, and was dragged it to terminal, and got it to start opening, finally, but then this error popped up...anybody know what I need to do next?  This app says it is supported by Ubuntu 8.04, and I thought it might work for me...

TIA

---

### Post by Pro-reason on 2008-07-26
> **duckfeet said:**
> In trying to resolve my insanely fast mouse-wheel, I googled around, and found that some were using the app hidpoint1-0.bin ... so I downloaded it, and at first couldn't open it, but changed permissions, and was dragged it to terminal, and got it to start opening, finally, but then this error popped up...anybody know what I need to do next?  This app says it is supported by Ubuntu 8.04, and I thought it might work for me...

TIA

To find out your kernel version, type "*uname -sr*" at a terminal.

I think the default Linux kernel for Ubuntu 8.04 is 2.6.24-19.  You should look at the documentation for the thingy that you downloaded to see what it requires.

---

### Post by duckfeet on 2008-07-26
Yep, that's the kernel I have, and now I tried to open it, and got :'Could Not Open : Archive Type Not Supported"...oh well, I'll keep checking around..I go to site, the obvious source of info, but all I read in their forums are posts saying it doesn't work...Thankyou...anybody who has ideas on how to open this file, please feel free to jump in....

---

### Post by Pro-reason on 2008-07-26
What is this site you're talking about?

---

### Post by duckfeet on 2008-07-26
[www.hidpoint.com](www.hidpoint.com)

I'd tried lots of other things: this seemed like was what I needed, since my problem is with a microsoft mouse "Wireless Optical Mouse" 2.0, and the wheel zooms thru pages, I can't even use it...it only seems to happen in Linux...

I was going thru my synaptics apps, and found mouseemu, that someone else said worked, and that I was apple to install, so I'll play around with that...unless someone else knows of either a better app...I did read that someone else had had good luck w/a bluetooth mouse, and I might try that, next time I run across one...

---

### Post by Pro-reason on 2008-07-26
> **duckfeet said:**
> [www.hidpoint.com](www.hidpoint.com)

I'd tried lots of other things: this seemed like was what I needed, since my problem is with a microsoft mouse "Wireless Optical Mouse" 2.0, and the wheel zooms thru pages, I can't even use it...it only seems to happen in Linux...

OK.  I've downloaded the file to see.

I put it on my desktop.

I've gone to the terminal and run this:

```

md5sum ~/Desktop/hidpoint1-0.bin

```

...and it gives me "f9fcf8fdc92dab261978c1327f88a685", which is the check sum provided on the site.  This confirms that it downloaded OK.

Next, I run this:

```

chmod +x ~/Desktop/hidpoint1-0.bin
~/Desktop/hidpoint1-0.bin

```

It starts to uncompress itself just fine, with the following output:

```

Verifying archive integrity... All good.
Uncompressing HIDPoint1.0 (Beta) Build 80616 Setup............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

```

It eventually opens a window asking for my password.  Since I don't actually want to install anything, I closed it at this point.

Are you able to duplicate all of that successfully up to that point?

---

### Post by duckfeet on 2008-07-26
Not so far, so I'm going to try and duplicate what you just did, see what happens, since reading about this app, seems like it might help...sure appreciate the help...as u can see, this isn't a real popular topic...I try to only whine about it once a week ;-)

Off to try again...

---

### Post by duckfeet on 2008-07-26
I got as far as you did, and entered my password, and it finally did extract and install a file in my desktop directory...that was it: I thought maybe I'd get a little window or something, but at least it is installed: I went thru this twice, just to be sure, and will now search around, see how to get this app to run, since I've tried everything I can think of...

Again, much appreciate the help....

---

### Post by Pro-reason on 2008-07-26
OK, great.

I'm not sure what this software actually does once installed.  Perhaps it's just supposed to make the mouse start working correctly.

If it is some sort of kernel module, then you will have to reboot to see any effect.  There may be more information on the site it came from.

---

### Post by duckfeet on 2008-07-26
Well: it did that: nothing popped up, nothing adjusted, but it's about 1/4 of the speed it once was, so I'm *fine* with that...I've been battling this since I loaded linux...one of my main problems w/installation, which I remembered when I saw you had posted a "chmod" on the command line, was that I hadn't changed permissions, and I think that was why I couldn't install it...

In any case, I"m not spinning all over the place now, and I thank you, and will go ahead and change this to "solved"


> **Pro-reason said:**
> OK, great.

I'm not sure what this software actually does once installed.  Perhaps it's just supposed to make the mouse start working correctly.

If it is some sort of kernel module, then you will have to reboot to see any effect.  There may be more information on the site it came from.

---

