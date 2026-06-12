---
title: "virtualbox always crashes when running autocad 2007"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by kaston on 2008-04-22
subject says it all.  i run autocad 2007 using virtualbox and it consistently crashes and causes me a lot of lost work.  what can i do to make it more stable?

---

### Post by skymera on 2008-04-22
Maybe not enough graphic memory assigned to the virutal machine?
Or not enough system memory in general?

---

### Post by sdennie on 2008-04-22
Also, what version of VirtualBox are you using?  On older versions there was a bug with the QT interface and it would randomly crash if you were using gnome and hadn't setup a proper QT (KDE) theme.

---

### Post by kaston on 2008-04-22
i'm using virtualbox 1.5.0_OSE.  looks like there is a newer version available so i'll try to upgrade.  not sure how to allocate more memory to it yet but i'll try that too

---

### Post by kaston on 2008-04-22
quick questions:  

i went to the virtualbox download page here:  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) but where do i go to dl the binary for the OSE version?  i only see binaries for the "normal" closed source version.  

also, when i install the newer version, will it remember my current settings?  and how come synaptic didn't upgrade me automatically?

---

### Post by sdennie on 2008-04-22
If you are using the version in synaptic, it will only upgrade for security updates.  If the problem you described is being caused by a lack of QT theme, you could also just install kcontrol and manually set a theme for QT.  So, something like this should help (you'll have to restart virtualbox after this):

```

sudo apt-get install kcontrol
kcontrol

```

From there you can manually set a theme (such as Plastik).

Edit:

And, yes, it will remember your settings if you upgrade.  Though, I think you will have to completely turn off all VMs before you upgrade.

---

### Post by kaston on 2008-04-22
what is a "qt theme"?

i'd like to just upgrade to the newest version of vbox if possible.  where can i get the latest version of the OSE vbox?

good to know that my settings will be preserved.

---

### Post by sdennie on 2008-04-22
QT is the KDE equivalent of gtk.  It basically determines how buttons/menus/etc like that appear on your screen.  VirtualBox is a QT app so, if you are running gnome (Ubunutu and not Kubuntu), you'll notice that it doesn't look the same as the rest of your apps because it's using a different mechanism for getting it's themes (QT).

I don't think you will be able to directly upgrade the OSE version of VirtualBox if you got it from synaptic.  I think your only options are to uninstall the OSE version and install a version from the VirtualBox website or, custom compile your own OSE version (in either case you'd have to uninstall the version you have installed at the moment).

The other thing you could try would be to run VirtualBox from the commandline with VBoxSDL and VBoxManage and see if you still have the crashing problem.

To start a VM from the commandline:
```

VBoxSDL -vm "name of your VM"

```

To save the machine state it's:
```

VBoxManage controlvm "name of your VM" savestate

```

---

### Post by Can+~ on 2008-04-22
> **vor said:**
> 
```

sudo apt-get install kcontrol
kcontrol

```

From there you can manually set a theme (such as Plastik).

You don't need the whole Kcontrol for it, qt3-qtconfig is enough (runs with qtconfig-qt3)

---

