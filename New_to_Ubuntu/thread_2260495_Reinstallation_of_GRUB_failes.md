---
title: "Reinstallation of GRUB failes"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by Hellboy256 on 2015-01-12
I have installed W7 as a second OS with dual boot on my notebook which was already running Ubuntu 14.10. 
W7 was installed on the HDD. For Ubuntu the /home and /usr/share are  installed on the HDD and the rest is installed on the the additional  SSD. After the installation of W7 the grub boot menu was deleted so I  tried to reinstall it with a live CD. 
 
I run boot-repair and selected Recommended repair which then gave me a prompt saying:
```

apt-error detected. Please open a terminal then type (or copy-paste) the following command:
sudo chroot "/mnt/boot-sav/sdb2" apt-get -f install

```

But when I run this command I get:
```

 debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (you may need to install the strict module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.20.1 /usr/local/share/perl/5.20.1 /usr/lib/x86_64-linux-gnu/perl5/5.20 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.20 /usr/share/perl/5.20 /usr/local/lib/site_perl .) at (eval 1) line 2.
  BEGIN failed--compilation aborted at (eval 1) line 2.
 ) -- aborting
 E: Can not write log (Is /dev/pts mounted?) - posix_openpt (2: No such file or directory)
 Setting up install-info (5.2.0.dfsg.1-4) ...
 Not a directory: /usr/share/info.
 dpkg: error processing package install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
 Errors were encountered while processing:
 install-info
 E: Sub-process /usr/bin/dpkg returned an error code (1)


```
I tried to run sudo apt-get install -f and sudo apt-get autoremove but didn't help...

---

### Post by fantab on 2015-01-12
Try this: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Its probably some bad pacakge.
After you've chrooted (as shown in the link page) with *sudo chroot /mnt* update and upgrade ubuntu with:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

..report back if you get errors. If you don't get any errors then just re-install grub as described in the link.

Also post the link to bootinfo summary that boot-repair creates.

---

### Post by Hellboy256 on 2015-01-12
When I run `sudo apt-get update && sudo apt-get dist-upgrade`
I get this 

```

W: Some index files failed to download. They have been ignored, or old ones used instead.
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 grub-pc : Depends: grub-common (= 2.02~beta2-15)
           Depends: grub2-common (= 2.02~beta2-15)
           Depends: grub-pc-bin (= 2.02~beta2-15)
           Depends: grub-gfxpayload-lists but it is not installed
E: Unmet dependencies. Try using -f.

```

I have tried to run `sudo apt-get -f install` but then I get the same error as in my first post


When I run the command as mentioned in the link I get the following error:

```

root@ubuntu:/# grub-install /dev/sdb
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/command-not-found/+filebug
Please include the following information with the report:

command-not-found version: 0.3
Python version: 3.4.2 final 0
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic
Exception information:

[Errno 2] No such file or directory: '/usr/share/command-not-found/programs.d'
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/util.py", line 24, in crash_guard
    callback()
  File "/usr/lib/command-not-found", line 89, in main
    cnf = CommandNotFound(options.data_dir)
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 131, in __init__
    for filename in os.listdir(os.path.sep.join([data_dir, self.programs_dir])):
FileNotFoundError: [Errno 2] No such file or directory: '/usr/share/command-not-found/programs.d'


```

---

### Post by Bashing-om on 2015-01-12
Hellboy256; UnGood !

Before we go (RE-)installing grub, let's make sure of what we are working with so we know where to install the boot code to.
Please post back the outputs of terminal commands:
From the liveDVD:
```

sudo fdisk -lu
sudo parted -l

```
We then see what we can do.

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by fantab on 2015-01-13
Post the **Bootinfo Summary** from Boot-Repair tool (just post the URL), as requested earlier. That should also take care of Bashing-om's request.

---

### Post by grahammechanical on 2015-01-13
this is the bit that I do not understand

> [COLOR=#000000]For Ubuntu the /home and /usr/share are installed on the HDD and the rest is installed on the the additional SSD.[/COLOR]

Does that mean that Ubuntu / is on the SSD along with all the other system folders but /usr is on the HDD? I can see a point to having Ubuntu on the SSD and /home on the HDD but splitting Ubuntu in that way, I am not sure what the advantage would be. Have you checked to see if there are any Grub folders in /usr/share/? There are on my system. I do not like complications.

Regards

---

