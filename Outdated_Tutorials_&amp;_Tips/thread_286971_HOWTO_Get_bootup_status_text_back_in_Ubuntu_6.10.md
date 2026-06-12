---
title: "HOWTO: Get bootup status text back in Ubuntu 6.10"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Daniel15 on 2006-10-28
If you're like me, then you like to see some status information during startup. I personally hate how Ubuntu Edgy now hides the startup information previously shown under Ubuntu Dapper (you know, the usual messages on startup, while Ubuntu is starting all the services. In case you don't know, I mean the text at the bottom of the splash screen - See [http://www.zdnet.com.au/shared/images/news/ubuntu/bootscreen.gif](http://www.zdnet.com.au/shared/images/news/ubuntu/bootscreen.gif) for screenshot). Well, it's quite easy to enable this again...

First, open your **/boot/grub/menu.lst** file with a text editor.
```
gksu gedit /boot/grub/menu.lst
```

Then, look for your kernel's 'kernel' line. On my computer, this looks like:
```

kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash vga=0x318

```

Simply remove the word 'quiet' from that line. In my case, the new line would look like:
```

kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro splash vga=0x318

```

Save the file, and reboot. If successful, you'll see status information just like in Ubuntu 6.06

---

### Post by frodon on 2006-10-28
This is just great, thanks for the tip, i love it ;)

---

### Post by Daniel15 on 2006-10-29
No problem... Glad to see that you like it as much as I do :D

---

### Post by bionnaki on 2006-10-29
do you have any suggestions for this thread: [http://www.ubuntuforums.org/showthread.php?t=192675&highlight=elegant](http://www.ubuntuforums.org/showthread.php?t=192675&highlight=elegant) ?

I'd like to have no ubuntu usplash image 
but instead a colorful text bootup.

---

### Post by jadugarr on 2006-10-29
Thanks for the tip. I thought that turning quiet off would solve it, but I wasn't sure if the new theme supported it.  I like to known what it going on at boot like you guys.  Nothing wrong with enabling quiet by default, so that new users aren't intimated.

---

