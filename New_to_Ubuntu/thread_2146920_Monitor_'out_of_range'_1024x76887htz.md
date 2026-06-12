---
title: "Monitor 'out of range' 1024x768/87htz"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by oushkul on 2013-05-20
Hi,
I am really new to this so step by step required, sorry. I've installed Ubuntu Server 12.04.
When I switch on the server, I see the bios screens during startup but then the monitor goes dark with a floating message "Out of range - 1024x768/87hz".
The server is running and I can access it through PuTTY from my laptop, but I've no idea how to get the servers monitor to display properly.
The monitor is plugged into the on board VGA port. No graphics cards or anything fancy. I've tried 2 monitors with same results.
Both monitors work perfectly with other PCs.

Thanks in advance for any help :)

---

### Post by CatKiller on 2013-05-20
The console is setting a resolution that your monitor can't display - it's probably too low. You can change the resolution by fiddling with Grub's settings, although I can't remember exactly how because the method changed with Grub 2.

The resolutions you can pick are determined by whichever ones there is VESA support for in your graphics device. This will probably not be all the resolutions that your graphics device supports generally. Ideally, one of these will be the native resolution of your monitor. As an alternative, hopefully your monitor will be able to display one of them.

This is the reason we have new-fangled graphical environments :)

---

### Post by oushkul on 2013-05-20
Can I easily install a graphical environment for the server? I don't really care how it all works as long as it does...

---

### Post by CatKiller on 2013-05-20
Yeah, it's easy enough. It's all just packages. Installing something like ubuntu-desktop will pull in all the bells and whistles, or you can take your pick of window managers and mix-and-match the environment that you like.

It's probably still possible to get your text-based server up and running, though.

What's the native resolution of your monitor?

EDIT: another possibility you could consider is just running headless. There isn't really that much that you need to be local for once you've got SSH running.

---

