---
title: "[SOLVED] Nvidia graphics driver not installing"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-27
Hello,

I am using 8.04 32-bit Ubuntu. 

I tried installing the Nvidia driver as seen in the following link: [http://www.nvidia.com/object/linux_display_ia32_169.12.html]("http://www.nvidia.com/object/linux_display_ia32_169.12.html"). 

During the installation, I got a warning telling me to turn off "X server". I then I tried pasting the following command line into the terminal as the warning showed: "sudo /etc/init.d/gdm stop" as shown in this link: [http://www.linuxforums.org/forum/ubuntu-help/92402-how-close-x-server-nvidia-drivers.html]("http://www.linuxforums.org/forum/ubuntu-help/92402-how-close-x-server-nvidia-drivers.html"). 

Once I entered this, I got a warning stating: "Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.". I checked the nvidia-installer.log and this is what it contained: 

[I]"nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue May 27 19:43:39 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5415'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing."[/I]


I'm not sure whats wrong. Any help is greatly appreciated.

---

### Post by RequinB4 on 2008-05-27
Try stopping X (sudo /etc/init.d/gdm stop) BEFORE you begin installation...

---

### Post by JimmyJim on 2008-05-27
> **RequinB4 said:**
> Try stopping X (sudo /etc/init.d/gdm stop) BEFORE you begin installation...

I tried that and my entire screen went into a black console. I wasn't sure what to do or what it was, so after trying various commands I rebooted. Do you know what I'm supposed to do? If you need me to, I could try it again and handwrite everything that comes up.

---

### Post by RequinB4 on 2008-05-27
Your X server is what allows you to have a graphical interface.  When you type "sudo /etc/init.d/gdm stop" you're SUPPOSED to get a black terminal so you can safely install your new drivers.  Do it again, but when you get to the black terminal, simply
```

cd /path/to/installer/

```

where /path/to/installer/ is where you have the file saved, then

```

sh NVIDIA-Linux-x86-169.12-pkg1.run

```

as per instructions.

Good luck!

---

### Post by iaculallad on 2008-05-27
Post your **uname -a** output.

On the terminal, place the command:

```
uname -a
```

---

### Post by Delever on 2008-05-27
1. Rename your downloaded file which ends with .run to nvidia.run and place to your home directory (i.e. /home/delever)

2. Install libraries for compiling things:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

3. Reset xorg.conf to basic state (if you need some settings in xorg, make backup of it before running this):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4. Log out, Log in. Resolution may have changed.

5. Turn off Gnome Display Manager, this will send you to console.
```
sudo /etc/init.d/gdm stop
```

6. Log in there.

7. Run nvidia installer:
```
sudo sh nvidia.run
```

8. Follow instructions, let it modify xorg.conf when it asks.

9. Restart pc right from there:
```
sudo shutdown -r now
```

I hope I haven't forgot anything. I have done this recently :)

EDIT: modified "libraries" part

---

### Post by JimmyJim on 2008-05-27
> **RequinB4 said:**
> Your X server is what allows you to have a graphical interface.  When you type "sudo /etc/init.d/gdm stop" you're SUPPOSED to get a black terminal so you can safely install your new drivers.  Do it again, but when you get to the black terminal, simply
```

cd /path/to/installer/

```

where /path/to/installer/ is where you have the file saved, then

```

sh NVIDIA-Linux-x86-169.12-pkg1.run

```

as per instructions.

Good luck!

I just tried that and I got the following messages:
"No precompiled kernel interface was found to match your kernel"
"None found on NVIDIA FTP site; installer will need to be compiled"
"ERROR- you do not appear to have libc header files installed on your system. Please install your distribution's libc development package"

I'm not what's wrong there. Also, is there a way to exit that console so I don't have to reboot everytime?

I'll try what Delever said and respond to iaculallad now.

---

### Post by JimmyJim on 2008-05-27
> **iaculallad said:**
> Post your **uname -a** output.

On the terminal, place the command:

```
uname -a
```

It outputs "Linux desktop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux"

---

### Post by Delever on 2008-05-27
> **JimmyJim said:**
> 
I'm not what's wrong there. Also, is there a way to exit that console so I don't have to reboot everytime?


Actually, instead of restarting, you can probably start GDM again:

sudo /etc/init.d/gdm start

---

### Post by JimmyJim on 2008-05-27
> **Delever said:**
> Actually, instead of restarting, you can probably start GDM again:

sudo /etc/init.d/gdm start

:lolflag: makes sense

I'm trying the method that you previously mentioned now.

---

### Post by iaculallad on 2008-05-27
> **JimmyJim said:**
> It outputs "Linux desktop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux"

On the terminal, issue the command:

Code:

> sudo apt-get install linux-restricted-modules-generic

afterwards, re-install your NVIDIA driver or use the Restricted Drivers Manager to enable your device. Hope that will work.

---

### Post by RequinB4 on 2008-05-27
> **JimmyJim said:**
> I just tried that and I got the following messages:
"No precompiled kernel interface was found to match your kernel"
"None found on NVIDIA FTP site; installer will need to be compiled"
"ERROR- you do not appear to have libc header files installed on your system. Please install your distribution's libc development package"

I'm not what's wrong there. Also, is there a way to exit that console so I don't have to reboot everytime?

I'll try what Delever said and respond to iaculallad now.

You need to do what Delever said, it should work.

For future reference (do NOT use this while installing)
```

/etc/init.d/gdm start

```

will start it up again.

---

### Post by Delever on 2008-05-27
> **JimmyJim said:**
> It outputs "Linux desktop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux"

btw,

sudo apt-get install linux-headers-`**uname -r**`

is clever way of placing that information into installation command.

---

### Post by JimmyJim on 2008-05-27
Delever's method worked! :) Thanks a lot everyone. To anyone else in the future that may read this for help, I'm sure iaculallad's method would work as well. The only difference (I think) is that I installed from a file rather than an automatic installation.

One more thread will be coming up based on sound. Thanks again everyone.

---

### Post by Delever on 2008-05-27
You will need to do that after every kernel update, so if you see that one incoming, you better get ready before updating ;)

kernel = linux

---

### Post by JimmyJim on 2008-05-27
> **Delever said:**
> You will need to do that after every kernel update, so if you see that one incoming, you better get ready before updating ;)

kernel = linux

:neutral: How often are there updates? How do I know if an update is coming out? What will happen if I do not update it?

---

### Post by Delever on 2008-05-27
There will be few, and all of them are security updates. Just check the list before updating for "linux-image-*-generic" and "linux-*-modules-generic". It breaks anything what depends on kernel modules (kernel modules must be compiled against current kernel). For me, it includes nvidia drivers, and virtual machines.

In any case, you should be able to select previous kernel from menu when booting up.

If you are interested what kernel actually contains look it up. It is basically driver superpack.

P.S. I should break the habbit of over editing posts many times after posting :D

---

