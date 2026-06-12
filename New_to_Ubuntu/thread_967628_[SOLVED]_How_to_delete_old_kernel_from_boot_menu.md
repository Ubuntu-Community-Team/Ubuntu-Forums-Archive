---
title: "[SOLVED] How to delete old kernel from boot menu"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by mal_conductor on 2008-11-02
I get this when I boot up:

Ubuntu 8.04.1, Kernel 2.6.24-21-generic
Ubuntu 8.04.1, Kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, Kernel 2.6.24-19-generic
Ubuntu 8.04.1, Kernel 2.6.24-19-generic (recovery mode)

I have upgraded the kernel from 19 to 21.
I have removed 2.6.24-19 using the Synaptic Package Manager.

How do I remove the 2.6.24-19 option from the boot screen?

Regrds,

---

### Post by WRDN on 2008-11-02
Open the Terminal and type:

```
gksudo gedit /boot/grub/menu.lst
```

Now comment out, or remove the relevant entries for the kernels you have removed, save the file, and you're done.

---

### Post by fooman on 2008-11-02
easiest way is to install startupmanager.  it is in synaptic,  or install it in a terminal:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager

open it and under the "advanced" tab you will see an option for "number of kernels".  put a check next to it and choose "1".  close startup-manager (give it a minute to make the change).

hope that helps.

---

### Post by Paqman on 2008-11-02
There's a few different ways:

[list]
[*] If using Intrepid, use the "cruft remover" to get rid of the old kernels.
[*] On any version, use Synaptic to remove the kernels (linux-image packages), both these methods also clean up the Grub menu automatically.
[*] Use startupmanager. Very good tool.
[*] Edit /boot/grub/menu.lst manually. This is the old-school way to do it, and doesn't remove the actual kernels.
[/list]

---

### Post by mal_conductor on 2008-11-02
Thank you all,  this is great.

---

### Post by bobdobbs on 2008-11-03
> **Paqman said:**
> There's a few different ways:


If using Intrepid, use the "cruft remover" to get rid of the old kernels.



I would not advise using cruft remover.
In it's current state it seems to remove random packages that are in use.

I just ran it, because I stupidly assumed that it do the same thing as
'apt-get clean'.

It removed skype.
Other people on the forums have been seeing this behaviour as well.
I'd shed more light on it if I knew more.

But unless one does know more, it would pay to be cautious about cruft-remover.

---

### Post by Paqman on 2008-11-03
> **bobdobbs said:**
> 
But unless one does know more, it would pay to be cautious about cruft-remover.

Yes, it will remove anything from outside the Ubuntu repos, because it can't identify them. However, for removing kernels, it does a fine job.

It lists what it will remove, so anything you want keep, simply uncheck them.

---

### Post by mal_conductor on 2010-08-14
NEW FOR Lucid Lynx

 Re: OS Order
There is no menu.lst in the current ubuntu. Instead it is grub.cfg.
Though it is not recommended to edit directly, you can do it as follows:
In gnome-terminal type

Code:

sudo gedit /boot/grub/grub.cfg

search for
Code:

 set default="0"

change this zero to your windows entry ( grub menu entry minus one)

Example: If you see your windows entry in 4rd place in grub menu, set default="3"

save & exit

---

