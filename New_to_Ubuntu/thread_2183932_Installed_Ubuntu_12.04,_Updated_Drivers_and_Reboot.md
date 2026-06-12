---
title: "Installed Ubuntu 12.04, Updated Drivers and Rebooted when prompted... now in TTY"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by bunkie.lover on 2013-10-27
Hello,

I installed x64 12.04 Precise from the Live CD. It's a dual-boot with Windows 7 x64. I have an NVIDIA Geforce GTX 460 card, and two monitors.

After installing Ubuntu, I was prompted to install better drivers. I was warned that they were closed source, but that they were "tested". The list seemed to repeat twice (including which driver was currently "Active"). I selected one of the two marked "RECOMMENDED" and "Activated" it. I was then prompted to reboot (I also had a reboot pending from installing the ~150 updates).

After rebooting, if I go into Ubuntu it only gets as far as a tty prompt. I've searched these forums and tried a bunch of recommended solutions to situations that seemed pretty similar, but no luck.

I think what I want to do now is just roll back those drivers and run the "nouveau" ones (or whatever it was it shipped with). Alternatively, I've downloaded the latest drivers for my card from nvidia.com using Windows (which still works), so I could try updating to those... only I have no idea how to do this from the command line.

I'd appreciate any help. Thanks.

---

### Post by bunkie.lover on 2013-10-27
Some notes, because I have no idea what I'm doing:

```

me@host:~$ unity
WARNING: no DISPLAY variable set, setting it to :0
compiz (core) - Fatal: Couldn't open display :0
unity-panel-service: no process found

```


```

me@host:~$ startx

/etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: server error

```

Making progress?

```

me@host:~$ sudo apt-get install xserver-xorg-lts-precise #because it sounded good
<snip>
me@host:~$ startx
# black screen, cursor is present.

```

Unfortunately, I'm stymied.

---

### Post by bunkie.lover on 2013-10-27
I think I maybe got it working!

```

me@host:~$ sudo apt-get install gdm
<snip>
me@host:~$ sudo dpkg-reconfigure gdm # I think this happened automatically, honestly
me@host:~$ sudo reboot

```

I was able to log in with gdm, and then launch a terminal, in which I:

```

me@host:~$ rm ~/.Xauthority # I had actually renamed this to .Xauthority.backup earlier, so it's super-weird to me that this should have done anything.
me@host:~$ sudo dpkg-reconfigure lightdm
me@host:~$ sudo reboot

```

(I also installed and removed about a thousand different packages during this process, but the above is what *seems* to have done the trick.)

---

### Post by warp99 on 2013-10-27
You can use apt-get to remove the nvidia packages from the system and everything should revert to the open drivers.

```
:~$ sudo apt-get remove nvidia*
```

---

