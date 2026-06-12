---
title: "What's wrong with my problem?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by kcoylenet on 2008-08-19
Sorry to do this, but I've posted this problem twice now and got zero replies. There are other users having the same problem, and also not getting replies. So I need to know if I'm not posting the right information, or if this is a particularly difficult problem... I guess I just need some feedback, any feedback! Thanks. Here's what I posted before:

I was doing updates to gutsy gibbon, and I keep getting this error:

dpkg: error processing cupsys (--configure):
subprocess post-installation script returned error exit status 1

I've done apt-get -f install a number of times and this keeps happening. I tried:

apt-get -r cupsys

and got

hplip depends on cupsys (>= 1.1.20).
ubuntu-desktop depends on cupsys.
cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
Package cupsys is to be removed.
Package cups is not installed.
bluez-cups depends on cupsys.
hal-cups-utils depends on cupsys.
cups-pdf depends on cupsys.
cups-pdf depends on cupsys (>= 1.1.15).
cups-pdf depends on cupsys.
cups-pdf depends on cupsys (>= 1.1.15).
dpkg: error processing cupsys (--remove):
dependency problems - not removing

Now I can't install any packages because I keep getting this error. Anyone know of a way to fix it?

Thanks again, and sorry for the repeat posts.
kc

---

### Post by loell on 2008-08-19
oh, most probably your package manager is badly messed up :(

---

### Post by phidia on 2008-08-19
Try > sudo apt-get clean all && apt-get update

---

### Post by kcoylenet on 2008-08-19
That gets me:

karen@karen-desktop:~$ sudo apt-get clean all && apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Sounds like something didn't finish correctly. Can I manually unlock?

---

### Post by kcoylenet on 2008-08-19
Note: I can "sudo vi lock" successfully.

---

### Post by mellowd on 2008-08-19
odd.

what happens if you type this?

```
sudo aptitude install cupsys
```

---

### Post by kbeswick on 2008-08-19
> **kcoylenet said:**
> That gets me:

karen@karen-desktop:~$ sudo apt-get clean all && apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Sounds like something didn't finish correctly. Can I manually unlock?

the command should have been : 

sudo apt-get clean all && sudo apt-get update

---

### Post by halitech on 2008-08-19
going to ask a (possibly) dumb question, you don't have synaptic open when you are trying to use the command line to install stuff?

---

### Post by sameerds on 2008-08-19
> **kcoylenet said:**
> 
hplip depends on cupsys (>= 1.1.20).
ubuntu-desktop depends on cupsys.
cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
Package cupsys is to be removed.
Package cups is not installed.
bluez-cups depends on cupsys.
hal-cups-utils depends on cupsys.
cups-pdf depends on cupsys.
cups-pdf depends on cupsys (>= 1.1.15).
cups-pdf depends on cupsys.
cups-pdf depends on cupsys (>= 1.1.15).
dpkg: error processing cupsys (--remove):
dependency problems - not removing


Just making a wild guess here, maybe you have already tried it ... try removing everything that is listed as "depends on cupsys" in the above output, in one single command:

```
apt-get remove cupsys hplip ubuntu-desktop ...
```

Don't worry about uninstalling "ubuntu-desktop" btw, its just a dummy package that installs many other packages. Nothing depends on it:

```

sameerds@gajanan:~$ aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: not installed
Version: 1.102
Priority: optional
Section: metapackages
...

```

---

### Post by egh on 2008-08-19
Responding You have a bad package (cupsys) whose install script is giving an error. This is in my experience the most vulnerable part of the generally quite stable debian packaging system, because one packages bad script can cause your whole system to be in a bad state.

I have had luck in the past with the following:

```
sudo dpkg --purge --force-depends cupsys
```

This will purge cupsys from your system, ignoring the fact that other packages depend on it.

Then, when you are finished with that:

```
sudo apt-get -f install
```

will reinstall cupsys.

This will wipe out any configuration for cupsys (printing), so you will have to reconfigure your printers, if you use any.

---

### Post by kcoylenet on 2008-08-19
did the dpkg --purge etc. then -f install; get:

dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

Actually, for a minute there I thought it was going to work! So at least you've given me hope. ;-) thanks.

---

### Post by kcoylenet on 2008-08-19
> **halitech said:**
> going to ask a (possibly) dumb question, you don't have synaptic open when you are trying to use the command line to install stuff?
Actually, I don't really know what 'synaptic' is, but i haven't consciously opened anything with that name.

---

### Post by egh on 2008-08-19
Googling around it looks like cupsys has some issues.

If you don't need to print the best thing to do might be to remove cupsys permanently.

If you do need to print (& most of us do), could you try doing a:

```
sudo dpkg --purge --force-depends cupsys
```

to try to get everything in a good state? Then you might want to ensure that there are no cups processes around still:

```
ps -fade |grep cups
```

should not have a process that looks like /usr/sbin/cupds; if it does, do a 

```
sudo killall -9 cupsd
```

And then finally we can try a:

```
sudo apt-get update && sudo apt-get dist-upgrade; sudo apt-get -f install
```

& cross our fingers.

---

### Post by kcoylenet on 2008-08-19
> **mellowd said:**
> odd.

what happens if you type this?

```
sudo aptitude install cupsys
```
Thanks. I did that, then did apt-get -f install again (since that's now the output I know how to read) and I still get that cupsys config error. But it was worth a try!

---

### Post by egh on 2008-08-19
> **kcoylenet said:**
> Actually, I don't really know what 'synaptic' is, but i haven't consciously opened anything with that name.

synaptic is the ubuntu graphical package manager.

---

### Post by Irihapeti on 2008-08-19
I had a similar problem about a year ago with a different package.

You might like to try this, which (with a different program name, obviously) fixed my problem:

```
sudo dpkg --remove --force-remove-reinstreq cupsys
```


Irihapeti

---

### Post by kcoylenet on 2008-08-19
Thanks. That command gets me:

dpkg: dependency problems prevent removal of cupsys:
 hplip depends on cupsys (>= 1.1.20).
 ubuntu-desktop depends on cupsys.
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is to be removed.
  Package cups is not installed.
 bluez-cups depends on cupsys.
 hal-cups-utils depends on cupsys.
 cups-pdf depends on cupsys.
 cups-pdf depends on cupsys (>= 1.1.15).
 cups-pdf depends on cupsys.
 cups-pdf depends on cupsys (>= 1.1.15).
dpkg: error processing cupsys (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 cupsys

This *$&#$^ cupsys really needs to go!

---

### Post by kcoylenet on 2008-08-19
> **egh said:**
> synaptic is the ubuntu graphical package manager.
I'd only used the add/remove and the command line, so I opened up synaptic and tried to re-install cupsys. I got the same error:
  "E: cupsys: subprocess post-installation script returned error exit status 1"

Then I marked cupsys for removal, and it said that it would also remove the dependent packages. --- got the same error 

then i re-did apt-get install cupsys (after closing synaptic) and got the same error. (Yes, I think I'm repeating some operations, but I just can't seem to stop.)

---

### Post by Irihapeti on 2008-08-19
What happens if you add --force-depends to the command I gave above? i.e.

```
sudo dpkg --remove --force-depends --force-remove-reinstreq cupsys
```

Note: I'm suggesting things here I haven't done myself, so you might want to wait for a second opinion before you try it. :)

Irihapeti

---

### Post by kcoylenet on 2008-08-20
> **Irihapeti said:**
> What happens if you add --force-depends to the command I gave above? i.e.

```
sudo dpkg --remove --force-depends --force-remove-reinstreq cupsys
```

Note: I'm suggesting things here I haven't done myself, so you might want to wait for a second opinion before you try it. :)

Irihapeti
That gets me:

(Reading database ... 124801 files and directories currently installed.)
Removing cupsys ...
 * Stopping Common Unix Printing System: cupsd  

and then i did apt-get install cupsys and got:

dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupsys (1.3.2-1ubuntu7.7) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done   

I'm now going to hook up an external drive and do a full backup. I see a re-install of Ubuntu in my future. :-)

kc

---

### Post by meindian523 on 2008-08-20
Please post ```
ls /var/cache/apt/archives/partial
```

---

### Post by philinux on 2008-08-20
Try this


sudo dpkg --configure -a

---

### Post by loell on 2008-08-20
> **kcoylenet said:**
> 

I'm now going to hook up an external drive and do a full backup. I see a re-install of Ubuntu in my future. :-)

kc

good clairvoyance :)  and a positive fall back plan. :KS

---

### Post by egh on 2008-08-20
Ok, one final try.

It looks like you might be having some trouble with AppArmor. AppArmor was in my opinion not ready for inclusion by default in Gutsy; I have had some problems with it & I know others have as well. So I would advise that you try removing it:

```
sudo apt-get remove apparmor
```

and then reinstalling cupsys.

Best of luck!

---

### Post by egh on 2008-08-20
PS: Others have the same problem.

[http://ubuntuforums.org/archive/index.php/t-630182.html](http://ubuntuforums.org/archive/index.php/t-630182.html)

---

### Post by egh on 2008-08-20
Also: [http://georgia.ubuntuforums.org/showthread.php?t=629322](http://georgia.ubuntuforums.org/showthread.php?t=629322)

---

### Post by kcoylenet on 2008-08-20
> **meindian523 said:**
> Please post ```
ls /var/cache/apt/archives/partial
```
karen@karen-desktop:/var/cache/apt/archives/partial is empty

karen@karen-desktop:/var/cache/apt/archives/partial$ ls
total 0

---

### Post by kcoylenet on 2008-08-20
> **egh said:**
> Also: [http://georgia.ubuntuforums.org/showthread.php?t=629322](http://georgia.ubuntuforums.org/showthread.php?t=629322)
This thread had the following steps:

To fix broken packages:

1. Try to configure all packages that are not configured :
sudo dpkg --configure -a

2. Try to let apt-get remove all problematic packages:
sudo aptitude -f remove

3. Rerun this after running the command above:
sudo dpkg --configure -a

4. To remove left-overs (dependencies) etc:
sudo apt-get remove
sudo apt-get autoremove

5. Reinstall problematic package, and check if there are no dependencies which cannot be met.

I did them all... unfortunately this didn't work either, although it did for the original poster on that thread (who I now envy greatly.)

kc

---

### Post by kcoylenet on 2008-08-20
I tried the apparmor hint. I did:

1. sudo apt-get remove apparmor
2. sudo apt-get install cupsys
 -- same error: dpkg: error processing cupsys (--configure)

then I tried

3. sudo apt-get remove cupsys
4. sudo apt-get install cupsys

 -- same error: dpkg: error processing cupsys (--configure)

*********

"Consistency is all I ask!" (Rosencrantz and Guildenstern are Dead, by Tom Stoppard) -- I should be ecstatic by now.

---

### Post by philinux on 2008-08-20
Did you try this as i suggested before. It might just sort it out.

```
sudo dpkg --configure -a
```

---

### Post by LowSky on 2008-08-20
what kind of printer are you using?
try
```
sudo aa-complain cupsd
```
or grap cupsys from source
you can get cupsys directly from here.
[http://packages.ubuntu.com/gutsy/cupsys](http://packages.ubuntu.com/gutsy/cupsys)

---

### Post by kcoylenet on 2008-08-20
> **philinux said:**
> Did you try this as i suggested before. It might just sort it out.

```
sudo dpkg --configure -a
```
Yes, tried that one, thanks. Same error.

---

### Post by kcoylenet on 2008-08-20
> **LowSky said:**
> what kind of printer are you using?
try
```
sudo aa-complain cupsd
```
or grap cupsys from source
you can get cupsys directly from here.
[http://packages.ubuntu.com/gutsy/cupsys](http://packages.ubuntu.com/gutsy/cupsys)
I did:
  sudo aa-complain cupsd

and got a 'command not found' 

I'm using a Laserjet 1100 -- well , I was before I started all of this. It did still work after I got this error, but now that I've tried to remove cups numerous times it isn't showing in the system manager, and I tried 'start cups' and 'start cupsys' and 'start cupsd' -- but there are 223 files with "cups" in the name, and many named "cups".

---

### Post by kcoylenet on 2008-08-20
OK, here's something interesting relating to apparmor.

There's a post here:
  [https://answers.launchpad.net/ubuntu/+question/27690](https://answers.launchpad.net/ubuntu/+question/27690)

that refers to apparmor/usr.sbin.cupsd. That's what aa-complain is supposed to fix in some way. On my system, usr.sbin.cupsd in in apparmor.d/ and there's no aa-complain command. I attempted to remove apparmor but undoubtedly it didn't happen because of this cupsys error. 

Meanwhile, I copied usr.sbin.cupsd to apparmor and did: sudo apt-get install apparmor-utils  per the instructions that popped up on my screen, and I now have cupsd set to 'complain'. However, my apt-get -f install still

gives

me

the

same

error.

I realize that any NORMAL person would have given up by now. 

kc

---

### Post by egh on 2008-08-20
> **kcoylenet said:**
> 
Meanwhile, I copied usr.sbin.cupsd to apparmor and did: sudo apt-get install apparmor-utils  per the instructions that popped up on my screen, and I now have cupsd set to 'complain'. However, my apt-get -f install still

gives

me

the

same

error.

I realize that any NORMAL person would have given up by now. 

kc

You might want to file a bug...it is a bit of work but what you are dealing with is definitely a bug. cupsys should not break dpkg.

You can get more information about why the post-install script is failing by running it by hand with the -x option, as:

```
sudo /bin/sh -x  /var/lib/dpkg/info/cupsys.postinst configure
```

Bugs for ubuntu packages can be filed at [https://bugs.launchpad.net/ubuntu/+source/cupsys](https://bugs.launchpad.net/ubuntu/+source/cupsys)

Thanks for sticking this out.

---

### Post by Irihapeti on 2008-08-20
> **kcoylenet said:**
> 

I realize that any NORMAL person would have given up by now. 

kc

Thank goodness you're not normal. I think it's not-normal people that hold the world together (and advance it). :)

A "normal" person also might have posted a huge rant in another section on not getting help. Kudos to you that you didn't.


At the moment, it's starting to look as though you may have to reinstall. OK, this is off topic, but if it comes to that, you could look at doing a regular backup of just your system (i.e. not including home directory) to a tar.gz file or similar. More than once I've had to reinstall because I broke something, and these backups have saved me an awful lot of time reinstalling packages and reconfiguring things. I also backup my home directory but I do it separately.

All the same, I hope that *someone* can give you the magic command that will fix things.

Irihapeti

---

### Post by egh on 2008-08-21
ok, a bit more searching, this problem bugged me.

The problem is not really with cupsys, but a mismatch between the cups packages install scripts & the sysv init package. You will find more information & a possible fix here:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/237519](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/237519)

Hopefully this can prevent you from reinstalling!

---

### Post by kcoylenet on 2008-08-23
Thanks, I tried the command in that bug listing, but what I got was that 

E: Version '2.86.ds1-14.1ubuntu45' for 'sysv-rc' was not found

So I looked up sysv-rc and tried versions 38 and 61 (38 seems to be the Debian etch version). Neither existed. So then I tried it without the "lunbuntu":

sudo apt-get install sysv-rc=2.86.ds1-38

This got me the message:

sysv-rc is already the newest version.

Looking in the sysv-rc folder at the change log, the latest entry is for -38, so I assume that's what I'm running. -14 doesn't seem to be available. -38 is dated January, 2007.

So... it looks like I need to get access to the source of -14 for ubuntu. I know that somewhere there is a file with the list of repositories, and maybe I need to add something? Can someone find this -14 and tell me how I can get to it?

Thanks!

---

### Post by kcoylenet on 2008-08-24
In that previous listing, I used the word "source" -- not in the sense of "source code" but in the sense of "fount," e.g. "where it is."

---

### Post by egh on 2008-08-26
you can find out the version of sysv-rc you are running with the command:

```

dpkg -l sysv-rc

```

On the latest version of ubuntu you should get something like:

```

egh@gales:~$ dpkg -l sysv-rc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                    Version                                 Description
+++-=======================================-=======================================-==============================================================================================
ii  sysv-rc                                 2.86.ds1-14.1ubuntu45                   System-V-like runlevel change mechanism

```

If you have a different version & cannot install this version you might have a problem with versions in your /etc/apt/sources.list file.

Here is mine:
```

egh@gales:~$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main multiverse restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main multiverse restricted universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy main multiverse restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main multiverse restricted universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main multiverse restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main multiverse restricted universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb-src http://ftp.indexdata.dk/debian indexdata/etch released

```

You can see from the appearance of 'hardy' that I am on the latest Ubuntu. I've been presuming that you also are on Hardy? By the way, you can see there also the indexdata sources you can use for installing yaz, etc. from source.

/Erik

---

### Post by hyperhopper on 2008-08-26
To answer the question in the title- nothing is wrong with your problem. The a only way it could be is if there was no problem in your problem, thus making it a problem problem. :mrgreen:

---

### Post by kcoylenet on 2008-08-29
Thanks, Erik. I'll update my sources.list. Meanwhile, to fix everything I first tried upgrading from Gutsy to Hardy -- which failed in just the last few minutes. But I was prepared for a clean install, which I have done, and will start restoring some of my personal files. Fortunately, there aren't many. 

I greatly appreciate all of the help here. And hope I get to the point some day of being able to return the favor! But meanwhile, you all may hear from me again. ;-)

---

### Post by emvy on 2008-09-02
Hey, I have the same problem here (with Gutsy). Tried all the solutions proposed here and still nothing changed. I would like to know if re-installing the OS solves the problem or it still remains. thnx in advance!!![-o<

---

