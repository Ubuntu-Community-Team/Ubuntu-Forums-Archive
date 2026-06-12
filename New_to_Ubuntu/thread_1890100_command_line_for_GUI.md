---
title: "command line for GUI?"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by cronish on 2011-12-02
The Ubuntu 'test drive' shows a desktop, which I was expecting to appear upon reboot after installation. However, instead of the desktop, after logging in I get a command prompt. How do I get to the desktop from the command prompt?

---

### Post by HavoK360 on 2011-12-02
This means you haven't installed it correctly. If its CMD on Ubuntu...I cant help. BUT if its the computer visulation CMD (Meaning really pixelated font and black screen) you have a bad install, and a wiped hard drive. There IS a way to install without the OS, but it requires another computer to get the command lines. Assuming you are using a ifferent computer right now...you should be fine.
Good luck!

---

### Post by cronish on 2011-12-02
It's a typical command line. I installed 32-bit 11.10. There were several failed installations, so this time I went without any of the software packages.

If someone can tell me either a) how to command-line to the desktop, or b) how to re-install so that it boots to the desktop, I would be happily guided.

---

### Post by lisati on 2011-12-02
If you have a prompt inviting you to login, there may be a chance that you can fix things without having to bother with reinstalling. 

Try logging in with the user name you created when you did the installation. Don't panic if the password doesn't show as you type, this is normal. If you log in successfully, there will be options, such as trying this:
```
sudo startx
```

Depending on how you get on, there are other things we can suggest to help you.

---

### Post by cronish on 2011-12-02
Thanks lisati, my command line shows username@ubuntu:~$ and when I type sudo startx I get a reply "command not found"

---

### Post by papibe on 2011-12-02
That's weird. Could you post the name of the ISO (or link) that you installed?

May be you installed a minimal CD or the server edition?

Regards.

---

### Post by -kg- on 2011-12-02
What concerns me a bit is the following:

> **cronish said:**
> I installed 32-bit 11.10. There were several failed installations, so this time I went without any of the software packages.

Did you just attempt to install several times, or between each installation attempt, did you delete the partitions that were created in the previous attempt?  If you didn't delete the partitions from the previous attempts, they'll build up and leave you with not enough room to install everything in.

I was going to ask you about the exact distro you installed, but papibe beat me to it.  Certainly, what you describe sounds like a server edition.

---

### Post by lolpenguin on 2011-12-02
Looks like the X Window System is not installed. This is probably a install failure. Boot into the install disk and check it for errors, then delete all partitions IF YOU DO NOT HAVE ANY PRECIOUS DATA ON THEM, and restart the installation.

---

### Post by cronish on 2011-12-03
I downloaded and installed the 10.04 version, and that works fine. Maybe my hardware won't support the new version? 

I can't get my wireless card working, even with ndiscwrapper installed, but that's another problem.

Thanks everyone for the assistance, much appreciated.

---

### Post by lolpenguin on 2011-12-03
Possibly...possibly.

---

