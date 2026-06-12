---
title: "Add/Remove apps?"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-08
Hi,

I tried installing various apps like AV, Browsers root kit detectors etc.

My question is that I uninstalled some, need to remove some...To summarize is there any way to clean up the fresh install & remove the left overs like Revo in windows.

OR have the options to reinstall Ubuntu since am new, havent installed any thing personal on this machine.......

Hoping to hear your suggestions, views.

Thanks.

---

### Post by Lars Noodén on 2012-10-08
If you take a snapshot *before* you start messing around you can restore to the packages as the were.

```

dpkg --get-selections > my-packages

```

To restore

```

sudo dpkg --clear-selections
sudo dpkg --set-selections < my-packages
sudo apt-get dselect-upgrade

```

---

### Post by MG&amp;TL on 2012-10-08
> **Yezinki said:**
> Hi,

I tried installing various apps like AV, Browsers root kit detectors etc.

My question is that I uninstalled some, need to remove some...To summarize is there any way to clean up the fresh install & remove the left overs like Revo in windows.

OR have the options to reinstall Ubuntu since am new, havent installed any thing personal on this machine.......

Hoping to hear your suggestions, views.

Thanks.

Reinstallation is a perfectly viable option, but not necessary in this instance.

If you just want to remove the no-longer-needed dependencies and 'clutter' that come with uninstalled applications, the following command (press Ctrl-ALt-T, type into purple box that arrives) should work pretty well.

```
sudo apt-get autoremove
```

---

### Post by audiomick on 2012-10-08
I would like to add the following to the previous post:

First of all, if you haven't yet used "sudo", don't be confused when you don't see your password when you type it in when it is requested. You wont see what you type, but it does go in. Type your password then hit enter.

You can look into the various options for apt-get (as for any command) with the man page.

Do
```
man apt-get
```

You should also look at the options "remove" and "purge". I think purge might even be more suitable for what you want.

I believe the command is
```
sudo apt-get purge <package name>
```

If you want a GUI solution, you might like to install synaptic. When you select a package in synaptic and apply the option "completely remove", it invokes "purge", I believe.

---

### Post by Bölvaður on 2012-10-08
I second this approach
> **audiomick said:**
> If you want a GUI solution, you might like to install synaptic. When you select a package in synaptic and apply the option "completely remove", it invokes "purge", I believe.
Just go into the ubuntu software (store?center?repository?) and get Synaptic. In order to be allowed to install anything with Synaptic you need to give it permission to, so hold in Alt+F2 and write in ```
gksu synaptic
``` which is basically a **gr**aphical **su**do command. From there you can search for the programs and packages you installed and just click purge and then apply to purge out all files and configs related to the package. If you uninstall normally config files will be kept, there is no other difference between 'purge' and 'remove'.

---

### Post by Yezinki on 2012-10-08
Thanks.

---

