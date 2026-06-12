---
title: "NVidia Driver Broken"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-12-03
Hi, I just upgrade my ubuntu (Current Operating System: Linux server 2.6.38-13-server) and The NVidia driver doesn't seem to work. I tried different approaches suggested in this forum but it seems I messed it up and can't get it work. Right now I got this Warning:
```

=================WARNING WARNING WARNING WARNING =============
This server has a video driver ABI version of 10.0 that is not 
supported by this NVIDIA driver. Please check 
http://www.nvidia.com for driver updates or downgrade to an X 
server with a supported driver ABI.
==============================================================
```

Anyone could help me out?

EDIT: I run the code below:
```

dkms status

```
and got the information
```

nvidia-173, 173.14.30, 2.6.38-13-server, x86_64: installed
nvidia-173, 173.14.30, 2.6.35-28-server, x86_64: installed
nvidia-current, 270.41.06, 2.6.38-13-server, x86_64: installed

```

Thanks,

---

### Post by flemur13013 on 2011-12-03
[B][URL="http://www.phoronix.com/scan.php?page=news_item&px=OTQ3NA"][SIZE=1]X Server 1.11 Breaks The Video Driver ABI 
[/SIZE][/URL][/B]

maybe a solution below:
[https://bbs.archlinux.org/viewtopic.php?id=126988](https://bbs.archlinux.org/viewtopic.php?id=126988)

---

### Post by Unewbeginner on 2011-12-03
hi thanks. but I still can't get it to work. Could anyone here give me a more detailed solution for this?

---

### Post by paul_in_london on 2011-12-03
Look at the top of your **/var/log/Xorg.0.log** file. In my case it says:
```
[    18.360] 
X.Org X Server 1.11.2.901 (1.11.3 RC 1)
Release Date: 2011-11-28
[    18.360] X Protocol Version 11, Revision 0
```

If it says 1.11, try adding these lines to your **/etc/X11/xorg.conf** file (create it if you don't have one):

```
Section "ServerFlags"
    Option         "IgnoreABI" "True"
EndSection
```

---

### Post by Unewbeginner on 2011-12-03
hi, it's 1.10
```

[   34.271]
X.Org X Server 1.10.1
Release Date: 2011.04.15
[   34.271] X Protocol Version 11, Revision 0

```

---

### Post by paul_in_london on 2011-12-03
> **Unewbeginner said:**
> hi, it's 1.10
```

[   34.271]
X.Org X Server 1.10.1
Release Date: 2011.04.15
[   34.271] X Protocol Version 11, Revision 0

```

Ok, that probably wouldn't help then. When you say the nvidia driver doesn't seem to work, can you be more specific? Does your system boot properly?

What do you get from this command?

```
paul@precise-64:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu precise (development branch)
Release:        12.04
Codename:       precise
paul@precise-64:~$
```

---

### Post by Unewbeginner on 2011-12-03
Hi, I mean I can't get into the graphical mode, which means I can only work in command line. When I run starx command, the message I mentioned in my first thread showed.
```

Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty

```

---

### Post by paul_in_london on 2011-12-03
> **Unewbeginner said:**
> Hi, I mean I can't get into the graphical mode, which means I can only work in command line. When I run starx command, the message I mentioned in my first thread showed.
```

Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty

```

Ok, are you using any ppas?

What is your output from this command:

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 290.10-0ubuntu1~xedgers~precise1
  Candidate: 290.10-0ubuntu1~xedgers~precise1
  Version table:
 *** 290.10-0ubuntu1~xedgers~precise1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     285.05.09-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```

Try running these commands and maybe you'll get an update for your nividia driver:

```
sudo aptitude update
sudo aptitude full-upgrade
```

When you've done that, you could consider upgrading from 11.04 to 11.10 by doing this:

```
sudo do-release-upgrade
```

---

### Post by Unewbeginner on 2011-12-03
Hi Paul, thanks for your reply. I think I just fixed it following the guide of this page ([http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)).

I just removed all my nvidia drivers and installed nvidia-current. It works for me now.

---

### Post by paul_in_london on 2011-12-03
> **Unewbeginner said:**
> Hi Paul, thanks for your reply. I think I just fixed it following the guide of this page ([http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)).

I just removed all my nvidia drivers and installed nvidia-current. It works for me now.

Oh, ok. That's good. So you didn't have nvidia-current installed before? If you do want to run the command to update to 11.10 make sure you run those two aptitude commands first :)

---

