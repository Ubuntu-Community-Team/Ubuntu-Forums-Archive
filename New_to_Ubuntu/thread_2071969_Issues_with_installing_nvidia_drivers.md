---
title: "Issues with installing nvidia drivers"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Akennard on 2012-10-16
Lets start from the beginning; I was having trouble with a new Ubuntu 12.04 OS installed on my HP dv6000 laptop. The screen would freeze and only the cursor would work. So I did my research and found out the problem was the nvidia drivers. So I go to my terminal and install the driver or re-install the current driver. I'm not sure what i did  but I used the command "sudo apt-get install nvidia-current". Well it did its thing and now I have no GUI icons! In addition when I try to open the terminal that freezes. I can log in using my password but all I get is the nice ferris wheel wallpaper but no GUI icons. I can no longer make the thing work. So what the hell happened?](*,)](*,)](*,)](*,)](*,)

---

### Post by shreepads on 2012-10-17
When you say you installed the driver from Terminal how exactly did you do this, from a terminal window in a running desktop environment?

Usually I do NVidia proprietary driver installs from safe mode and it works well. If you did this from safe mode and still have problems, the nvidia-current version (295.40 I think) may not be suitable for your graphics card.

Try this:
- Boot, choose the safe mode option in Grub
- From the safe mode menu choose 'Enable Networking' (this will also make the filesystem writable)
- Next choose (from the same menu) drop to root shell
- Now first uninstall nvidia-current

```

# apt-get purge nvidia-current

```

- Next install either nvidia-current (if you installed it from within the desktop environment earlier) else try the nvidia-experimental-304 package for the nearly-latest stable drivers (304.48 ). So

```

# apt-get install nvidia-current

```

OR

```

# apt-get install nvidia-experimental-304

```

Once installed succesfully run 'reboot' to restart, choose the regular (non safe mode) option from Grub menu and cross your fingers and toes..

---

