---
title: "Want to boot with no xserver, no GUI."
date: 2012-04-12
forum: New to Ubuntu
---

### Post by guilleme on 2012-04-12
Hi! Well, the thing I want to do is to be able to boot my computer with no Xserver running, and therefore no GUI at all (I want it to boot on a CLI), but I want to be able to use a GUI such as gnome if I decide to. 
Have you read Neal Stephenson`s Criptonomicon? In the third book, there is a chapter in which he describes how his character`s computer boots, and describes the computer booting on a CLI by default, and starting a full GUI when startx is inputted. That`s what I want to do. 
I have done some research, and tinkered a bit with the xorg.config file, but then I realized that was not the file I was looking for, the information there affects xorg after it has been started, and I wanted to prevent it from starting. 
Now, it is possible to get completely rid of the xserver by running ```
sudo apt-get remove --purge xserver-xorg
```, but that would just nuke the GUI out until you reinstall it, and I`m looking for a way to run a GUI when I want, not just to have a CLI by default. 
Thank you very much for reading, and any help or suggested reading is very appreciated. 
(Humm, there seems to be a lot of material about this on the net, but most of it applies only to old versions and distributions, have we as a community lost interest on this subject?).

---

### Post by eriktheblu on 2012-04-12
No experience, but I think you'll want to try
```
sudo gdmsetup
``` and look through those options.

---

### Post by ajgreeny on 2012-04-12
This will depend on your version of Lubuntu, but in 11.04 if you use command ```
sudo chmod -x /etc/init.d/lxdm
``` it wil make that file non-xexcutable, so no login screen from lxdm will apear. You can then login to cli and use ```
startx
``` when needed for the lxde gui.

I think 11.10 uses lightdm in place of lxdm, so search your system to find what you have as display manager, and do the same for that instead of lxdm.

I am sure there are other ways to do it, but this will work, even if it's not the only way.

---

### Post by lykwydchykyn on 2012-04-12
AFAIK the correct way to disable services at startup in Ubuntu is to edit their startup scripts in /etc/init/.  

It used to be (and still is, in Debian and some other distros) that you'd use a utility called update-rc.d to configure services, or else just add/delete symlinks to /etc/rc.X directories.  But that's (mostly) gone on Ubuntu.

Basically, to disable lxdm at startup, you edit /etc/init/lxdm.conf and find this:
```

start on ((filesystem
    and runlevel[!06]

```

And change that to:
```

start on ((filesystem
   and runlevel[!026]

```

Basically, you are adding "runlevel 2" to the list of conditions under which lxdm will *not* start.  Runlevel 2 is the default runlevel of Ubuntu.

lightdm works the same way, though you edit /etc/init/lightdm.conf instead, of course.

EDIT: I've found that in newer versions of Ubuntu there's an even cleaner way of disabling a service.  Basically create a file /etc/init/servicename.override and put the word "manual" in it.  So in this case, you want to create /etc/init/lxdm.override and simply put "manual" in the file.  This command will do just that:

```

echo manual |sudo tee /etc/init/lxdm.override

```

Note that there might be some complications during boot due to Plymouth -- probably it's going to sit at the plymouth animation forever until you hit ctrl-alt-f1 or esc or something.

---

### Post by guilleme on 2012-04-17
Well, thanks o all for your responses. 
I`m disappointed by myself because I must say I couldn`t "get it". 
I tried your suggestions, and didn`t work, I tried changing filenames and service running moments, didn`t work either. 
I`ll get back on this problem in some time, in a time I have more free time to burn, and I`m ain`t fed up with X server`s obstinacy to keep starting. :).

---

### Post by Statia on 2012-11-21
Hi!
Did you ever fix this?
Because I am trying to achieve the same for a machine that is going to be used as a server.

---

### Post by Wim Sturkenboom on 2012-11-21
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
Edit the file /etc/default/grub (you need root permissions so use sudo / gksudo and find the line in red; append the word text after 'quiet splash' so it reads 'quiet splash text'.

Next run _sudo update-grub_.

---

### Post by Statia on 2012-11-23
It works!
What black magic is this? ;-)
How can a boot loader tell the X server to start or not start?
I'm getting old, I just don't understand Linux any more.
In the old days I understood how things worked. I fired up my Pentium 200MHz and lilo would boot the kernel, the kernel would run init and I could put my desired runlevel in inittab.
Now we have bootloaders who can do that.
Black magic! Heresy!

---

### Post by Wim Sturkenboom on 2012-11-23
> 
What black magic is this?
...
...
Now we have bootloaders who can do that.


In the past, you could use the bootloader to tell init to use a certain runlevel (to override the one in inittab). I assume this is more or less the same (although I don't know the details and hence it's black magic for me as well).

---

### Post by Statia on 2012-11-25
> **Wim Sturkenboom said:**
> In the past, you could use the bootloader to tell init to use a certain runlevel (to override the one in inittab). I assume this is more or less the same (although I don't know the details and hence it's black magic for me as well).

Ah yes, now you mention it I think I remember.

> A running system can be taken to single user mode by using the telinit command to request run level 1 as follows:   telinit 1 
  It can be entered when the system boots by giving the word "single" or  "emergency" on the kernel command line.  This can be done at the LILO  prompt after pressing the <TAB> key and entering your selection  with the word "single" after it.  The kernel sends the command line to  the init program and it doesn't use the default run level.  The kernel  command line entry is dependent on how you boot the system.


---

