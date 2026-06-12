---
title: "[SOLVED] Help uninstalling Origami (folding at home)"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-02
I need to uninstall Origami. It was called Folding at Home at one time. It has been on my 'puter for several years. But two to three weeks ago, a file named: FahCore_a0.exe started running at start-up. 

That .exe absorbed about 80 to 90 percent of the CPU, all the time.

Christer Edwards, the guy who wrote the program has a documentation Ubuntu wiki page and give instructions on how to uninstall it using the "erase" command. The erase command isn't installed on this computer and I have no idea whether it's a bash feature, or just what.

I just want to safely remove the entire program and edit any init files to get rid of this nuisance.

---

### Post by KIAaze on 2008-10-02
Do you mean this tutorial?:
[https://help.ubuntu.com/community/FoldingAtHome/origami#Removal](https://help.ubuntu.com/community/FoldingAtHome/origami#Removal)

```
sudo ./origami erase
```
Looks like "erase" is just a parameter for the origami script/program.
It's not a program you have to install.

Does the "sudo ./origami erase" command not work for you?

---

### Post by Mark_in_Hollywood on 2008-10-02
Yes, that is the page that the problematic (for me) erase feature shows up on.

mark@Lexington-19:~$ sudo ./origami erase
[sudo] password for mark: 
sudo: ./origami: command not found

Why would the OS try to run an .exe file?

---

### Post by KIAaze on 2008-10-02
The wiki lists three methods to install it:
-tar package
-bzr branch lp:origami
-deb [http://ppa.launchpad.net/christer.edwards/ubuntu](http://ppa.launchpad.net/christer.edwards/ubuntu) hardy main

Which one did you use?

If you used the debian package, this should remove it:
```
sudo apt-get remove origami
```

Otherwise, make sure to go to the directory from which you installed it before running the "sudo ./origami erase" command.
Use the "cd" command to navigate directories.
The uninstall command should be run from within the origami-* folder.

> Why would the OS try to run an .exe file?
I don't know, but ".exe" is just an extension. It could be a GNU/Linux native binary, a script, or a windows binary run through wine.
Would have to look into how origami works to know what exactly it is.

---

### Post by louieb on 2008-10-02
You need to be in the directory origami was installed into.

Opps- KIAaze got here ahead of me and with a better post.

---

### Post by kamitsukai on 2008-10-02
Hi, don't mean to hijack your thread...well actually I am:D but I've just installed folding at home via the origami script and was wondering will it automatically start when I login to ubuntu or do I have to set that up? and how? (through sessions?)

Thanks in advance!

PS: Is there a GUI in the works at all?

---

### Post by Mark_in_Hollywood on 2008-10-02
> **KIAaze said:**
> The wiki lists three methods to install it:
-tar package
-bzr branch lp:origami
-deb [http://ppa.launchpad.net/christer.edwards/ubuntu](http://ppa.launchpad.net/christer.edwards/ubuntu) hardy main

Which one did you use?

If you used the debian package, this should remove it:
```
sudo apt-get remove origami
```

Otherwise, make sure to go to the directory from which you installed it before running the "sudo ./origami erase" command.
Use the "cd" command to navigate directories.
The uninstall command should be run from within the origami-* folder.

I don't know, but ".exe" is just an extension. It could be a GNU/Linux native binary, a script, or a windows binary run through wine.
Would have to look into how origami works to know what exactly it is.


Why would the installation method matter? Well, for now that's rhetorical. I don't remember, it's that long ago. 

As for apt-get remove, I use aptitude and the results are:

mark@Lexington-19:/$ sudo apt-get remove origami
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package origami is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The origami folder is in /var/lib

---

### Post by KIAaze on 2008-10-02
> **Mark_in_Hollywood said:**
> Why would the installation method matter?

Because it's quite probable that the debian package and the installation script from the tar.gz install things differently.

Furthermore, a debian package is a lot easier and straightforward to remove.
You uninstall it like any other package.

However, it seems that you haven't installed origami using the debian package.
Have you already deleted the folder you installed it from?

If that's the case, you may try redownloading it and running the erase command.
Latest release is origami-0.6.8.1.tar.gz
Get it here: [http://zelut.org/projects/origami/?C=M;O=A](http://zelut.org/projects/origami/?C=M;O=A)

```
tar -xzvf origami-0.6.8.1.tar.gz
cd origami-0.6.8.1/
./origami erase

```

@kamitsukai:
Sorry, I have no idea at all since I haven't used origami yet.
Try contacting the developers directly. ;)

---

### Post by forger on 2008-10-02
Why wouldn't the installation method matter? :)

**[COLOR="Red"]WARNING! Use at your own risk![/COLOR]**
```

sudo killall -9 origami
sudo killall -9 -rI fah
sudo apt-get purge origami
sudo rm -rv /var/lib/origami
sudo crontab -u origami -r
sudo deluser origami
sudo delgroup origami
sudo rm -v /etc/init.d/origami
sudo rm -v /usr/bin/origami
sudo rm -v /usr/share/doc/origami
sudo rm -v /usr/share/man/man1/origami.1.gz
sudo find / -depth -iname "*origami*"
sudo find / -depth -iname "fah*"

```

---

### Post by forger on 2008-10-02
> **kamitsukai said:**
> PS: Is there a GUI in the works at all?

It's not folding@home, but boinc-client has a gui, boinc-manager and they support more projects.
[apt://boinc-manager]("apt://boinc-manager")

---

### Post by kamitsukai on 2008-10-03
Thanks forger!

---

### Post by Mark_in_Hollywood on 2008-10-06
Forger's post with the list of command lines to do the removal worked perfectly. They did the trick. My CPU %s are down to normal levels.

thanks, community.

---

### Post by altonbr on 2009-08-10
If you're running Jaunty, you can install origami via the repositories...

So if you had it installed and uninstalled it but it is still running, you need to do this:

```
sudo aptitude install origami
sudo origami erase
sudo aptitude purge origami
```[B]

Let's see what files are currently named 'origami'
[/B]> brett@van-gogh:~$ locate origami
/etc/rc.local.origami
/etc/init.d/origami
/etc/rc0.d/K20origami
/etc/rc1.d/K20origami
/etc/rc2.d/S20origami
/etc/rc3.d/S20origami
/etc/rc4.d/S20origami
/etc/rc5.d/S20origami
/etc/rc6.d/K20origami
/usr/bin/origami
/usr/share/doc/origami
/usr/share/man/man1/origami.1.gz
/var/lib/origami
/var/lib/dpkg/info/origami.list
/var/lib/dpkg/info/origami.md5sums
/var/lib/origami/client.cfg
/var/lib/origami/fahback
/var/lib/origami/finstall
/var/lib/origami/foldingathome
/var/lib/origami/foldingathome/CPU1
/var/lib/origami/foldingathome/CPU2
/var/lib/origami/foldingathome/FAH6.02-Linux.tgz
/var/lib/origami/foldingathome/FAHLinux.txt
/var/lib/origami/foldingathome/fah6
/var/lib/origami/foldingathome/fah_config
/var/lib/origami/foldingathome/finstallFAQ.txt
/var/lib/origami/foldingathome/get_qdinfo
/var/lib/origami/foldingathome/installService
/var/lib/origami/foldingathome/mpiexec
/var/lib/origami/foldingathome/origami
/var/lib/origami/foldingathome/uninstallService
/var/lib/origami/foldingathome/CPU1/FAH504-Console.exe
/var/lib/origami/foldingathome/CPU1/FAHlog-Prev.txt
/var/lib/origami/foldingathome/CPU1/FAHlog.txt
/var/lib/origami/foldingathome/CPU1/FaH
/var/lib/origami/foldingathome/CPU1/FahCore_78.exe
/var/lib/origami/foldingathome/CPU1/MyFolding.html
/var/lib/origami/foldingathome/CPU1/client.cfg
/var/lib/origami/foldingathome/CPU1/client.cfg.origami
/var/lib/origami/foldingathome/CPU1/fah6
/var/lib/origami/foldingathome/CPU1/machinedependent.dat
/var/lib/origami/foldingathome/CPU1/queue.dat
/var/lib/origami/foldingathome/CPU1/unitinfo.txt
/var/lib/origami/foldingathome/CPU1/work
/var/lib/origami/foldingathome/CPU2/FAH504-Console.exe
/var/lib/origami/foldingathome/CPU2/FAHlog-Prev.txt
/var/lib/origami/foldingathome/CPU2/FAHlog.txt
/var/lib/origami/foldingathome/CPU2/FaH
/var/lib/origami/foldingathome/CPU2/FahCore_78.exe
/var/lib/origami/foldingathome/CPU2/MyFolding.html
/var/lib/origami/foldingathome/CPU2/client.cfg
/var/lib/origami/foldingathome/CPU2/client.cfg.origami
/var/lib/origami/foldingathome/CPU2/fah6
/var/lib/origami/foldingathome/CPU2/machinedependent.dat
/var/lib/origami/foldingathome/CPU2/queue.dat
/var/lib/origami/foldingathome/CPU2/unitinfo.txt
/var/lib/origami/foldingathome/CPU2/work[B] 

Origami is uninstalled, so origami's 'erase' command will not work[/B]
> brett@van-gogh:~$ sudo origami erase
sudo: origami: command not found
[B]
Install origami so we can later erase it...[/B]
> 
brett@van-gogh:~$ sudo aptitude install origami
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  origami 
0 packages upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 21.0kB of archives. After unpacking 90.1kB will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe origami 0.6.9-0ubuntu1 [21.0kB]
Fetched 21.0kB in 0s (30.6kB/s)
Selecting previously deselected package origami.
(Reading database ... 275904 files and directories currently installed.)
Unpacking origami (from .../origami_0.6.9-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up origami (0.6.9-0ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
**Tell origami to erase itself**
> 
brett@van-gogh:~$ sudo origami erase
UNINSTALLING... PLEASE BE PATIENT.
Please report feedback at [https://bugs.launchpad.net/origami](https://bugs.launchpad.net/origami)
**Now we can uninstall/purge origami**
> 
brett@van-gogh:~$ sudo aptitude purge origami
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REMOVED:
  origami{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 90.1kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 275910 files and directories currently installed.)
Removing origami ...
Processing triggers for man-db ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
**And just for fun, let's see what's leftover on my computer**
> 
brett@van-gogh:~$ locate origami
/etc/rc.local.origami
/etc/init.d/origami
/etc/rc0.d/K20origami
/etc/rc1.d/K20origami
/etc/rc2.d/S20origami
/etc/rc3.d/S20origami
/etc/rc4.d/S20origami
/etc/rc5.d/S20origami
/etc/rc6.d/K20origami
/usr/bin/origami
/usr/share/doc/origami
/usr/share/man/man1/origami.1.gz
/var/lib/origami
/var/lib/dpkg/info/origami.list
/var/lib/dpkg/info/origami.md5sums

---

