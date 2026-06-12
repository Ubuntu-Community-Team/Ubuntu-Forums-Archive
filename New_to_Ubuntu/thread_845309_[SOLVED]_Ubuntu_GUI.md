---
title: "[SOLVED] Ubuntu GUI"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by WallyWest on 2008-06-30
Hello,
I am trying to get rid of Hardy's GUI and leave only cmdline as i will be  using an IBM t42 laptop as a temp IP database and do not want nor need any sort of GUI. My hardware doesn't appear to support a server edition of ubuntu so i decided to use hardy-alternate-i386.iso  from this address....

[http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu-cd/hardy/daily/current/](http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu-cd/hardy/daily/current/)

I have been looking on Google for a solution and tried a few "solutions" but have been unsuccessful (probably an error between the chair and the keyboard.) So i figured id ask for someone's help.

---

### Post by appi2012 on 2008-06-30
I'm pretty sure that 
```
sudo apt-get remove ubuntu-desktop
```
should work but i'm not sure, so don't try this unless some other more experienced users tell you to do the same.

---

### Post by sisco311 on 2008-06-30
Boot the alternate cd and select the *Install a command-line system *option.
This will install a minimal command line system whitout any GUI.
[URL="http://www.psychocats.net/ubuntu/purexfce"]
[/URL]

---

### Post by damis648 on 2008-06-30
> **appi2012 said:**
> I'm pretty sure that 
```
sudo apt-get remove ubuntu-desktop
```
should work but i'm not sure, so don't try this unless some other more experienced users tell you to do the same.

Ubuntu-desktop is a meta package. Removing it will simply remove the meta package and not the contained ones.

---

### Post by steveneddy on 2008-06-30
You could try removing ubuntu-desktop in Synaptic.

It should show you a a list of other applications that will be uninstalled also, so be careful while doing this.

Maybe installing Fluxbox before you uninstall Gnome. Flux is a little lighter DE and may server you well.

And you can always just turn off the GUI by going to a tty terminal and typing:

```

sudo /etc/init.d/gdm stop

```

To get to a tty terminal, just 

Ctrl+Alt+F1 - you'll have to logon and password here.

or F2, or F3 - you get the point - up to F6 - F7 is where the GUI resides and F8 are for system messages.

---

### Post by Canis familiaris on 2008-06-30
I would seriously recommend that you to just try editing the default runlevel in the /etc/inittab file so that you boot to a command line by default. And you would not need to disable GUI for it too.

You could select the appropriaye Runlevel.
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

If you wish to start the GUI, just type:
```
startx
```

---

### Post by nick_h on 2008-06-30
Here is a link for mininal and command-line systems.

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

---

### Post by WallyWest on 2008-06-30
Thanks for the many quick responses... ill be sure to post back when i reach a finished product.

---

### Post by WallyWest on 2008-06-30
> **sisco311 said:**
> Boot the alternate cd and select the *Install a command-line system *option.
This will install a minimal command line system whitout any GUI.
[URL="http://www.psychocats.net/ubuntu/purexfce"]
[/URL]

Thanks... this was the easiest and quickest solution. It worked fine. Now my next task is to put together a LAMP... the server script i need to support is PHP so Im going to try and find a quick and painless statement that could get me apache, mysql, and php in one swift kick. 
Thanks again sisco

---

