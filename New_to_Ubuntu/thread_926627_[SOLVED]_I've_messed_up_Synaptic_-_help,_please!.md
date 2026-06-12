---
title: "[SOLVED] I've messed up Synaptic - help, please!"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Absinthe Minded on 2008-09-22
Hello all,

I've just messed up Synaptic Package Manager, somehow.
I've freshly installed xubuntu 8.04.1 (Heron), but every time I reboot, I lose my wireless network connection and need to wipe the passphrase and re-enter it to connect to the internet.

I looked on the web and found that you can install Wicd to solve the problem. The site says tells me to add the repository to the package manager and I did this by adding the following:

```
deb http://apt.wicd.net hardy extras
```

Now, when I start Synaptic, I get this error:

> E: Malformed line 65 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Closing the error window just closes Synaptic, too - so I can't check the repository that I added to see if I've made a spelling mistake.

Any help greatly appreciated.

Cheers,
Nick.

---

### Post by billgoldberg on 2008-09-22
in a terminal:

```
sudo gedit /etc/apt/sources.list
```

--

Remove the line (or uncomment it) you added.

Then do 

```
sudo apt-get update
```

--

You can download a .deb package for WICD here (double click to install the package):

[https://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=heanet&filename=wicd_1.5.2_all.deb&46920181](https://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=heanet&filename=wicd_1.5.2_all.deb&46920181)

It must be noted that you first need to remove network-manager before wicd can be installed.

WICD will start on boot. To launch the GUI for it, use wicd-client or use the applications menu.

---

### Post by Absinthe Minded on 2008-09-22
Hi Bill,

Thanks for the quick reply. It asks for my password, I enter and here's what I get:

```
sudo: gedit: command not found
```

Cheers,
Nick.

---

### Post by plucky on 2008-09-22
> **Absinthe Minded said:**
> Hi Bill,

Thanks for the quick reply. It asks for my password, I enter and here's what I get:

```
sudo: gedit: command not found
```

Cheers,
Nick.

Xubuntu does not have gedit.Try ```
sudo nano /etc/apt/sources.list
``` and do as Bill said.

Good Luck

---

### Post by Absinthe Minded on 2008-09-22
Thanks, plucky - works fine.

Sorry about this, but presumably I need to save the terminal contents after editing - how do I do that?

Cheers,
Nick.

---

### Post by unutbu on 2008-09-22
In nano, press Ctrl-X. (The menu bar writes ^X for Ctrl-X).

---

### Post by Absinthe Minded on 2008-09-22
Thanks, unutbu.

I thought that Ctrl-X would close it without saving, so I didn't bother with it! All done now. So, how do I remove network-manager prior to installing wicd? Is this done through add/remove?

Thanks again!
Nick.

---

