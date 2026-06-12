---
title: "In Nvidia Turmoil"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Sam324 on 2008-06-23
Hi.  So, I had my Nvidia driver installed from EnvyNG for a while, until the updates to the system installed a worse one, which caused Ubuntu to run in "limited graphics mode".  After a while I managed to get the EnvyNG driver reinstalled, but I can't install the official Nvidia driver from the site.  I type "sudo sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run" just like it tells me to, but the stupid thing says I'm running an "X Server" and I should stop it first.  It refers me to some weird readme that doesn't even mention stopping the X Server once!  What's an X Server?  How do I stop it and install the official drivers?

---

### Post by sdennie on 2008-06-23
See this link: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

---

### Post by angryfirelord on 2008-06-23
First, I would advise to not use Envy. While it makes driver installation easier for new users, that script has been known to cause problems. (not in this case however)

Second, the X server is a program that allows you to have a GUI interface. The desktop environments & window managers (Gnome, KDE, fluxbox, etc) go on top of it to make the GUI a bit more refined. If you're curious about what it does, then you can read the wikipedia article: [http://en.wikipedia.org/wiki/X_server]("http://en.wikipedia.org/wiki/X_server")

Now, there are two ways to do this. The first is the recommended method for Ubuntu.

1.) Find a program called *Hardware Drivers Manager*. Put a check next to the nVidia option, wait for it to download and install the driver, then reboot. You can install nvidia-settings afterward.
2.) Download the nvidia driver from nvidia's website to your /home/*your_name* (also called $HOME) directory. To shut down X, first press Ctrl-Alt-F1 and log in at the prompt. Type ```
/etc/init.d/gdm stop
``` if you run gnome or ```
/etc/init.d/kdm stop
``` if you run KDE. Next, type ```
ls
``` at the prompt to list the contents of your $HOME folder, just to make sure it's there. Type ```
sudo sh *name_of_nvidia_driver*
``` and it should do its thing without problems. Reboot.

---

### Post by Sam324 on 2008-06-23
I followed angryfirelord's instructions, and it said something about having no precompiled kernels and having to compile one itself.  Now, the next time I boot, it has 800x600 as the max resolution and no desktop effects.  What do I do?

---

### Post by angryfirelord on 2008-06-23
> **Sam324 said:**
> I followed angryfirelord's instructions, and it said something about having no precompiled kernels and having to compile one itself.  Now, the next time I boot, it has 800x600 as the max resolution and no desktop effects.  What do I do?
Yes, that's normal, let it compile one for you. If it didn't spew out any other errors, then continue. To fix the resolution issue:

Open up a terminal and type in this:
```
sudo nvidia-settings
```
Click on the X Server Display Configuration. Go to Resolution, select the one you want, click Save to X Configuration file and click ok (or click yes, I don't remember) when the popup appears. Log out and log back in.

Here's a picture for reference:
[IMG]http://tracylogan.com/uploads/Image/nvidia-settings.png[/IMG]

---

