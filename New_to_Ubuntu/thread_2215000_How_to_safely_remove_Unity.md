---
title: "How to safely remove Unity?"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by newbietwo on 2014-04-04
Hello, new to Ubuntu 13.10 and really enjoying it.

I prefer Cinnamon 2.0 to Unity and wanted to know if there is a safe way to remove Unity and Firefox without removing needed dependencies?

Thanks.

---

### Post by 3rdalbum on 2014-04-04
I've never found the desire to remove Unity, so I've never tried this, but 'sudo apt-get remove unity*' should do the job without accidentally removing the libraries for Brasero and other programs compiled against Unity.

Removing Unity is probably unnecessary. You can have Cinnamon and Unity installed concurrently and just log into the one you want to use.

---

### Post by mikewhatever on 2014-04-04
It's hard to say without knowing what dependencies you need. Can you tell us?

---

### Post by Double.J on 2014-04-04
Hi there!

i am wondering if, going forward this is the best solution. Here's what we know:
unity is a front end to gnome desktop.
as of 2.0 cinnamon is a complete de - gnome desktop is not used.
Unity is expected to migrate to the MIR display server in later releases.
cinnamon has not yet decided it's path, but it has close ties to the mate desktop project who have decided along with kde to primarily focus on wayland.

It may be preferable to locate a derivative that focuses on cinnamon or install the base ubuntu system and add the packages you do want.

personally I just put up with doubled up apps!

---

### Post by coldcritter64 on 2014-04-04
> **gnu/mirow said:**
> ...personally I just put up with doubled up apps!

+1, same here. It is often easier dependency wise to leave unity in place and add whatever desktop/s (I usually install several options), and just log into the one you want. 

It is possible to edit desktop config files manually and store them in ~/.local/share/applications (~ is your home folder) to separate different applications into their respective desktop environments menus and not leave a clutter of entries in all the installed desktops. 

Using lines in the config files, like for example, "NotShowIn=", "NoDisplay=(true/false)" and  "OnlyShowIn=" allow you to control IF and WHICH desktop environment menus your applications show up in. Nice clean menus can be attained using such techniques on a per user basis as the config files are in your home directory and are only applied to your user profile, you don't affect other users (if you have any set up that is).

---

### Post by buzzingrobot on 2014-04-04
When another environment is installed and used on Ubuntu --  Cinnamon or whatever -- the components of the Unity interface do not  execute. Removing them simply removes those files from the drive. 

I've gone through this drill a couple of times.  Not by zapping Unity in one big chop, but by removing one or two packages at time, noting what dependencies were pulled out, and reinstalling what I wanted with frequent us of the "--no-install-recommends" option to apt-get. It was a very long and error-prone process.  In the end, I didn't think I'd really accomplished much.

Scopes and a number of applications can be safely removed. But, any thing that has been compiled against a Unity library will very likely trigger some cascading dependencies that will remove packages you probably do not want to remove. Unity is, after all, the default Ubuntu environment.  Even something like Mint hasn't entirely purged every Unity librar

---

### Post by ibjsb4 on 2014-04-04
I find it easier to use the mini.iso and build my own, leaving out things like unity and compiz.

For a gnome only session you can start with a basic build:


```
sudo apt-get install lightdm gnome-terminal synaptic gedit && sudo apt-get install --no-install-recommends gnome-session-flashback nautilus

```

You need to add your web browser to this and other choice packages, this is just the start point.


This works with 13.10 and 14.04

---

### Post by silex89 on 2014-04-04
...Or if you want an Ubuntu experience more tailored to your needs, you can try the Ubuntu Minimal Install [HERE]("https://help.ubuntu.com/community/Installation/MinimalCD"). The ISO contains a CLI wizard that will guide you to install the components, packages and desktop environments that you want. Nothing more and nothing less and it's only 30MB. How cool is that! :D

SIDE NOTE: It WILL take a considerable amount of time since it need to download the packages and install them with dpkg, so be sure to have enough coffee and a comfortable couch if you want to try this.

Best of Luck

EDIT: This is not useful for booting in UEFI mode, only for Legacy BIOS mode. See the link I gave you

---

### Post by buzzingrobot on 2014-04-04
When you install with the minimal image, you eventually will be shown a list of a dozen or more 'tasks' you can install.  Note that if you choose 'ubuntu-desktop', you will install Unity.  Ditto kubuntu-desktop (KDE).  I usually select 'openssh-server' which installs a very small number of packages.  Then, reboot and start adding.

---

