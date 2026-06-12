---
title: "New kernel 3.0 rc4 in Launchpad"
date: 2011-06-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-25
The new rc4 of the linux kernel 3.0-2.3 has arrived into Launchpad.
You can download it from here (the state is new):
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-2.3](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-2.3)

> linux (3.0-2.3) oneiric; urgency=low
  [ Andy Whitcroft ]
  * ubuntu: AUFS -- update to 0e2bafab74f0d1463383faeb93f9fc5eb8c2c54e
  [ Leann Ogasawara ]
  * rebase to v3.0-rc4
  * [Config] updateconfigs after rebase to 3.0-rc4
  * fix ERROR: __devcgroup_inode_permission undefined
  [ Stefan Bader ]
  * SAUCE: iscsitarget: Remove driver from the kernel
  [ Tim Gardner ]
  * SAUCE: rtl8192se: Force a build for a 2.6/3.0 kernel
  * [Config] Add grub-efi as a recommended bootloader for server and
    generic
    - LP: #800910
  [ Upstream Kernel Changes ]
  * Fix node_start/end_pfn() definition for mm/page_cgroup.c
  [ Leann Ogasawara ]
  * rebase to v3.0-rc4

---

### Post by VinDSL on 2011-06-25
Why you keep getting me into trouble?  LoL!  :D

I just recovered from last night's escapade - 7.10.3-0ubuntu4 / 275.09.07-0ubuntu2

Okay, so here we go again...

Wish me luck!

---

### Post by VinDSL on 2011-06-25
Works...

```

vindsl@Zuul:~$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
Sat Jun 25 00:38:15 MST 2011
Ubuntu oneiric (development branch)
**[COLOR="Red"]Linux 3.0-2-generic[/COLOR]**
unity 4.0.1
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 275.09.07

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

Built just fine, and survived a cold boot.

Thanks, again, Harry!

---

### Post by Harry33 on 2011-06-25
VinDSL,

Yes it seems to work realy well.
But hey, there are other problems ahead.
Did you see the packages gnome-desktop3-data (3.1.2-0ubuntu1), libgnome-desktop-3-2 (3.1.2-0ubuntu1) and gnome-panel + gnome-panel-data (3.0.2-0ubuntu5)?

---

### Post by lucazade on 2011-06-25
> **Harry33 said:**
> VinDSL,

Yes it seems to work realy well.
But hey, there are other problems ahead.
Did you see the packages gnome-desktop3-data (3.1.2-0ubuntu1), libgnome-desktop-3-2 (3.1.2-0ubuntu1) and gnome-panel + gnome-panel-data (3.0.2-0ubuntu5)?

Not able to update gnome-panel and evolution here.. I don't recall now which dependencies hell was.

---

### Post by afv on 2011-06-25
> **VinDSL said:**
> Why you keep getting me into trouble?  LoL!  :D

I just recovered from last night's escapade - 7.10.3-0ubuntu4 / 275.09.07-0ubuntu2

Okay, so here we go again...

Wish me luck!

How did you install it? *linux-headers-3.0-2-generic* depends on *linux-headers-3.0-2*, that doesn't "exist" yet ([https://launchpad.net/ubuntu/oneiric/+package/linux-headers-3.0-2](https://launchpad.net/ubuntu/oneiric/+package/linux-headers-3.0-2)).

---

### Post by VinDSL on 2011-06-25
> **afv said:**
> How did you install it? *linux-headers-3.0-2-generic* depends on *linux-headers-3.0-2*, that doesn't "exist" yet [...]
I navigated to:  [INDENT][https://launchpad.net/ubuntu/+source/linux/3.0-2.3/+build/2590257](https://launchpad.net/ubuntu/+source/linux/3.0-2.3/+build/2590257) (i386 build of linux 3.0-2.3 in ubuntu oneiric RELEASE)[/INDENT]


Then, I downloaded:

```

linux-headers-3.0-2_3.0-2.3_all.deb
linux-headers-3.0-2-generic_3.0-2.3_i386.deb
linux-image-3.0-2-generic_3.0-2.3_i386.deb

```

To initiate the build:

```
sudo dpkg -i *.deb
```


To test it (after a cold boot):

```
date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
```

---

### Post by VinDSL on 2011-06-25
> **Harry33 said:**
> Did you see the packages gnome-desktop3-data (3.1.2-0ubuntu1), libgnome-desktop-3-2 (3.1.2-0ubuntu1) and gnome-panel + gnome-panel-data (3.0.2-0ubuntu5)?
Heh!

Batten down the hatches!

There's rough water ahead...  :D

---

### Post by afv on 2011-06-25
> **VinDSL said:**
> I navigated to:  [INDENT][https://launchpad.net/ubuntu/+source/linux/3.0-2.3/+build/2590257](https://launchpad.net/ubuntu/+source/linux/3.0-2.3/+build/2590257) (i386 build of linux 3.0-2.3 in ubuntu oneiric RELEASE)[/INDENT]


Then, I downloaded:

```

linux-headers-3.0-2_3.0-2.3_all.deb
linux-headers-3.0-2-generic_3.0-2.3_i386.deb
linux-image-3.0-2-generic_3.0-2.3_i386.deb

```

[…]


Ah, there's the *linux-headers-3.0-2_3.0-2.3_**all**.deb*!

I was looking for it at the amd64 build ([https://launchpad.net/ubuntu/+source/linux/3.0-2.3/+build/2590255](https://launchpad.net/ubuntu/+source/linux/3.0-2.3/+build/2590255)). Thanks! :)

---

### Post by jfernyhough on 2011-06-25
> **jarryslink said:**
> just install a  Linux Kernel 3.0 rc2 I need the &#8220;module-init-tools 3.13&#8243; but i have a module-init-tools 3.12 in Ubuntu 11.04 how to resolved the problem?&#8230; thank
Go here: [https://launchpad.net/ubuntu/oneiric/+source/module-init-tools](https://launchpad.net/ubuntu/oneiric/+source/module-init-tools) , look under Binary packages, and grab the one for your architecture.

---

