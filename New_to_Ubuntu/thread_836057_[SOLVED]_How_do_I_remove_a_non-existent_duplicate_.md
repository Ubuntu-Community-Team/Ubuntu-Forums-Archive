---
title: "[SOLVED] How do I remove a non-existent duplicate GDebi package installer session?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Felicity_X on 2008-06-21
I have just installed Ubuntu 8.04 on my desktop, and everything seems to be O.K.

I decided to install P2P accounting from a DVD.  I had copied the package from the internet to this DVD while my system was booted from a live cd of Ubuntu 5.04.  This may have been the reason my now installed Ubuntu 8.04 Gdebi package installer hung while installing.  There seemed to be nothing I could do to escape the loop or close down the window.  Nor would the system shut down with it open!  I closed down by disconnecting the power cable; Naughty! Naughty![-X

On rebooting, I removed the DVD and proceeded to install from the P2P website.  Now I get the error message "Only one software management tool is allowed to run at the same time".  I presume this means the system is still flagged as having the package installer running.  How do I correct this?

Also, will there be a partial installation of P2P files on my system which I will need to remove before attempting reinstall?  If so how do I find and remove them?  I cannot find anything in what, to me, are the obvious places.:confused:

---

### Post by MasterSander on 2008-06-21
Did you check your system monitor? You can try killing the process that's causing this.

---

### Post by Felicity_X on 2008-06-21
I did, both before and after receiving your message, MasterSander.  But, with all other applications not running, the only running process was the Gnome desktop itself.  There were lots of sleeping processes, but none that I could specifically identify as belonging to Gdebi.  I decided discretion was the better part of valour here, as I did not wish risk crudding the system any further.:confused:.

On booting, I did press <escape> at the right point to get to the grub level and was given the options of version 19, version 19 (recover), version 16, version 16 (recover).  I am presuming that version 16 is my original download, and version 19 is the updates I installed.  I am wondering if version 19 (recover) might restore me to my updated operating system without the problem?:-k.  I actually selected version 19 and it did bring me to everything as I had left it, problem included!

Can anyone put me right on this, please?

---

### Post by Felicity_X on 2008-06-21
I did, both before and after receiving your message, MasterSander.  But, with all other applications not running, the only running process was the Gnome desktop itself.  There were lots of sleeping processes, but none that I could specifically identify as belonging to Gdebi.  I decided discretion was the better part of valour here, as I did not wish risk crudding the system any further.:confused:.

On booting, I did press <escape> at the right point to get to the grub level and was given the options of version 19, version 19 (recover), version 16, version 16 (recover).  I am presuming that version 16 is my original download, and version 19 is the updates I installed.  I am wondering if version 19 (recover) might restore me to my updated operating system without the problem?:-k.  I actually selected version 19 and it did bring me to everything as I had left it, problem included!

Can anyone put me right on this, please?

---

### Post by drs305 on 2008-06-21
Have you tried uninstalling Gdebi (if you can get to uninstall)? It might remove a configuration file that is hanging up the system. Once/if it clears, you can reinstall it. 

If you can't open a gui:
```

sudo aptitude purge gdebi

```

Switching the kernel is not likely to solve this issue.

---

### Post by cariboo on 2008-06-21
If you are still having a problem with gdebi in a terminal run:

```
ps ax
```

Look for a line similar to this:

```
8960 ?        S      0:02 /usr/bin/python /usr/bin/gdebi-gtk /home/jimk/downloads

```

Of course  substitute /home/jimk/downloads for the directory your .deb is located in.

Jim

---

### Post by Felicity_X on 2008-06-21
Thanks very much, DRS305.  I cannot deinstall Gdebi, which I had already tried. I did try your second option, but got the message that the dpkg process was interrupted and I must run command: 'dpkg --configure -a' to sort it.  I have hit this problem before when trying to download software, and cannot work out how to log on as a root user, which is the only user level which can execute the command.

I have already put in a thread about this problem.

But in between notifying me of the glitch twice, your command did appear to be doing a number of operations which probably would have cleared the gdebi problem if the glitch would have let them!

---

### Post by drs305 on 2008-06-21
> **Felicity_X said:**
> Thanks very much, DRS305.  I did try what you said, but got the message that the dpkg process was interrupted and I must run command: 'dpkg --configure -a' to sort it.  I have hit this problem before when trying to download software, and cannot work out how to log on as a root user, which is the only user level which can execute the command.

I have already put in a thread about this problem.

But in between notifying me of the glitch twice, your command did appear to be doing a number of operations which probably would have cleared the gdebi problem if the glitch would have let them!


Simple, you just run the command as root:

```
sudo dpkg --configure -a
```

Try purging gdebi again and then update and upgrade if desired:
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by Felicity_X on 2008-06-21
I would like to try your option, Jim (Caribou907), but I am too much of a newbie to know how to set about it.

For example, I have not yet worked out how to get a directory tree and have no idea how to locate the different software packages, source or compiled, on the system.  Or how to compile and load source code as opposed to opening downloaded packages.

I would like to know all these things of course!

---

### Post by Felicity_X on 2008-06-21
But, DRS305, how do I get on as root?  The system will not let me log in as root at the places where everyone else logs in.

Should I have done the original system installation as root?  Is that the problem?  If so should I reinstall and set myself up as root instead of administrator?

---

### Post by drs305 on 2008-06-21
> **Felicity_X said:**
> But, DRS305, how do I get on as root?  The system will not let me log in as root at the places where everyone else logs in.

Should I have done the original system installation as root?  Is that the problem?  If so should I reinstall and set myself up as root instead of administrator?

If you can get to a terminal, and you are the only user or a member of admin, you can gain temporary 'root' or administrative powers by beginning the command with 'sudo'. Using the **sudo** command enables you to gain temporary permission to alter system files, which is what you are trying to do. 

When you type a 'sudo' command, it will ask for your password. As you type you won't see it being entered but it is registering. Just type and enter and the command should start to run.

This explains root & sudo better than I can:
[URL="https://help.ubuntu.com/community/RootSudo"]https://help.ubuntu.com/community/RootSudo
[/URL]

---

### Post by cariboo on 2008-06-21
If you look at drs305's post:

> sudo dpkg --configure -a

the **sudo** stands for **super user do**

So in other words you become the super user or root for that one command

Jim

---

### Post by Felicity_X on 2008-06-21
Thank you very much for all your help on this thread, DRS305.

I used the sudo commands as follows and got the following responses.

administrator@Our-Desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
administrator@Our-Desktop:~$ sudo dpkg --configure -a
[sudo] password for administrator:
Setting up java-common (0.28ubuntu3) ...

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
administrator@Our-Desktop:~$ sudo aptitude purge gdebi
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  ubuntu-desktop
The following packages have been kept back:
  sun-java6-bin
The following packages will be REMOVED:
  gdebi{p}
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 229kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gdebi but it is not installable
Resolving dependencies...
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop


:lolflag:  Seems pretty clear to me.

I pulled the plug on the system a day or two ago when the gdebi package hung while installing the dependencies for a P2P Accounting download.  As I have been advised by two people, that can seriously damage the system and that seems to be what has happened.

I will try de-installing Ubuntu desktop as instructed but, if it will not reinstall, then I will have to reinstall from the disk. :oops:

---

### Post by drs305 on 2008-06-21
> **Felicity_X said:**
> 
Remove the following packages:
ubuntu-desktop
:lolflag:  Seems pretty clear to me.
I will try de-installing Ubuntu desktop as instructed but, if it will not reinstall, then I will have to reinstall from the disk. :oops:

I know it sounds scary. I run the standard 64-bit hardy on this machine and don't even have ubuntu-desktop installed - but it scared the heck out of me the first time I saw it was going to be removed as part of some upgrade I was doing ;-)

---

### Post by Felicity_X on 2008-06-21
I re-ran the purge and then allowed it to de-install ubuntu-desktop.  I still got the following error message:

E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)

Can this be done, or do I need to reinstall the whole system?  If it can be done, how?

No need.  All sorted. I went back to add/remove and tried to install Equonomize.  It found the erroneous file and rebuilt it all on its ownio!!
\\:D/\\:D/\\:D/.

I think this is all sorted.  If any remaining problems, I will open a new thread.  Thanks again to all who helped me on this:popcorn:

---

### Post by drs305 on 2008-06-21
> **Felicity_X said:**
> I re-ran the purge and then allowed it to de-install ubuntu-desktop.  I still got the following error message:

E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)

Can this be done, or do I need to reinstall the whole system?  If it can be done, how?

You shouldn't need to reinstall the entire package. 
Can you get into synaptic? If so, first try going to the left side and select status and see if there is a listing for broken packages. If there is, allow synaptic to try to fix it. If that doesn't work, try to reinstall sun-java6-bin. If that still doesn't work, you can try removing it with the "sudo aptitude purge sun-java6-bin" command.

Hopefully you will soon get this resolved. I'll be off the computer but others should help you out.

---

