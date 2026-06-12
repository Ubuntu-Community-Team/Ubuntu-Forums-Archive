---
title: "Couple of questions. One regarding BASH and one regarding the Budgie software"
date: 2020-04-16
forum: New to Ubuntu
---

### Post by xcfstarflight1 on 2020-04-16
Hi!
About Ubuntu budgie. What are the different software sections? Just if someone can tell me a bit about what the different archives are for:

[LIST=1]
[*]Budgie applets
[*]Software center
[*]Snap apps
[*]Flatpak apps
[/LIST]
I don't even know what Flatpak is. So please someone can explain a bit.

Second question regarding BASH.
I need to add a program stored in &#771;~/programname/program.sh (It's a sh script).
Where and how do I add the folder to a PATH variable correctly and what file should I store it in? 
I just use the Tillix terminal without any other format. 

Best regards, Sigurd Skauvik

---

### Post by Tadaen_Sylvermane on 2020-04-16
Normally packages are distro specific. Ubuntu packages are not usually binary compatible with Debian and so forth. Snaps and Flatpak are universal packages. In the case of snap you need to have the snapd daemon installed. This can be installed on most major distros. That daemon allows any distro to run the same package, eliminating distro specific things. Flatpak is the same idea, different implementation. Software center is nothing more than an App store. The applets are just widgets for the desktop or bars I would think. Most Desktop Environments have some sort of those running or available.

As far as Bash is concerned you should put your executable scripts in ~/bin. The normal login shell should add that to your $PATH if it exists for local users. If you have any custom scripts you would like all users to have access to then I'm pretty sure /usr/local/bin is the place for those.

---

### Post by Frogs Hair on 2020-04-16
1.[ Budgie extras]("https://github.com/UbuntuBudgie/budgie-extras") is a repository of panel applets for the Budgie desktop.
2. Gnome software provides software from the Ubuntu Sources  listed in software sources including the Canonical Partners repository if enabled and snap. 
3. [Snap ]("https://wiki.archlinux.org/index.php/Snap")
4. Snap [Store ]("https://snapcraft.io/store")
5.[Flatpak ]("https://flatpak.org/")

---

### Post by yetimon_64 on 2020-04-16
> **Tadaen_Sylvermane said:**
> ...As far as Bash is concerned you should put your executable scripts in ~/bin. The normal login shell should add that to your $PATH if it exists for local users...

~/bin is the easiest to use for user scripts as it is, as noted above, already in the path. If the user has to create it then a logout and log back in to the users desktop will be needed to have the path set up fully.

However to add a custom directory, as asked by the OP, outside of ~/bin a simple export command placed in the ~/.profile file will do the job.

An example from this install of mine is for screen layout scripts; I hold several custom scripts I store in ~/.screenlayout for altering my screen setup with simple mouse gestures. To have ~/.screenlayout in my user path I added the line in the next code box to my ~/.profile file...
```
export PATH=$PATH:$HOME/.screenlayout
```

For the OPs situation the export command in ~/.profile would look like...
```
export PATH=$PATH:$HOME/programname
```
After logging out of the desktop and logging back in the path can be checked with...
```
echo $PATH
```

Regards, yeti

---

### Post by xcfstarflight1 on 2020-04-16
Thank you! I will add a couple of scripts I made to this folder.

---

### Post by Tadaen_Sylvermane on 2020-04-16
> [COLOR=#000000]If the user has to create it then a logout and log back in to the users desktop will be needed to have the path set up fully[/COLOR][COLOR=#000000]

Indeed. I missed that as well as adding the desired directory to $PATH. [/COLOR]

---

