---
title: "Some questions about apt..."
date: 2020-10-03
forum: New to Ubuntu
---

### Post by automate-stuff on 2020-10-03
I am using Ubuntu 20.04. I have installed texstudio, Gummi, LibreOffice, Bluefish, Sagemath and Chrome. I upgraded the system like 4 times like this: 

```
sudo apt update && sudo apt upgrade && sudo apt autoremove
```

And I never purged/removed anything!!

As you can see, I forgot to pass the **--purge** argument to **autoremove**, **--purge** gets rid of the setting files under **/etc/**.

My questions are: 

(0) Are there any residues(left-over) files under /etc/ now ? 

(1) Will there be any orphan packages if I only upgraded the system with the apps mentioned above (I never purged/removed anything) ? 

(2) Do the packages I mentioned above create setting files under /etc/ ?

---

### Post by TheFu on 2020-10-04
Have you tested the scenario?  What happens?

Questions of this sort are best answered by the manpage for each program.  The behavior could change over time and since apt is still warning that it isn't a stable interface and shouldn't be used in any scripts/automation, we probably shouldn't use apt in any scripts or automation.

The apt manpage contains this:
```
       autoremove (apt-get(8))
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed as dependencies changed or the package(s) needing them
           were removed in the meantime.

           You should check that the list does not include applications you
           have grown to like even though they were once installed just as a
           dependency of another package. You can mark such a package as
           manually installed by using apt-mark(8). Packages which you have
           installed explicitly via install are also never proposed for
           automatic removal.
```
So, it appears that *apt autoremove* just implements *apt-get autoremove*.
```
       autoremove (and the auto-remove alias since 1.1)
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed.

```
There isn't any mention of purge being an option to autoremove. The apt-get manpage has this:
```
       --purge
           Use purge instead of remove for anything that would be removed. An
           asterisk ("*") will be displayed next to packages which are
           scheduled to be purged.  remove --purge is equivalent to the purge
           command. Configuration Item: APT::Get::Purge.
```

So it appears to be undocumented what using --purge does with autoremove.
I wouldn't worry.

---

### Post by VMC on 2020-10-04
> **automate-stuff said:**
> ...
My questions are: 

(0) Are there any residues(left-over) files under /etc/ now ? 

(1) Will there be any orphan packages if I only upgraded the system with the apps mentioned above (I never purged/removed anything) ? 

...
(0) You might be thinking of "/var/cache/apt"
(1) *deborphan* will find orphans.

---

### Post by Impavidus on 2020-10-04
-1: I never run those commands as a bundle. Each one of them gives feedback, which I use to decide whether to run the next command in the sequence.

0: If apt autoremove removed anything, there may be residual config files. You should be able to tell from the output it gave you. If you didn't pay attention, ask dpkg:```
dpkg --list | grep '^rc'
```If you never removed anything, the only way apt autoremove could have removed something is when apt upgrade upgraded a package that changed dependencies. This happens usually with kernel upgrades, about once every two weeks, and very rarely on other occasions. Note that kernel packages don't actually contain such config files, so although they may be marked as "remove, remaining config", they've been completely removed. Still, you can purge them to get rid of the clutter in dpkg's output.

1: apt autoremove should remove such orphans, if you have any. And maybe it's not clearly documented, but apt autoremove --purge does exactly what you'd expect.

2: At least TeX and LibreOffice put stuff in /etc. I don't know about the others.

---

### Post by automate-stuff on 2020-10-04
So lets say I removed a package without removing its config file....running the following command will show that package: ?

**dpkg --list | grep '^rc'**

In other words, dpkg has a logging system that keeps track of removed packages ?

---

### Post by Impavidus on 2020-10-05
Yes. The package manager (which is a bunch of tools working together with a database) keeps track of the status of every package. This status can be
- not installed
- installed
- configuration files only
and several others that only appear during installation or after your package management tool crashed. dpkg --list lists all packages with their status and grep '^rc' filters the output of dpkg to show only those packages with status rc, which means desired status remove, configuration files remaining.

---

### Post by TheFu on 2020-10-05
For fun, on a 20.04 mate-desktop, I found a package with dpkg -l|grep '^rc' that I was willing to purge. It had already been removed, but left the config files behind.

The package was openvpn.  Inside /etc/openvpn/ was only 1 file - a route-update script. Ran
```
sudo apt purge openvpn
```
answered 'Y'
and the /etc/openvpn/ directory and all files inside were gone.

I'm willing to completely **purge** these packages too: network-manager-gnome network-manager-openvpn update-notifier.  They are already remoted, just the config files aren't.
rc  network-manager-gnome    1.8.24-1ubuntu2 amd64 network management framework (GNOME frontend)
rc  network-manager-openvpn  1.8.12-1 amd64        network management framework (OpenVPN plugin core)
rc  update-notifier          3.192.30 amd64        Daemon which notifies about package updates

```
sudo apt --purge autoremove
```
didn't do anything, so the config files are not considered removable.

```
$ sudo apt purge network-manager-gnome network-manager-openvpn update-notifier
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  network-manager-gnome* network-manager-openvpn* update-notifier*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
**After this operation, 0 B of additional disk space will be used.**
Do you want to continue? [Y/n] y
(Reading database ... 254754 files and directories currently installed.)
Purging configuration files for network-manager-gnome (1.8.24-1ubuntu2) ...
Purging configuration files for update-notifier (3.192.30) ...
Purging configuration files for network-manager-openvpn (1.8.12-1) ...
```

To me, hardly seems worth the effort. The most useful aspect of this is that dpkg doesn't show the 'rc' packages with the config files gone anymore. Hummmmmm. That is slightly interesting.

---

