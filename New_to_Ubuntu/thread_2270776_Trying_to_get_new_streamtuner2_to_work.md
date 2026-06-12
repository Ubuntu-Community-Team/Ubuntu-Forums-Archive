---
title: "Trying to get new streamtuner2 to work"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by send2 on 2015-03-25
Hi all,

First of all, I am running Trusty Tahr 14.04 LTS version.

I just installed Streamtuner2 version 2.1.4. The program gets stuck at the begining "loading xiph" and goes no further. I first ran in terminal the program and I got the following:

```
Please install the packages python-lxml and python-pyquery from your distributions software manager
```

I checked in Synaptic for those packages, I had python-lxml already but had to install python-pyquery. I ran the program again thru terminal and this time I got the following:
```
  streamtuner2

/usr/bin/streamtuner2:143: GtkWarning: IA__gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed

  gtk.Builder.add_from_file(self, conf.find_in_dirs([".", conf.share], ui_file)), gui_startup(2/20.0)

/usr/bin/streamtuner2:145: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

  self.extensionsCTM.set_submenu(self.extensions)  # duplicates Station>Extension menu into stream context menu  
```

 
what to do now?

thanks for any pointers.

---

### Post by dino99 on 2015-03-25
Looks like 14.04 is too old to provide the required packages versions; might work with vivid (which is the best release i've met and used)

---

### Post by send2 on 2015-03-25
> **9d9 said:**
> Looks like 14.04 is too old to provide the required packages versions; might work with vivid (which is the best release i've met and used)

Thanks for your reply 9d9,
  
as I understand it, vivid is for Kubuntu (I think) and I am using Ubuntu, don't really want to change distros for just one application, my previous drive crashed and now I have the new LTS edition, just intalled it, don't want to go trough all of that again any time soon :)

---

### Post by mc4man on 2015-03-25
The 2.1.4 .deb is poorly packaged but does work here, not a matter of 14.04 being too old. You could also consider using the version in 14.04 or install the .deb from 15.04 (- vivid is not kubuntu only, it's just an Ubuntu 'point' release on the way to 16.04 & only has 9 months support

If sticking with the .deb you downloaded run this command to get more packages that should be installed
(warnings in a terminal usually aren't fatal & many times can be ignored
```
sudo apt-get install python-lxml python-imaging python-pyquery \
python-keybinder python-gtk2 python-glade2 python-requests
```
scr. from 14.04 Ubuntu

If you want the latest Ubuntu packaged .deb then **first remove the one you installed** & then click here (needs all the above either already installed or Software-center will take care of if used to install.
[https://launchpad.net/ubuntu/+archive/primary/+files/streamtuner2_2.1.3-1_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/streamtuner2_2.1.3-1_all.deb)

---

### Post by xmilky on 2015-03-25
Hi, package author here.
If it hangs on the first startup with "loading xiph", then it has less to do with the Ubuntu version. In fact I'm running it on 14.04.

The Xiph plugin loads from a caching API, which however can be just as slow as the primary Xiph API at times.

If it doesn't work at all, then you could disable the plugin right away.
Create a **~/.config/streamtuner2/settings.json** (if there isn't one already) with:

```
{
    "plugins": { "xiph": false }
}
```

That'll skip initialization.
The trusty version of python-requests and other packages are current enough.

---

### Post by send2 on 2015-03-26
> **mc4man said:**
> The 2.1.4 .deb is poorly packaged but does work here, not a matter of 14.04 being too old. You could also consider using the version in 14.04 or install the .deb from 15.04 (- vivid is not kubuntu only, it's just an Ubuntu 'point' release on the way to 16.04 & only has 9 months support

If sticking with the .deb you downloaded run this command to get more packages that should be installed
(warnings in a terminal usually aren't fatal & many times can be ignored
```
sudo apt-get install python-lxml python-imaging python-pyquery \
python-keybinder python-gtk2 python-glade2 python-requests
```
scr. from 14.04 Ubuntu

If you want the latest Ubuntu packaged .deb then **first remove the one you installed** & then click here (needs all the above either already installed or Software-center will take care of if used to install.
[https://launchpad.net/ubuntu/+archive/primary/+files/streamtuner2_2.1.3-1_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/streamtuner2_2.1.3-1_all.deb)

Thanks mc4man,

I installed all the packages you told me about thru synaptic and I still get the same start up problem, I uninstalled my version and used your link and still same problem. Streamtuner gets stuck at same startup routine.

---

### Post by send2 on 2015-03-26
> **xmilky said:**
> Hi, package author here.
If it hangs on the first startup with "loading xiph", then it has less to do with the Ubuntu version. In fact I'm running it on 14.04.

The Xiph plugin loads from a caching API, which however can be just as slow as the primary Xiph API at times.

If it doesn't work at all, then you could disable the plugin right away.
Create a **~/.config/streamtuner2/settings.json** (if there isn't one already) with:

```
{
    "plugins": { "xiph": false }
}
```

That'll skip initialization.
The trusty version of python-requests and other packages are current enough.

Hi xmilky, 

can you elaborate more on this please? I am new to this procedure. Thanks for your reply and help.

.... I just got the new version to install by modifying the above .config file. Thanks xmilky, that did the trick, can I load xiph after I start the program?

thanks....

---

### Post by xmilky on 2015-03-26
> **send2 said:**
> .... I just got the new version to install by modifying the above .config file. Thanks xmilky, that did the trick, can I load xiph after I start the program?

You can try it again by reenabling the Xiph plugin under **Edit > Preferences > Channel Plugins**, and then restart streamtumer2.

It still sounds like some network connectivity problem though.
Try to open **(1)** [http://api.include-once.org/](http://api.include-once.org/) and **(2)** [http://api.include-once.org/xiph/cache.php](http://api.include-once.org/xiph/cache.php) in your browser first.
The first one should yield a Forbidden message. If not, then it's a provider/routing issue.
If the second URL doesn't start a download, then it could be some form of proxy issue. (The caching server can't be pinged, btw. Which is why it might get blocked by intransparent provider proxies. And it doesn't reply with a dated application/*-MIME type.)

Anyway, I'm going to add a shorter timeout there for the next version.
And reenable the package dependencies (at least for the .deb).

G!

---

### Post by send2 on 2015-03-26
Thanks for your answers xmilky, I will enable Xiph, I did check the two links you gave me and they both worked as you described. Thanks for letting me know about the timeout too.

I really appreciate your help. I will mark this thread closed.

---

