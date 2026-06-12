---
title: "Can't seem to remove Notes through Uninstall button?"
date: 2022-06-16
forum: New to Ubuntu
---

### Post by abdul1337 on 2022-06-16
I get the message saying **no packages to remove**, when trying to uninstall through Ubuntu software. How would i do this in CLI or normal uninstall? 

Was a windows user where uninstall is much simpler, hence the confusion.

---

### Post by Bashing-om on 2022-06-16
abdul1337; Hello

Do you mean the app "note' from the Ubuntu software repository ?

Ubuntu has the notion that you might want to reinstall an application - hence user config files are not removed with a remove operation. To also remove the config files one uses the "--purge" flag to apt:
As in:
```

sudo apt --purge remove note

```

Make sense ?

[INDENT]there is a process[/INDENT]

---

### Post by Holger_Gehrke on 2022-06-17
How to uninstall some software depends on how you installed it. I can think of six different ways to install something of the top of my head - Debian package, snap package, Flatpack, Appimage, pre-compiled binary with installer, and of course installation from source. Ubuntu Software only covers the first two of those (but can be made to cover Flatpack too by installing a plugin).

Holger

---

### Post by ActionParsnip on 2022-06-17
What is "notes" please? There are a number of packages with "notes" in them
[https://packages.ubuntu.com/search?keywords=notes&searchon=names&suite=jammy&section=all](https://packages.ubuntu.com/search?keywords=notes&searchon=names&suite=jammy&section=all)

As Holger_Gehrke says, lots of ways to install applications so we'll need a little more info

---

### Post by abdul1337 on 2022-06-17
I installed it through Ubuntu Software. Didn't touch or use CLI for this.

It called Notes (icon is Yellow sticky paper of 1.1MB size).

Tried uninstalling through Bin icon on Ubuntu Software but it gave the error aforementioned.

---

### Post by Holger_Gehrke on 2022-06-17
If I search for 'notes' in gnome-software I get about 100 hits, but only two have a stack of yellow sticky notes as their icon. One of the two is the XFCE notes panel app (xfce4-notes-plugin) that I use and you don't mention using XFCE. The other is Gnome Notes (gnote), but it's a lot bigger than 1.1 megabytes, about 3.5 mb download and 20 mb installed.
If that's the one, then
```
apt-cache policy gnote
```
in a terminal should show something like
```

gnote:
  Installed: 42.0-1
  Candidate: 42.0-1
  Version table:
     42.0-1 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
assuming you're running Ubuntu 22.04 (the latest LTS release).
In that case a simple
```

sudo apt remove gnote

```
should uninstall it (but as Bashing-om mentioned it will not erase your data or configuration; the --purge option he mentions will only remove system wide configuration which might get left behind without '--purge', user data and user configuration are **never ever** touched by the package manager. When you prefix a command with sudo (**s**witch **u**ser and **do**) the system will ask for **your** password (the one you use to log in) and will not echo anything when you type it in. That's a security measure to stop people standing behind you while you type your password from seeing the length of the password.

Holger

---

### Post by abdul1337 on 2022-06-18
> **Holger_Gehrke said:**
> If I search for 'notes' in gnome-software I get about 100 hits, but only two have a stack of yellow sticky notes as their icon. One of the two is the XFCE notes panel app (xfce4-notes-plugin) that I use and you don't mention using XFCE. The other is Gnome Notes (gnote), but it's a lot bigger than 1.1 megabytes, about 3.5 mb download and 20 mb installed.
If that's the one, then
```
apt-cache policy gnote
```
in a terminal should show something like
```

gnote:
  Installed: 42.0-1
  Candidate: 42.0-1
  Version table:
     42.0-1 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
assuming you're running Ubuntu 22.04 (the latest LTS release).
In that case a simple
```

sudo apt remove gnote

```
should uninstall it (but as Bashing-om mentioned it will not erase your data or configuration; the --purge option he mentions will only remove system wide configuration which might get left behind without '--purge', user data and user configuration are **never ever** touched by the package manager. When you prefix a command with sudo (**s**witch **u**ser and **do**) the system will ask for **your** password (the one you use to log in) and will not echo anything when you type it in. That's a security measure to stop people standing behind you while you type your password from seeing the length of the password.

Holger

Sorry for this as I am new to ubuntu (started 2 days ago). I was trying to upload an image to resolve this issue quickly. The link should tell the error and the app name. Let me know which one this is :S

Don't understand why removing an app from ubuntu is made so to be  complicated. Is there any guide, which you can recommend, tells what uninstallation on ubuntu is opposed to windows?

[https://ibb.co/dr2nMH6](https://ibb.co/dr2nMH6)

---

### Post by Holger_Gehrke on 2022-06-18
As you can probably tell from the fact that my first impulse was to use the command line, I'm not a fan of the "Software" application (and graphical system administration tools in general). I tried installing the program from your screenshot using the "Software" program and got the same problem when trying to remove it. And no, it is in fact not gnote, it's an older version of gnote from the time when it was still called bijiben (which is "notebook" in some variant of Chinese ...). So the command line way of uninstalling it is
```

sudo apt remove bijiben

```

As to why it's so complicated, it shouldn't be. It's probably a small error somewhere in the additional metadata for this specific package that the graphical installer needs (and the command line tools don't). If it was a general error in the "Software" App, we'd be up to our necks in error reports similar to yours.

Holger

---

### Post by abdul1337 on 2022-06-18
> **Holger_Gehrke said:**
> As you can probably tell from the fact that my first impulse was to use the command line, I'm not a fan of the "Software" application (and graphical system administration tools in general). I tried installing the program from your screenshot using the "Software" program and got the same problem when trying to remove it. And no, it is in fact not gnote, it's an older version of gnote from the time when it was still called bijiben (which is "notebook" in some variant of Chinese ...). So the command line way of uninstalling it is
```

sudo apt remove bijiben

```

As to why it's so complicated, it shouldn't be. It's probably a small error somewhere in the additional metadata for this specific package that the graphical installer needs (and the command line tools don't). If it was a general error in the "Software" App, we'd be up to our necks in error reports similar to yours.

Holger

Thank you so much, it seems to have removed it. I was trying to find the actual filename but notes was not recognised by sudo-apt; how did you find out the filename out of curiosity?

---

### Post by Holger_Gehrke on 2022-06-18
As I said, I use XUbuntu. In XUbuntu / XFCE you get a start menu similar to the one in Windows 7. You can simply right click on a menu item to get a context menu, which includes an option to edit the menu item. Through that I got the name of the executable file ('bijiben'). I then used 'which' to find the exact location of the executable and fed that into dpkg-query (part of the lower, local level of the package management; with the option '-S' and a full path and filename it tells you which package a file comes from) with 'dpkg-query -S $(which bijiben)'. That gave me the package name, which was - rather unsurprisingly - 'bijiben'.

Holger

---

### Post by mIk3_08 on 2022-06-19
> **abdul1337 said:**
> Thank you so much, it seems to have removed it. I was trying to find the actual filename but notes was not recognised by sudo-apt; how did you find out the filename out of curiosity?
To find out what notes you are looking for try to run command which shows all your installed application. Try to run the command below in your terminal.
```
apt list
```
Once successfully run the command in your terminal, press ctrl and shift + f then type the app you are looking for and press enter so it will find the word that you type in the search bar. Regards and cheers

---

### Post by abdul1337 on 2022-06-19
> **mIk3_08 said:**
> To find out what notes you are looking for try to run command which shows all your installed application. Try to run the command below in your terminal.
```
apt list
```
Once successfully run the command in your terminal, press ctrl and shift + f then type the app you are looking for and press enter so it will find the word that you type in the search bar. Regards and cheers

Thanks so much mate.

---

### Post by Holger_Gehrke on 2022-06-19
A small problem with 'apt list' is that it shows all packages, not only the installed ones and it only shows the package name without a description. Slightly better would be 'apt list --installed' (which shows all installed packages, manual and automatic - meaning packages which were installed because some other package needs them) or - even better - 'apt list --manual-installed' (which only shows the packages which were installed because you ordered them). Also 'apt list' produces so much output that it might overflow your terminal's buffer. On my system 'apt list|wc -l' (count the lines 'apt -list' produces) show 72678 - far more than the meager 4000 my xfce-terminal has. I don't know how large the buffer of gnome-terminal is, but I doubt it's that big.

The best alternative IMHO would be
```

apt search note|less

```
This searches all packages for the ones which have the word 'note' in it's package name or description and lists them in a format which includes the first line of the description and shows it's installation status. The '|less' at the end of that command sends the output of apt to the pager program 'less' which is independent of the terminal's buffer and allows movement through the file and searching using the '/' key (use 'q' to get out of less). Once one has found a candidate, one can drill down by using 'apt show package-name' (substituting the real package name for package-name) to see more detailed information on a package.

And a third way would be consulting apt's log-files in /var/log/apt/history.log. If you know when you installed a program (at least the date and the approximate time) then finding the package for a program is quite easy.

Holger

---

### Post by abdul1337 on 2022-06-19
> **Holger_Gehrke said:**
> A small problem with 'apt list' is that it shows all packages, not only the installed ones and it only shows the package name without a description. Slightly better would be 'apt list --installed' (which shows all installed packages, manual and automatic - meaning packages which were installed because some other package needs them) or - even better - 'apt list --manual-installed' (which only shows the packages which were installed because you ordered them). Also 'apt list' produces so much output that it might overflow your terminal's buffer. On my system 'apt list|wc -l' (count the lines 'apt -list' produces) show 72678 - far more than the meager 4000 my xfce-terminal has. I don't know how large the buffer of gnome-terminal is, but I doubt it's that big.

The best alternative IMHO would be
```

apt search note|less

```
This searches all packages for the ones which have the word 'note' in it's package name or description and lists them in a format which includes the first line of the description and shows it's installation status. The '|less' at the end of that command sends the output of apt to the pager program 'less' which is independent of the terminal's buffer and allows movement through the file and searching using the '/' key (use 'q' to get out of less). Once one has found a candidate, one can drill down by using 'apt show package-name' (substituting the real package name for package-name) to see more detailed information on a package.

And a third way would be consulting apt's log-files in /var/log/apt/history.log. If you know when you installed a program (at least the date and the approximate time) then finding the package for a program is quite easy.

Holger

Thank you. I am still learning that | operator XD

---

### Post by mIk3_08 on 2022-06-20
> **Holger_Gehrke said:**
> A small problem with 'apt list' is that it shows all packages, not only the installed ones and it only shows the package name without a description. Slightly better would be 'apt list --installed'  Yes you are right it is slightly same results. That is why I gave him the idea of searching/find the application of what he is looking for so it will be easy for him to find out.  That is the best way so far to look for the applications.
And another thing. For me, it is better to run the command
```
apt search note
```
than 
```
apt search note|less
```
because this command takes some delay by pressing enter while you can completely run the whole thing and scan it by yourself. That's for me. Regards and cheers.

---

