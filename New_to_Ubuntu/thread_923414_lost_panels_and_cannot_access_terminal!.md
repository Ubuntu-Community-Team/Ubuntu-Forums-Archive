---
title: "lost panels and cannot access terminal!"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by mhedges48 on 2008-09-18
I am running hardy; I lost all panels and AWN. Alt-f2 does not open up a terminal. I am in Firefox b/c the web browser shortcut on my keyboard works.

What happened was, I was having a bug in Hardy evolution. Launchpad recommended upgrading to intrepid version where it was fixed. However, I realized too late that when I did that, for some reason it uninstalled gnome panel, awn, and nautilus...

How can I reinstall these?

thanks!

---

### Post by hellion0 on 2008-09-18
Use Ctrl+Alt+F1 and see if that brings you to a prompt on an otherwise blank screen. This works just like the Terminal; log in with your username and password.

Reinstall the lost packages with apt-get or aptitude.

Use Ctrl+Alt+F7 to return to the GUI and log out, then back into Gnome.

---

### Post by mhedges48 on 2008-09-18
thank you. This worked; however, I am unable to install anything. For example, trying to install nautilus I get that it depeds on nautilus-data (<1:2.23) but 1:2.23.92-0ubuntu1 is to be installed
and likewise for gnome-panel, get that it depends on gnome-control-center when in turn depends on capplets-data (1:2.23) but 1:2.23.90-ubuntu1 is to be installed...

I have already tried dpkg to check for broken packages as well as apt-get update.

---

### Post by Keen101 on 2008-09-18
try doing a "sudo apt-get upgrade" I don't know if that will help, but it's something to try while waiting for the other guy to reply.

---

### Post by mhedges48 on 2008-09-18
sudo-apt upgrade didn't do anything... thanks though

---

### Post by prshah on 2008-09-18
> **mhedges48 said:**
> for some reason it uninstalled gnome panel, awn, and nautilus...
How can I reinstall these?


First, as suggested, use an apt-get update to ensure your repositories are in shape. If you get no errors, use apt-get upgrade. If you still have errors, (Using a sledgehammer to squash an ant):```
sudo apt-get --reinstall install ubuntu-desktop
```

---

### Post by hellion0 on 2008-09-18
> **Keen101 said:**
> I don't know if that will help, but it's something to try while waiting for the other *guy* to reply.Excuse me? I'm a girl. :razz:

Aaaaanyway... I'll second prshah's suggestion involving ants and sledgehammers. Or reinstalling ubuntu-desktop.

---

### Post by mhedges48 on 2008-09-18
Thank you. I tried that, however, the ubuntu-desktop has dependencies, including gnome-panel and nautilus (which has the problem stated above), as well as alacarte...

---

### Post by hellion0 on 2008-09-18
I think the ant needs a nuclear bomb. You might try at least restoring your system to some usability by installing another desktop environment, as a workaround.

You might have to get rid of your Evolution fix afterward.

---

### Post by mhedges48 on 2008-09-18
Before I nuke myself, do you think there is some way to force the version? We are very close to getting this to work; I can browse file systems using firefox for example, I think we just have to figure out how to force the right version to reinstall gnome panels and nautilus

Problem seems to be that it needs 1:2.23 but wants to install 1:2.23.90-ubuntu1...

thank you all for your time

---

### Post by hellion0 on 2008-09-18
To be fair, I only mentioned a nuke as something to further the sledgehammer : ant metaphor.

When you applied that fix for Evolution, did you change your repositories via Synaptic or via manually editing /etc/apt/sources.list? (Which way it happened is not as important as *did* it happen.)

If so, you might need to revert those sources back to the defaults.

---

### Post by mhedges48 on 2008-09-18
Good idea on the sources list; I replace sources.list with the sources.list.default but didn't fix it though.

However, I have gotten the panels working! I did this by removing the capplets-data and then reinstalling it, that then let me install gnome-panel... now on to trying to fix the nautilus...

thanks

---

### Post by mhedges48 on 2008-09-18
and this is why nautilus won't work


The following packages have unmet dependencies:
  nautilus: Depends: libeel2-2 (>= 2.21.90) but it is not going to be installed
            Depends: libgail-common (>= 1.10.1) but it is not going to be installed
            Depends: libgail18 (>= 1.10.1) but it is not going to be installed

---

### Post by prshah on 2008-09-18
> **mhedges48 said:**
> Thank you. I tried that, however, the ubuntu-desktop has dependencies, including gnome-panel and nautilus (which has the problem stated above), as well as alacarte...

In for a penny, in for a pound:```
sudo apt-get --reinstall --fix-missing install ubuntu-desktop
```

OR: If the above gives an error:```
sudo apt-get --reinstall --ignore-missing install ubuntu-desktop
```

Remember: package files that already exist on your system will not be (re)downloaded, which is good.

And, as for
> **mhedges48 said:**
> 
The following packages have unmet dependencies:
  nautilus: Depends: libeel2-2 (>= 2.21.90) but it is not going to be installed
            Depends: libgail-common (>= 1.10.1) but it is not going to be installed
            Depends: libgail18 (>= 1.10.1) but it is not going to be installed

Can you try```
sudo apt-get -s install nautilus libeel2-2 libgail-common libgail18
``` If that spits out no errors, repeat the command, but without the "-s" (simulation) switch.

---

### Post by mhedges48 on 2008-09-19
Thank you very much. I get the error I am pasting below after running the command you recommended. I think the problem is, when I tried to update evolution to intrepid, it upgrade these other things to intrepid as well. I fixed the gnome-panel problem by just removing the intrepid dependencies and installing the hardy. However, I can't do the same for the libgail18 for example b/c when I try, it says it will remove other files at the same time....

¨¨¨

root@hedges:/home/matt# sudo apt-get -s install nautilus libeel2-2 libgail-common libgail18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libeel2-2: Depends: libbonoboui2-0 (>= 2.15.1) but it is not going to be installed
             Depends: libglade2-0 (>= 1:2.6.1) but it is not going to be installed
             Depends: libgnome-desktop-2 (>= 1:2.22) but it is not going to be installed
             Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not going to be installed
             Depends: libgnomeui-0 (>= 2.17.1) but it is not going to be installed
             Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
  libgail-common: Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
  libgail18: Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
  nautilus: Depends: gnome-control-center (>= 2.6) but it is not going to be installed
            Depends: libglade2-0 (>= 1:2.6.1) but it is not going to be installed
            Depends: libgnome-desktop-2 (>= 1:2.22) but it is not going to be installed
            Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not going to be installed
            Depends: libgnomeui-0 (>= 2.17.1) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not going to be installed
            Depends: libnautilus-extension1 (>= 1:2.22.2) but it is not going to be installed
            Depends: librsvg2-2 (>= 2.18.1) but it is not going to be installed
E: Broken packages

---

### Post by hellion0 on 2008-09-19
Just a hunch... do a:
```
cat /etc/issue | grep Ubuntu
```
and paste the results back here.

---

### Post by mhedges48 on 2008-09-19
matt@hedges:~$ cat /etc/issue | grep Ubuntu
Ubuntu 8.04.1 \n \l

---

### Post by hellion0 on 2008-09-19
Ok, so it's the proper version... don't know why the packages for it won't work.

The last resort I can think of is to grab the packages manually from [here](http://packages.ubuntu.com/hardy/) and then 'dpkg -i' the lot of the ones that are missing.

---

### Post by fahorne on 2008-09-19
> **prshah said:**
> In for a penny, in for a pound:```
sudo apt-get --reinstall --fix-missing install ubuntu-desktop
```

OR: If the above gives an error:```
sudo apt-get --reinstall --ignore-missing install ubuntu-desktop
```

Remember: package files that already exist on your system will not be (re)downloaded, which is good.

And, as for


Can you try```
sudo apt-get -s install nautilus libeel2-2 libgail-common libgail18
``` If that spits out no errors, repeat the command, but without the "-s" (simulation) switch.Brought MY panels back. Thanks prshah

---

### Post by mhedges48 on 2008-09-19
Tried doing the packages via the downloads as suggested but got the same errors... for programs not installed like nautilus went back to the dependences, and it wouldn't install dependencies b/c quoted wrong version again...

---

### Post by gjoellee on 2008-09-19
This happened with a update in Intrepid Ibex a week ago....Gnome Do saved the day...I managed to updet the terminal and start ```
gnome-panel
``` and added it to startup and everything is fine:)

Boot up in recoverymode and to to the root command prompt in the text-based menu that appears and use the command ```
sudo apt-get install gnome-panel
```

---

### Post by gjoellee on 2008-09-19
This happened with a update in Intrepid Ibex a week ago....Gnome Do saved the day...I managed to update the terminal and start ```
gnome-panel
``` and added it to startup and everything is fine:)

Boot up in recovery mode and to to the root command prompt in the text-based menu that appears and use the command ```
sudo apt-get install gnome-panel
```
or the code for reinstalling :)

---

### Post by mhedges48 on 2008-09-21
To get nautilus back I had to bite the bullet and do a fresh Hardy install...

---

### Post by s|fr on 2009-01-04
Just incase someone is still looking for a solution. I have encountered this problem a couple of times now. The way I fix this is by (re)installing nautilus using aptitude.

simply type at the terminal: ```
sudo aptitude install nautilus
```

Aptitude will automatically detect the problem and provide a solution for it. For me, everytime, the issue has been that the libgtk module is upgraded and is no longer compatible with libgail18 module (which consequently conflicts with libeel et al.).
Aptitude will downgrade the relevant modules and resinstall nautilus for you. Hope that helps.

---

