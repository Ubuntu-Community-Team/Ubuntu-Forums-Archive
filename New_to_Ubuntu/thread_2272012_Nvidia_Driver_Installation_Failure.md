---
title: "Nvidia Driver Installation Failure"
date: 2015-04-03
forum: New to Ubuntu
---

### Post by cobalt2 on 2015-04-03
When attempting to install a Nvidia driver I received the error saying that installation failed because I have a 'X server running. I looked through the task manager and couldn't find any task with the name 'x server'. What could possibly be causing this problem?

Edit: I'm running Ubuntu 14.10.

---

### Post by dino99 on 2015-04-03
purge all the installed nvidia driver(s) : sudo apt-get purge nvidia*
then install the required driver from the ubuntu archive (its easy with 'synaptic' app)

---

### Post by cobalt2 on 2015-04-03
I want to use the driver I already downloaded from Nvidia's website for my specific graphics card. After purging all Nvidia drivers, could I install it manually?

---

### Post by Al1000 on 2015-04-03
There might well be an nvidia driver available for your graphics card in the software repositories. Software in the repositories for your particular version of Ubuntu has been checked for compatibility with that version of Ubuntu, whereas software that you download from websites hasn't, so there's no guarantee that it will work. X server (which your desktop requires) running, shouldn't have caused installation to fail.

After purging nvidia, I would install and run a program called nvidia-detect, which searches your computer for the graphics card then recommends a driver for it.

To install nvidia-detect, in a terminal type:

```
sudo apt-get install nvidia-detect
```

To run nvidia-detect:

```
nvidia-detect
```

---

### Post by buzzingrobot on 2015-04-03
If you are using the.run archive from the Nvidia site, you can't be running the GUI aka the 'X server'.  Probably the simplest way to get there is to kill it after you've booted up opening a terminal and executing this:

```
sudo         /etc/init.d/lightdm stop
```

That will drop you to a full-screen console.  Navigagte to the directory where you've placed the .run file and follow Nvidia's instructions.  Then, cross your fingers and reboot.

If the Additional Drivers tool offers you a driver you can accept, it's usually much simpler and more reliable to take that option.

---

### Post by Vladlenin5000 on 2015-04-03
> **buzzingrobot said:**
> If the Additional Drivers tool offers you a driver you can accept, it's usually much simpler and more reliable to take that option.

+1

And if you need a newer version for whatever reason it's generally preferable to use a PPA like X-edgers. Not even Arch/Manjaro requires you to run an installer like you normally would in Windows. And also the downside of installing the way you're trying to is that you have to repeat the process for every new kernel (unless you add dkms modules)...

---

