---
title: "[SOLVED] Cancel an apt-get installation"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Tiekyl on 2008-06-28
Hey all, 

I've searched around the forums and google for "cancel apt installation" and whatnot, and most of the posts seem to be talking about how to fix it, and tell you to dpkg --configure -a ..

I started trying to install flash through the apt system, and I forgot that the servers never seem to work for me. I found my old .tar.gz file, and installed it, but now I'm stuck with it trying to install. Is there anyway to just tell it that I don't want to install anymore? 

Thanks,

Katie

---

### Post by drs305 on 2008-06-28
You can try running this command:
```
sudo apt-get autoclean
```

and/or emptying /var/cache/apt/archives/partial
To do that, open a file manager using the gksudo command, such as:
```
gksudo nautilus /var/cache/apt/archives/partial
```

Delete the files within "partial" but not the folder itself.

---

### Post by Tiekyl on 2008-06-28
Well, the autoclean doesnt work, it said it was locked, and the partial directory was empty..

-Thanks though

---

### Post by drs305 on 2008-06-28
With an aborted tar.gz installation, do you still have the installation folder? Sometimes there is a 'postinst' folder with a removal script. Or there might be another script that would apply. If the folder exists, you could also try to rename/delete it.

By the way, keeping installation folders after a tar.gz install is a good thing since even with a successful install it is often the only method of cleanly uninstalling an app that isn't registered with dpkg.

---

### Post by Tiekyl on 2008-06-28
Sorry about the slow replys, been incessently restarting to try to fix this. It wasnt an aborted .tar.gz install though, it was through apt that I was having problems. The server just isn't responding to me.

---

### Post by drs305 on 2008-06-28
Here's my next brainstorm, now that I understand it's a hung apt install. This may work if the entire aptitude system isn't locked. Make sure no other synaptic is running.

First, trying the usual options:


```

sudo killall aptitude
sudo killall synaptic
sudo aptitude purge **appname** && sudo aptitude remove **appname** && sudo aptitude clean && sudo aptitude autoclean
```

When that doesn't work ;-)
Generate a list of installed packages and see if you can find the one you attempted to install:
```
sudo dpkg --get-selections >~/Desktop/bad-install 
gedit ~/Desktop/bad-install

```

If you find the troublemaker, check the status. Either change it to 'deinstall' or remove it completely. Then run:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/bad-install 	
sudo apt-get -u dselect-upgrade

```

Maybe that will clear it. If nothing else, it bumps your thread. Good luck.

---

### Post by Tiekyl on 2008-06-28
Yay! It finally worked, thank you so much. Everything didnt work until the clearing of it out of the conf file, or whatever it was. Its re-updating now, but I'm very happy now ^_^ Thanks!

---

### Post by drs305 on 2008-06-28
> **Tiekyl said:**
> Yay! It finally worked, thank you so much. Everything didnt work until the clearing of it out of the conf file, or whatever it was. Its re-updating now, but I'm very happy now ^_^ Thanks!

I'm just curious - how was the app's status listed in the generated file?

Glad you finally got this resolved. :)

---

### Post by unutbu on 2008-06-28
> **Tiekyl said:**
> Everything didnt work until the clearing of it out of the conf file

It sounds like the package was never truly purged. 
That would mean you might have fragments of the package's files on your hard drive just taking up space. If you want to get rid of them, try

```
sudo apt-get install packagename
sudo apt-get purge packagename
```

Edit: drs305, please correct me if I'm wrong. I'm not familiar with the command
"sudo apt-get -u dselect-upgrade"
If a package has been marked "deinstall" does it mean the package has already been deinstalled, or that it should be deinstalled if currently installed? 

If Tiekyl simply erased that line from ~/Desktop/bad-install, wouldn't "apt-get dselect-upgrade" simply do nothing? I doubt it would remove the package.

---

### Post by drs305 on 2008-06-28
unbuntu,

the problem was that the app would never complete an install. he tried, or at least i suggested, using purge but apparently it couldn't break through and get it done for some reason. 

creating a list of the current status of all packages was my last attempt at getting dpkg/apt to forget trying to complete the installation. one of the reasons i asked about what the generated list contained was that i would like to know whether it was listed as deinstall, install or something else. i am fairly certain deinstall is a status for packages awaiting removal and would probably be found by synaptic's residual config filter. 

if you run the command and then inspect the file there are very few, if any, packages marked deinstall. i constantly add and remove apps to try to figure out what's happening on other reader's computers and my list would contain dozens if not hundreds of old apps if it retained them in history. 

you are correct that the final command in the sequence would do nothing about removing the package. the solution was not a clean uninstall. your suggestion to run the install and purge was something i was going to recommend after he got all his updates completed and i did some further investigation. i just didn't have the heart to ask him to try it again so soon. i was also a bit concerned about how it would affect his install via the tar.gz installation. although dpkg wouldn't have registered that installation i wasn't sure if a fresh install/removal via apt would find and remove any of his other files. 

as for deselect-upgrade command, that is just the command i suggested to try to get apt to accurately reflect and update the status of things. since he removed a line from the generated list without going through the normal procedures i suggested this line in hopes it would reset the list to accurately reflect the status of the packages.

---

### Post by Tiekyl on 2008-06-29
Er, I accidently got distracted with one of the programs that I finally got to install last night after this started working. 

In the generated file, it was listed as "install", so I changed it to deinstall rather than deleting it, just in case I couldn't remember the file name later. 

I am running the reinstallation now, I'll let it run for a few hours, see if it can finish finding the server. 

You guys have been great though. Mucho thanks.

---

### Post by drs305 on 2008-06-29
> **Tiekyl said:**
> Er, I accidently got distracted with one of the programs that I finally got to install last night after this started working. 

In the generated file, it was listed as "install", so I changed it to deinstall rather than deleting it, just in case I couldn't remember the file name later. 

I am running the reinstallation now, I'll let it run for a few hours, see if it can finish finding the server. 

You guys have been great though. Mucho thanks.

I wouldn't use the technique we came up with on a normal basis. The apt system is very versatile and usually does a good job of keeping track of things. There are various commands using aptitude, apt-get and dpkg that will keep everything orderly and these are what should normally be used.

You can read about them by typing "man aptitude" or "man apt-get". The options regarding package maintenance include remove, purge, clean, and autoclean.

---

### Post by Tiekyl on 2008-06-29
I will likely not use that again, I'll make sure I dont need to. 

There really should be a way to cancel a pending installation though, seems like it could come in handy...

---

### Post by drs305 on 2008-06-29
> **Tiekyl said:**
> I will likely not use that again, I'll make sure I dont need to. 

There really should be a way to cancel a pending installation though, seems like it could come in handy...

There is a 'keep' switch to aptitude that may work in some cases. Hopefully there won't be a next time but if so we'll explore it.

---

### Post by unutbu on 2008-06-29
By the way drs305, when I run 

```
dpkg --get-selections > ~/tmp/selections
grep deinstall ~/tmp/selections 
```

I see each of the packages that I have removed with

```
sudo apt-get remove
```

I see stuff like this:```

acct						deinstall
audacious					deinstall
emacs22						deinstall
emacs22-bin-common				deinstall
emacs22-common					deinstall
emacs22-gtk					deinstall
eog						deinstall
...

```
I understand that the config files are still present. 

1) Do you know a CLI command which shows where the config files are?
2) Do you know a CLI command which removes the config files?

When I run 
```

child@play:~% df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            299463656  30090168 266331100  11% /
...
child@play:~% sudo apt-get purge acct
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acct is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
child@play:~% df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            299463656  30090168 266331100  11% /
...

```
I can see from the df commands that nothing has been removed.

---

### Post by drs305 on 2008-06-29
> **unutbu said:**
> 

1) Do you know a CLI command which shows where the config files are?
2) Do you know a CLI command which removes the config files?


No, and it bothers me. I haven't had the time since this thread started to do the research to find an answer. The only way I know to get it now is to run the --get-selections command.

---

### Post by unutbu on 2008-06-29
I think I now know the answer to this question:
> 2) Do you know a CLI command which removes the config files?
```

% sudo dpkg --purge acct
(Reading database ... 179959 files and directories currently installed.)
Removing acct ...
Purging configuration files for acct ...
rm: **cannot remove `/var/log/account'**: No such file or directory
dpkg: error processing acct (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 acct

% sudo touch /var/log/account
% sudo dpkg --purge acct
(Reading database ... 179959 files and directories currently installed.)
Removing acct ...
**Purging configuration files for acct ...**
removed `/var/log/account'
```

It was /var/log/account that was holding everything else up. Now 

```
%  dpkg --get-selections | grep deinstall | awk '{print $1}' | xargs sudo dpkg --purge 
```

happily purged all my other "residual config" packages.

---

### Post by unutbu on 2008-06-29
When it rains, it pours. I now know the answer to this:
> 1) Do you know a CLI command which shows where the config files are?
For any package whose config files are still on the machine, run `dpkg --status <package>`. The files listed under Conffile are precisely the ones that won't be removed by `apt-get remove` but will be removed by `apt-get purge`. For example,

```
% dpkg --status a2ps
22:22:32 atom@rest:~% Package: a2ps
Status: install ok installed
Priority: optional
Section: text
Installed-Size: 3056
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 1:4.13c~rc5-1
Depends: libc6 (>= 2.5-0ubuntu1), libpaper1, file, psutils
Recommends: bzip2, lpr | rlpr | cupsys-client, wdiff
Suggests: emacsen-common, groff, gs-common, gv, html2ps, imagemagick, tetex-bin, t1-cyrillic
Conffiles:
[B] /etc/a2ps.cfg 0e3b5fb6411af0914b377bda6c05f192
 /etc/a2ps-site.cfg a0350f2cd325c85160950f3c5731a4dc
 /etc/emacs/site-start.d/50a2ps.el 068898100c5014ea731ac7a1d55e65e0[/B]
```

---

### Post by jwandborg on 2010-10-13
I had a problem with the package manager in Debian after I had killed an [FONT="Courier New"][COLOR="DarkGreen"]$ aptitude install php5-dev[/COLOR][/FONT] process (the process was in a [Y/n/xxx] prompt and I disconnected from the shell).

I am trying the *dpkg --get/set-selelctions*, I'll se if it works.

Examples of my problem is available at [http://gist.github.com/623774]("http://gist.github.com/623774").

Here's the bad-install file: [http://wandborg.se/~root/bad-install.txt]("http://wandborg.se/~root/bad-install.txt")

Here's the good-install file: [http://wandborg.se/~root/good-install.txt]("http://wandborg.se/~root/good-install.txt")

---

### Post by Nahl_bee on 2011-11-03
Help me sir. . .when i want to install a software. . .this message always shown

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.



please help me. . .

---

### Post by drs305 on 2011-11-04
@ Nahl_bee,

Welcome to the Ubuntu forums.  :-)

First, have you installed the mscorefonts? You can get them by installing *ubuntu-restricted-extras*. You should also install *ttf-mscorefonts-installer*

You can do both via the terminal:
```
sudo apt-get install ttf-mscorefonts-installer ubuntu-restricted-extras
```

To open a terminal, type ALT-F2 and type 'gnome-terminal'. When you run a 'sudo' command in a terminal, it will ask for your password. You won't see it as you type.

If you still get the error, try these commands:
```
sudo apt-get install -f
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

---

### Post by Nahl_bee on 2011-11-07
@drs305

wow. . that's great sir,thank you very much for your help. :D

i'm a newbie in linux, what must i do for my new installed ubuntu 11.10?  maybe some tweak tips and great software that must be installed?


(my english is too bad. . sorry if there are some mistakes in my comment. . .=D  )

---

### Post by drs305 on 2011-11-07
> **Nahl_bee said:**
> @drs305

wow. . that's great sir,thank you very much for your help. :D

i'm a newbie in linux, what must i do for my new installed ubuntu 11.10?  maybe some tweak tips and great software that must be installed?


(my english is too bad. . sorry if there are some mistakes in my comment. . .=D  )

I'm happy your system is now working.

Your question is really too general to answer. Take it slowly. When you find you want or need something specific and don't know how to do it, perform a search of the forums via the 'Search' link at the top of the forum pages, or use an Internet search engine. 

Things have changed so much over the years that I normally use the 'advanced' option to limit answers to those written within the past six months. If I don't find an answer I'll then expand it to a longer time frame if necessary. 

Fortunately Ubuntu has been around long enough that whatever you want to do has most likely been thought of by others as well. And since users are happy to share their successes, you can probably find it documented online.

Happy Ubuntu-ing.

---

