---
title: "What’s the difference between apt-get and snap for installing software"
date: 2024-12-03
forum: New to Ubuntu
---

### Post by monike on 2024-12-03
Hi! I’m new to Ubuntu and Linux in general. 
I’m trying to install software from the terminal, but I’m confused about the difference between apt-get and snap. 
Can someone explain what they are and when I should use each?

---

### Post by guiverc on 2024-12-03
Applications and more are packaged as packages, and Ubuntu allows you to use different package types.

Debian & Ubuntu default to the *deb *package type, which are handled by the `dpkg` command, which is a tool that cannot handle downloading packages, just installing. The `apt-get` tool is an easier front-end that can download & install a package.

From `man apt-get` on my release its described as 

> 
apt-get is the command-line tool for handling packages, and may be considered the user's "back-end" to other tools using the  APT library. Several "front-end" interfaces exist, such as aptitude(8), synaptic(8) and wajig(1).

Snap however is a different sort of package, with the `snap` command intended for dealing with those *snap* packages. From `man snap`

> 
The  snap command lets you install, configure, refresh and remove snaps.  Snaps are packages that work across many different Linux distributions, enabling secure delivery and operation of the latest apps and utilities.


FYI:  The only reason I mention 'my release' when I pasted the quotes; as manual pages can change slightly between releases, as I don't know your release I just copy/pasted from my *plucky* system/release. The detail should be identical; but there is tiny chance its not.

System packages for the main Ubuntu releases will be *deb* packages; so any system related tool will require the `apt` or `apt-get` command (or if you already downloaded it you can use `dpkg`). For user apps you can also use that tool.

If using a Ubuntu Core system however, which doesn't use *deb* packages you need to use the *snap *command as the system can only handle *snap* packages. Of course on these systems all user applications are also *snap* packages.

Some applications only come in *deb* format, some only come in *snap* format, so use the appropriate command. Some applications give you a choice; so use whichever is best for your install purposes (*this can vary on your product & usage; ie. Server, Desktop, want the latest version OR lightest for your system if resources are lacking etc; we have choice*).

There are other package types including *AppImage*, *Flatpak*, and there are further options too.

---

### Post by Dennis N on 2024-12-03
Copy "explain flatpak, snap, deb and rpm packaging" into Google Search to get an AI generated comparison of these Linux packaging types.

---

### Post by grahammechanical on 2024-12-04
You do not tell us what version of Ubuntu you are using. It is always useful to us to know the version of Ubuntu or its Flavors

Another aspect of running a Linux operating system is updating the system and the applications in it. If you use the Software Updater application it will update both deb packages and snap packages. It will also remove system packages that have been installed and are no longer required. It does this because it runs 4 commands that would otherwise have to be run from the terminal.

```
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo snap refresh
```

What applications do you want to use a terminal to install? Ubuntu has software repositories that contain many, many applications that are tested. It is best to install applications that are in the Ubuntu repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

We can use the terminal to install applications that are not in the Ubuntu repositories. There could be a level of risk in doing that. How well do you trust the author of the software?

The App Center in Ubuntu 24.04 LTS will primarily offer snap packaged applications but the search can be filtered to offer Debian packaged applications. For example, search for Web Browser and then select See all results for "Web Browser." Then change Filter By from Snap packages to Debian packages.

Regards

---

