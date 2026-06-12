---
title: "Large Black Cursor"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by cmcanulty on 2013-10-06
I have asked this before and tried numerous fixes but nothing works. I need  the DMZ-Black Cursor in 48 point. I can get it to work in firefox but nothing else. I have even tried it in LXDE, xfce4, classic, and unity. I run 10 computers in Ubuntu 12.04 classic at our library and this seems so dumb. Some it works in one user and not the other, some not at all. I am aware there is a setting in dconf but that does nothing, neither does gnome-tweak, or ubuntu-tweak.They don't even change the color to black except in firefox which has the 48pt black as I want. It used to work until the last 2 or 3 ubuntu upgrades. I need clear easy to follow directions as nothing works! Like the idea of installing large black cursor does nothing I need specifics, hopefully that will work in all Desktop environments but at least in classic and hopefully xfce4. Thanks, this seems to be a common problem and quite a dumb but irritating bug, thank you

---

### Post by fantab on 2013-10-07
Its a bug. Have you tried [this workaround]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647/comments/110")?
[This Video]("https://www.youtube.com/watch?v=a5_WGPPMKrg") shoud point you in the right direction...

---

### Post by cmcanulty on 2013-10-07
it is a bug that has been going on for at least 2 years and certainly needs fixing. A mouse setting should be easy.The link doesn't tell the steps needed to do it. Like step 1  where is the DMZ-Black folder and how do you set it to 48pt. I also have done the alternatives fix and it doesn't work either


```
1)
create a file in the folder of the Icon theme you want to use and name it
cursor.theme and put the following it it.
[Icon Theme]
Inherits=NameOfTheme"[/CODE


I tried it as I thought it should be done and get this big mess and it is still white and small


[CODE]cmcanulty@darcytech:~$ sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/DMZ-Black-Large
[sudo] password for cmcanulty: 
update-alternatives: --install needs <link> <name> <path> <priority>

Usage: update-alternatives [<option> ...] <command>

Commands:
  --install <link> <name> <path> <priority>
    [--slave <link> <name> <path>] ...
                           add a group of alternatives to the system.
  --remove <name> <path>   remove <path> from the <name> group alternative.
  --remove-all <name>      remove <name> group from the alternatives system.
  --auto <name>            switch the master link <name> to automatic mode.
  --display <name>         display information about the <name> group.
  --query <name>           machine parseable version of --display <name>.
  --list <name>            display all targets of the <name> group.
  --get-selections         list master alternative names and their status.
  --set-selections         read alternative status from standard input.
  --config <name>          show alternatives for the <name> group and ask the
                           user to select which one to use.
  --set <name> <path>      set <path> as alternative for <name>.
  --all                    call --config on all alternatives.

<link> is the symlink pointing to /etc/alternatives/<name>.
  (e.g. /usr/bin/pager)
<name> is the master name for this link group.
  (e.g. pager)
<path> is the location of one of the alternative target files.
  (e.g. /usr/bin/less)
<priority> is an integer; options with higher numbers have higher priority in
  automatic mode.

Options:
  --altdir <directory>     change the alternatives directory.
  --admindir <directory>   change the administrative directory.
  --log <file>             change the log file.
  --force                  allow replacing files with alternative links.
  --skip-auto              skip prompt for alternatives correctly configured
                           in automatic mode (relevant for --config only)
  --verbose                verbose operation, more output.
  --quiet                  quiet operation, minimal output.
  --help                   show this help message.
  --version                show the version.
cmcanulty@darcytech:~$ 

```


Here is the file I created as it said to do in/user/share/icons/DMZ-Black-Large
```

[Icon Theme]
Inherits=DMZ-Black-Large
```

And here is the step 3 which still shows white even after I type 6


```

cmcanulty@darcytech:~$ sudo update-alternatives --config x-cursor-theme
[sudo] password for cmcanulty: 
There are 8 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).

  Selection    Path                                     Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/DMZ-White/cursor.theme   90        auto mode
  1            /etc/X11/cursors/core.theme               30        manual mode
  2            /etc/X11/cursors/handhelds.theme          20        manual mode
  3            /etc/X11/cursors/oxy-white.theme          50        manual mode
  4            /etc/X11/cursors/redglass.theme           20        manual mode
  5            /etc/X11/cursors/whiteglass.theme         20        manual mode
  6            /usr/share/icons/DMZ-Black/cursor.theme   30        manual mode
* 7            /usr/share/icons/DMZ-White/cursor.theme   90        manual mode
  8            /usr/share/icons/cursor.theme             20        manual mode

Press enter to keep the current choice[*], or type selection number: 6
update-alternatives: using /usr/share/icons/DMZ-Black/cursor.theme to provide /usr/share/icons/default/index.theme (x-cursor-theme) in manual mode.
cmcanulty@darcytech:~$ 
```

---

### Post by cmcanulty on 2013-10-07
OMG I finally got it. The mistake I was doing was picking in galternatives the folder DMZ-Black-Large and not one level further to cursor.theme. Now before I marked this solved I need to know if I have to do this for all users or is it system wide. What a hassle to fix a small issue. A beginner could or would never be able to do this! Thanks

---

### Post by fantab on 2013-10-07
I have a simpler method to change cursor size globally... just got it.
Create a hidden file in your Home Folder and name it .Xresources (*$ gedit ~/.Xresources*) and put "**Xcursor.size: 48**" (without quotes) in the file and save it. Change the cursor size in dconf-editor and reboot.
EDIT: there is space after the colon. By the way, I am working on SAUCY and do have cursor.theme in my /usr/share/icons/DMZ-white.

Since I am the only user on my computer I cannot confirm if its per user or system wide.. do let us know.

---

### Post by stinkeye on 2013-10-07
> **cmcanulty said:**
> OMG I finally got it. The mistake I was doing was picking in galternatives the folder DMZ-Black-Large and not one level further to cursor.theme. Now before I marked this solved I need to know if I have to do this for all users or is it system wide. What a hassle to fix a small issue. A beginner could or would never be able to do this! Thanks

You sure about that???
Because that's the same as what I showed you in your previous thread except you don't have to make a
**cursor.theme** file because it's already there in the theme.
[http://ubuntuforums.org/showthread.php?t=2048046&p=12572902#post12572902](http://ubuntuforums.org/showthread.php?t=2048046&p=12572902#post12572902)
Goodluck. :p

---

### Post by cmcanulty on 2013-10-07
OK hard fix worked for both users on machine 1 . On machine 2 changed to black but still very small except in firefox and it is set correctly everywhere I think. But the choice of large doesn't show up in Ubuntu  Tweak or adv settings, it does show in galternatives and is selected. What is wrong?  .I logged out and in,  rebooted also.This is crazy hard and I need it to work at library as we have tons of seniors with poor eyesight. This being so hard for a simple setting is going to lose users.This seems almost random whether it works or not on each machine all running 12.04 classic.

---

### Post by Dennis N on 2013-10-07
There is a graphical front end to the **update-alternatives** command. It is called "Alternatives Configurator" and has the package name **galternatives**. It might make the work go easier.

If you are open to alternatives, I also install a larger cursor, and chose one that is natively large. It has a black version (as well as other colors). No problems getting it to work correctly in Ubuntu, Lubuntu, or Xubuntu of any release (including the current one). But, I have not tried it in Gnome Classic myself. See:

[http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027](http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027)

---

### Post by cmcanulty on 2013-10-07
I guess what I don't understand is why it only works on certain computers and certain users (machines are identical)

---

### Post by cmcanulty on 2013-10-07
I guess what I don't understand is why it only works on certain computers and certain users (machines are identical)

---

