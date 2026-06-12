---
title: "How do you clean up Linux and why?"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by gregoryshock on 2013-03-08
In windows you have a program called Diskcleanup. You can also add on other utilities like Ccleaner.  I have been wondering If or what programs in Linux does the samething for the Linux system.  Also How often a person should do it?  I've already discovered on my system two programs for cleaning up stuff.  But as far as what they are cleaning and if it is good or not, I don't know.  The One program is called Janitor.  The other I found in the ubuntu software center.  It is called: Bleachbit.  My goal here is to get rid of Cache and other unneeded stored information.  Also on Windows I use CCleaner to get rid of flash cookies.  How do you do that on Linux?

---

### Post by ibjsb4 on 2013-03-08
I use BleachBit and it works well.  Just be careful about what you clean.

If you wish to give it a spin I will help you with the setup.

---

### Post by LuisGMarine on 2013-03-08
> **gregoryshock said:**
> In windows you have a program called Diskcleanup. You can also add on other utilities like Ccleaner.  I have been wondering If or what programs in Linux does the samething for the Linux system.  Also How often a person should do it?  I've already discovered on my system two programs for cleaning up stuff.  But as far as what they are cleaning and if it is good or not, I don't know.  The One program is called Janitor.  The other I found in the ubuntu software center.  It is called: Bleachbit.  My goal here is to get rid of Cache and other unneeded stored information.  Also on Windows I use CCleaner to get rid of flash cookies.  How do you do that on Linux?

Using both programs that you just mentioned will sufice for what you are looking for.  If you want to learn about a few more things that you can clean up here is a guide that I think does a good job of getting you started.  [http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07]("http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07")

---

### Post by Frogs Hair on 2013-03-08
Ubuntu/ linux  doesn't use a registry so there are no keys to remove which is a function of Ccleaner. If using Firefox set this add-on to delete LSO/ flash cookies at browser close or open. [https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/)

---

### Post by bryanl on 2013-03-08
Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) has a "janitor" that will clean up a lot of cruft such as old kernels, apt-cache, and whatnot.

---

### Post by Kopkins on 2013-03-08
I have a very simple script for cleaning out apt whenever I feel the need.

I have it in /usr/local/bin/clean

So I just type clean into a terminal and it automatically clears out a few places that I want cleaned.

```

#!/bin/bash
#script to do a quick apt cleaning
sudo apt-get --purge autoremove #removes unneeded packages that were installed to satisfy dependencies along with their config files.
sudo apt-get autoclean          #removes obselete files/packages that can no longer be downloaded
sudo apt-get clean              #removes the downloaded packages to free disk space
exit

```

Of course this is not all of the things you should be cleaning out. The link to Make Tech Easier has some good suggestions.

Kopkins

---

### Post by woxuxow on 2013-03-08
I don`t
i thnik there is no need to cleanup your GNU/Linux like what you do in windows
i just clean apt cache , browser garbage and old kernels
of course i use clean install every 6 month

---

### Post by slickymaster on 2013-03-08
[Ubucleaner]("http://www.opendesktop.org/content/show.php/Ubucleaner?content=71529") script:

```
#!/bin/bash

OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED"Error: must be root"
  echo -e $YELLOW"Exiting..."$ENDCOLOR
  exit 0
fi

echo -e $YELLOW"Cleaning apt cache..."$ENDCOLOR
aptitude clean

echo -e $YELLOW"Removing old config files..."$ENDCOLOR
sudo aptitude purge $OLDCONF

echo -e $YELLOW"Removing old kernels..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"Emptying every trashes..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null

echo -e $YELLOW"Script Finished!"$ENDCOLOR
```

---

### Post by schragge on 2013-03-08
The only problem with Ubucleaner is that it's for older Ubuntu releases: e.g. from all currently supported releases packages *linux-ubuntu-modules-** are present only in hardy (8.04LTS), on the other hand, beginning from oneiric (11.10) there are *linux-image-extra-** that Ubucleaner doesn't know of. I tried to clean up Ubucleaner a bit, the result is [post=12533994]here[/post].

---

### Post by oldos2er on 2013-03-08
See [this thread]("http://ubuntuforums.org/showthread.php?t=1734711") for dealing with flash cookies.

---

### Post by blackbird34 on 2013-03-09
I'd advise Bleachbit over the Janitor, Janitor's been known to be buggy.

---

### Post by fiodev on 2013-03-09
sudo -s
apt-get autoremove && apt-get autoclean -y

---

### Post by schragge on 2013-03-09
[highlight]Edit.[/highlight] This one was plain wrong. I stand corrected.
[s]It must be quoted if written in one line[/s]

---

### Post by ibjsb4 on 2013-03-09
host@host:~$ [COLOR=#ff0000]sudo -s
root@host:~# apt-get autoremove && apt-get autoclean -y[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done


root@host:~#[COLOR=#ff0000] 'apt-get autoremove;apt-get -y autoclean'[/COLOR]
/bin/bash: apt-get autoremove;apt-get -y autoclean: command not found

..:confused:

---

### Post by schragge on 2013-03-10
[highlight]Edit.[/highlight] Corrected. **ibjsb4** and **sudodus**, thanks for pointing out my mistake.
[s]Once again, when written _on one line_.[/s]

[highlight]Edit.[/highlight] *The paragraphs below are correct now, but completely off-topic here.*

It's often used to get redirections right with sudo. E.g.
```
[COLOR=#ff0000]sudo echo 10 >/proc/sys/vm/swappiness[/COLOR]
``` is wrong as *sudo *only affects *echo*, but redirections are executed with regular user's permissions, and normal user doesn't have write access to */proc/sys/vm/swappiness*. To get redirection work, this could be rewritten as either
```
echo 10 | sudo tee /proc/sys/vm/swappiness
``` or ```
sudo sh -c 'echo 10 >/proc/sys/vm/swappiness'
```
This example is somewhat contrived as the right way to change [swappiness]("http://en.wikipedia.org/wiki/Swappiness") is
```
sudo sysctl vm.swappiness=10
```

---

### Post by zer010 on 2013-03-10
I definitely suggest [bleachbit.]("http://bleachbit.sourceforge.net/")  When the issue arose about ever-cookies, the bleachbit dev was the first to confirm deletion of said cookies. Flash and all other manner of cruft is removed. It's also one that I use for Windows, just too bad it doesn't clean the registry. Then I'd put over and above CCleaner.

---

### Post by ibjsb4 on 2013-03-10
> **schragge said:**
> Once again, when written _on one line_.
```
sudo -s  'apt-get autoremove;apt-get -y autoclean'
```

host@host:~$ sudo -s  'apt-get autoremove;apt-get -y autoclean'
[sudo] password for host: 
/bin/bash: apt-get autoremove;apt-get -y autoclean: command not found

Once again it does not work, have you even tried it?

---

### Post by blackbird34 on 2013-03-10
> **ibjsb4 said:**
> host@host:~$ sudo -s  'apt-get autoremove;apt-get -y autoclean'
[sudo] password for host: 
/bin/bash: apt-get autoremove;apt-get -y autoclean: command not found

Once again it does not work, have you even tried it?

Once you are root, you can just do ```
apt-get autoremove && apt-get -y autoclean
```

The '&&' always works, as a way of stringing two commands together. I do sudo apt-get update && sudo apt-get dist-upgrade for all my updates, flawless.

---

### Post by ibjsb4 on 2013-03-10
Thank you blackbird34, Yes your command will work fine.  I was just trying to find out why [**[COLOR=#000000]schragge[/COLOR]**]("http://ubuntuforums.org/member.php?u=1783515") would post non-working commands and also would like to know what swappiness has to do with cleaning up linux.

---

### Post by schragge on 2013-03-11
> **ibjsb4 said:**
> Once again it does not work, have you even tried it?:oops: No, I haven't. I read about *sudo -s* in the sudo manual page, and somehow assumed it would work. Thank you for correcting my misconception! Lesson learned. As I see now, *sudo -s* is equivalent to *sudo -i* except for the environment not being changed to that of root. That means it will work only in the following form (yes, now I've tested it):
```
sudo -s eval 'apt-get -y autoremove;apt-get autoclean'
``` or, better yet
```
sudo -i eval 'apt-get -y autoremove;apt-get autoclean'
```
Note also that it makes more sense using the option -y/--assume-yes with *autoremove* than with *autoclean* as *autoclean* usually won't ask you any questions anyway.

Just for fun, the shortest command equivalent to the *sudo -s eval* shown above is probably
```

sudo sh -c '$0 -y autoremove;$0 autoclean' apt-get

``` :)

---

### Post by HermanAB on 2013-03-11
Howdy,

A properly configured Linux system is self cleaning and can run for years on end with zero human intervention.

Read up on logrotate and its configuration file logrotate.conf.

---

### Post by siddharth007 on 2013-03-11
I second bryanl.Try Ubuntu Tweak.For its features follow this [link]("http://bluesteel007india.blogspot.com/2013/03/tweak-your-ubuntu-with-this-smart-tool.html")

---

