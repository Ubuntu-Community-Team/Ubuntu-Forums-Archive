---
title: "which version of vim to install?"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by chopra on 2014-08-23
Hi Guys,

I am somewhat new to Linux, and I have been using the vim text editor at work and on my own machine.  I sometimes use the gvim command at work computers to open up a seperate window if I don't want to work in the terminal.

So, I typed the command gvim into my laptop (Ubuntu 12.04 lts), and I get the following message:

The program 'gvim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-athena
 * vim-gtk
 * vim-nox
Try: sudo apt-get install <selected package>

I already have vim and vim.tiny commands on my machine, so I don't understand the first and third options.  Will they overwrite my current vim and vim-related executable files?  
Also, I wasn't sure which of these to install. I currently have the unity desktop that comes as a default with Ubuntu.  I don't like it, but I haven't decided which one I should switch to yet, and I'm not in a hurry to switch.

In other words, I'd hate to get a version like vim-gnome that is only usefull for a specific desktop environment, only to change my desktop environment later on, and have to re-install vim. So, is there a version that's versatile enough, without resorting to a so-called 'stripped-down' version, without the standard funtionality?

Thanks.

---

### Post by grahammechanical on 2014-08-23
What desktop Environment do the computers at your place of employment use? Are you sure that they are not running Gnome. I ask because the Ubuntu software centre describes gvim as a package that contains a version of Vim compiled with a Gnome 2 GUI. and when I search the software centre for vim-gnome I get gvim as the search result.

[http://askubuntu.com/questions/281886/what-is-the-difference-between-the-different-vim-packages-available-in-ubuntu](http://askubuntu.com/questions/281886/what-is-the-difference-between-the-different-vim-packages-available-in-ubuntu)

Regards.

---

### Post by chopra on 2014-08-24
Hi, thanks for the reply.
At my work, they use a version of scientific linux.  I looked it up, and it looks like they do use gnome, which surprised me, because their desktop looks nothing like the ubuntu.

---

### Post by Ksiencha on 2014-08-24
Well, Ubuntu uses Unity, not Gnome desktop environment. (I hope I understood correctly everything you wrote here, my English isn't so strong)

---

### Post by obake2 on 2014-08-24
> **chopra said:**
> Hi, thanks for the reply.
At my work, they use a version of scientific linux.  I looked it up, and it looks like they do use gnome, which surprised me, because their desktop looks nothing like the ubuntu.

Ubuntu is based of Gnome components but uses [Unity Shell]("https://unity.ubuntu.com/about/") instead of [Gnome-Shell]("http://www.gnome.org/gnome-3/"). :)

---

### Post by chopra on 2014-08-24
> **obake2 said:**
> Ubuntu is based of Gnome components but uses [Unity Shell]("https://unity.ubuntu.com/about/") instead of [Gnome-Shell]("http://www.gnome.org/gnome-3/"). :)

Oh, okay.  That makes a lot more sense.  I just found a way to configure the desktop to classic gnome. So if I want to use the gvim command, I would need vim-gnome?
I'm confused as to why it offered:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-athena
 * vim-gtk
 * vim-nox

The first one is just vim, and I gathered from a previous post that gvim applies only to the second option.  So is Ubuntu just too liberal in making suggestions?

---

### Post by nerdtron on 2014-08-25
Why not install install vim-gnome? If it needs dependencies, they will also be installed. If it needs vim, or vim-gtk they will be installed too.

Then try launching gvim. If it still won't launch, then install more packages and so on. No harm done on installing packages as these are all vim packages.

---

### Post by Claus7 on 2014-08-25
Hello,

usually on a new ubu box I install vim. I was able to see that from the offers that you mention:

* vim
* vim-gnome
* vim-**tiny**
* vim-athena
* vim-gtk
* vim-nox

the one in bold is installed in my system along with vim-runtime, vim-common.
Now athena, gtk, gnome, nox are not installed. More information about them you will be able to find under synaptic package manager, which gives a brief description about the packages.

For a graphical environment aside terminal I would use gvim as *nerdtron* mentioned before.

The difference between gtk and gnome can be found here:
[http://askubuntu.com/questions/33260/difference-between-vim-gtk-and-vim-gnome](http://askubuntu.com/questions/33260/difference-between-vim-gtk-and-vim-gnome)

Regards!

---

### Post by Jonathan Precise on 2014-08-26
I have vim-gtk installed, and it's compatible with KDE (to some extent), GNOME (full), XFCE (*think* it's compatible), and LXDE (*think* it's compatible).

---

### Post by chopra on 2014-08-30
Hey guys.  I installed vim-gnome, and it works fine.  Thanks for the help.

---

