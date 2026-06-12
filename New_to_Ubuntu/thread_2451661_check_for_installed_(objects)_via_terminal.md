---
title: "check for installed (objects?) via terminal"
date: 2020-10-08
forum: New to Ubuntu
---

### Post by f3mto5econd1nter4ction on 2020-10-08
On ubuntu is there a way (from terminal) to print out a list of objects that can be removed using the [FONT=arial]sudo apt-get remove 'AppNameHere' command?[/FONT] [FONT=arial]Some of the software pop up on my show applications tab while others don't.[/FONT]
Is the name for these objects applications? Since they don't appear under the tab that bears the name.

Cheers

---

### Post by yetimon_64 on 2020-10-08
> **f3mto5econd1nter4ction said:**
> On ubuntu is there a way (from terminal) to print out a list of objects that can be removed using the [FONT=arial]sudo apt-get remove 'AppNameHere' command?[/FONT] [FONT=arial]Some of the software pop up on my show applications tab while others don't.[/FONT]
Is the name for these objects applications? Since they don't appear under the tab that bears the name.

Cheers

Anything installed can be removed using apt or apt-get, though doing so may remove wanted applications as well due to dependency issues. I don't really comprehend exactly what you are asking for here.

A possible help tip for you when using "apt" or "apt-get" with the remove option is to test first with a simulation only. To do this use the "-s" (simulation only) switch.
For example if you want to remove "firefox" and check if anything else will be affected ...
```
apt-get remove **-s** firefox
```
The "-s" (in bold text for clarity/visibility) causes the command to run as a simulation only, NOTHING will be removed but you will see what will happen before you run the command for real (without the "-s" switch).

Just an extra note: the simulation switch (-s) can be used to test **any** action undertaken with apt or apt-get. I regularly use it with the autoremove option which in the past has caused some dependency headaches here; also with the install option to see what extra packages are being added when installing an application before I actually install anything.  

Hope that is of some help for you. Regards, yeti.

---

### Post by &amp;KyT$0P# on 2020-10-08
> **f3mto5econd1nter4ction said:**
> On ubuntu is there a way (from terminal) to print out a list of objects that can be removed using the [FONT=arial]sudo apt-get remove 'AppNameHere' command?[/FONT] 

Yes.  How do you intend to use this list?

> Is the name for these objects applications? 

Not all of them are applications.  I call them "deb packages".  Not all deb packages install an application.

@yetimon_64, the simulation doesn't need sudo.

---

### Post by Impavidus on 2020-10-09
It's called a package. All (almost) software on Ubuntu comes in packages. There are a few styles of packages, but the main one is a deb package and apt only deals with those. A package contains software (applications, shared libraries, collections of icons or fonts, core components or the operating system, ...), along with instructions to install and remove them. Most applications are in a package with the same name as the application (or similar). Packages may depend on other packages, such that some packages can only be installed when certain other packages are installed too.

apt assumes you're smart. If you tell it to remove some core component of the OS, it may give you a warning, but if you tell it to proceed it will assume you're brilliant and will just do what you tell it to do. So you can remove whatever package you want, but this may result in removal of other packages or your entire OS.

To get a list of all installed packages you can use dpkg, which is a lower-level tool used by apt to do some of its work:```
dpkg --list
```

What you see in "show applications" are the applications that can be launched from the GUI. They must have a .desktop file that tells with what command the application can be launched and some other useful stuff, like how it can be instructed to open a particular file and what icon should be associated with it.

---

### Post by yetimon_64 on 2020-10-09
> **halogen2 said:**
> ...
@yetimon_64, the simulation doesn't need sudo.
You're right there, thanks; I put it in without thinking earlier as a habit with using apt/apt-get. The code box command is now changed.

---

