---
title: "Deleting a program properly"
date: 2018-08-29
forum: New to Ubuntu
---

### Post by vysero on 2018-08-29
Hello! So I installed Qt from source and then I went ahead and deleted the directory thinking that would delete the program. Apparently that was incorrect because if I do a: qmake --version it pops up: QMake version 2.01a
Using Qt version 4.8.7 in /usr/lib/x86_64-linux-gnu. Is deleting the x86_64-linux-gnu directory in /usr/lib all I need to do? It isn't a huge problem or anything I think if I installed a new version of Qt that it would override the old version.

If you are curious I can't actually install from 'Ubuntu software' for some reason. Any time I try the programs never actually run. I am able to download them but if I click there icons they simply blink a few times and never open. Which is frustrating because it means I have to install everything either from source or from sudo-apt get command but that is a different question for a different thread I am sure.

---

### Post by deadflowr on 2018-08-29
>  Is deleting the x86_64-linux-gnu directory in /usr/lib all I need to do? 
Absolutely **do not delete** that directory.
It holds a ton of very important libraries used by a ton of various parts of the system.
Deleting that directory will break the system.

If you installed qmake from source look in the /usr/local directory tree.
That's where most source installed packages will be installed to, as a default.
You might also look at the source package installed from for a README file, which may include a howto uninstall.


And as for Ubuntu Software not running, hmm, what does running the apt commands show you.
And if you try launching with the terminal command ubuntu-software show?

---

### Post by vysero on 2018-08-29
Okay I found where this qt is, it's located in tmp. What is the tmp directory for and should I delete the qt directory from tmp or try to uninstall it?

I installed a random program from 'Ubuntu software' called Colibri and attempted to run it from the terminal:

```
murchrob@bznlinux038:~$ colibri
cannot create user data directory: /home/spray.com/murchrob/snap/colibri/7: Permission denied
murchrob@bznlinux038:~$ sudo colibri
[sudo] password for murchrob: 
mkdir: cannot create directory '/run/user/0': Permission denied
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Documents': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Desktop': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Downloads': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Music': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Pictures': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Videos': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Templates': No such file or directory
No protocol specified
```

Similar things usually happen when I attempt to start programs installed from 'Ubuntu Software' via the command prompt. Some type of 'Permission denied' usually pops up.

---

### Post by Impavidus on 2018-08-29
Running those sudo apt-get commands is much better than installing from source. Behind the scenes Ubuntu Software also issues those apt-get commands (more or less). Once software has been installed, there's no way to tell whether that was done via Ubuntu Software or directly using the command line. And there's synaptic package manager too.

And don't delete /usr/lib/x86_64-linux-gnu. That will really mess up your system, forcing you to reinstall. There's not one standard way to manually install stuff from source, so there's not one standard way to remove it either. You should be able to find more information in the documentation you got with the source code, but if everything was done properly, it should all be in /usr/local/.

Edit: Didn't see above post before posting this one.

---

### Post by DuckHook on 2018-08-29
I hope you won't take this the wrong way. It is not meant as criticism; just as observation. Seguing from deadflowr's comments and extrapolating from your original post, it will be very difficult and may prove impossible to chase down your problems, mainly due to the following issues:

[LIST=1]
[*]You have probably installed all sorts of apps and system services, some obscure, some from source.
[*]You have then deleted directories without properly uninstalling those apps/services.
[*]Your penchant for tinkering may have changed/deleted other key system files/directories.
[/LIST]
If the above are accurate, then unless you can remember all of the changes you've made to your system in complete detail, it is not realistic to try putting Humpty Dumpty back together again. The components in a modern distro like Ubuntu are very complex and interdependent, and your problems may be a result of any of a hundred different combinations of changes.

If you wish to try chasing things down, then you must follow deadflowr's instructions:> **deadflowr said:**
> And as for Ubuntu Software not running, hmm, what does running the apt commands show you.
And if you try launching with the terminal command ubuntu-software show?There's no point in complaining about installation difficulties without following deadflowr's diagnostic instructions.

Frankly, IMO your best bet is to backup your data and reinstall the OS. It will likely take less time.

Starting from a fresh install, you may wish to consider doing your future tinkering in a VM so that you can roll back to a previous snapshot if/when things go wrong. I certainly would not discourage you from tinkering—that's how we all learn—but there are better ways to do such things that don't involve the pain.

---

### Post by vysero on 2018-08-29
Yeah, no it's no problem. In my last post I believe I did what deadflowr was asking for. I downloaded an app from 'Ubuntu Software' that was experiencing the issue that I referred to in my original post and then tried running it from the command prompt. I posted the results of what was detailed in the terminal window after the attempt. Was that not what he was asking me to do?

---

### Post by monkeybrain20122 on 2018-08-29
> **Impavidus said:**
> Running those sudo apt-get commands is much better than installing from source. Behind the scenes Ubuntu Software also issues those apt-get commands (more or less). Once software has been installed, there's no way to tell whether that was done via Ubuntu Software or directly using the command line. And there's synaptic package manager too.

And don't delete /usr/lib/x86_64-linux-gnu. That will really mess up your system, forcing you to reinstall. There's not one standard way to manually install stuff from source, so there's not one standard way to remove it either. You should be able to find more information in the documentation you got with the source code, but if everything was done properly, it should all be in /usr/local/.

Yeah but sudo apt get gets you very old version which may not be adequate, or you may want to optimize things for performance instead of the stock build (e.g I do scientific stuffs and the default libblas from Ubuntu/debian is single threaded, it is a piece of garbage, and the stock openblas from repo is outdated and not optimized, I did a simple experiment: default blas takes more than 30s, stock openblas from repo takes 6-7s, self compiled openblas 1.5s! so tell me sudo apt get is the best. :))

There are safer ways to install from source instead of littering the file system with random files.

One way is to use checkinstall (in repo) instead of make install, that way it will create a .deb file which registers with the package management system so it is easy to remove with apt remove or synaptic.

The other way is to install in $HOME and then make symlinks to /usr/local/lib, /usr/local/include or /usr/local/bin as needed, or just set environmental variables such as $PATH and $LD_LIBRARY_PATH in either .profile or .bashrc. The point is you know where your custom installs are and whatever you do can be undone easily so you don't mess with the system's file system. I have qt5 in $HOME/opt and I use it to compile other apps because I don't want to change the qt default and also Ubuntu 16.04's qt5 is ancient and doesn't work for things that I want to install. 

Update-alternatives is also a very useful way to switch between different versions.

---

### Post by DuckHook on 2018-08-29
> **vysero said:**
> Yeah, no it's no problem. In my last post I believe I did what deadflowr was asking for. I downloaded an app from 'Ubuntu Software' that was experiencing the issue that I referred to in my original post and then tried running it from the command prompt. I posted the results of what was detailed in the terminal window after the attempt. Was that not what he was asking me to do?Ah. I see where the miscommunication is. For starters, post back the results of:```
sudo apt update
``````
sudo apt full-upgrade
```What does a simple update/upgrade cycle return? deadflowr's second request was to open a terminal and do:```
ubuntu-software
```…because starting an app from a terminal will provide error messages that are otherwise shuffled off to thin air.

---

### Post by monkeybrain20122 on 2018-08-29
> **vysero said:**
> Okay I found where this qt is, it's located in tmp. What is the tmp directory for and should I delete the qt directory from tmp or try to uninstall it?

I installed a random program from 'Ubuntu software' called Colibri and attempted to run it from the terminal:

```
murchrob@bznlinux038:~$ colibri
cannot create user data directory: /home/spray.com/murchrob/snap/colibri/7: Permission denied
murchrob@bznlinux038:~$ sudo colibri
[sudo] password for murchrob: 
mkdir: cannot create directory '/run/user/0': Permission denied
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Documents': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Desktop': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Downloads': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Music': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Pictures': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Videos': No such file or directory
ln: failed to create symbolic link '/root/snap/colibri/7/snap/colibri/7/Templates': No such file or directory
No protocol specified
```

Similar things usually happen when I attempt to start programs installed from 'Ubuntu Software' via the command prompt. Some type of 'Permission denied' usually pops up.

This is a snap. So it is not registered with apt or the normal packaging system (which uses apt). I find these snap packages problematic since they are kind of beta at best. I personally really don't think they should push these beta stuffs on  unsuspecting users through the software store. I suggest you install the synaptic package manager and browse the software available from there. The listing is much more complete except for paid apps and snaps.
```

sudo apt install synaptic
```

---

### Post by DuckHook on 2018-08-29
> **monkeybrain20122 said:**
> This is a snap. So it is not registered with apt or the normal packaging system (which uses apt). I find these snap packages problematic since they are kind of beta at best. I personally really don't think they should push these beta stuffs on  unsuspecting users through the software store. I suggest you install the synaptic package manager and browse the software available from there. The listing is much more complete except for paid apps and snaps…Good catch and also +1 on the advice.

---

### Post by vysero on 2018-08-29
Here are the results for sudo apt update:
```

murchrob@bznlinux038:~$ sudo apt update
[sudo] password for murchrob: 
Err:1 http://archive.getdeb.net/ubuntu trusty-getdeb InRelease
  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused)
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://ppa.launchpad.net/dominik-stadler/dsta-xenial-ppa/ubuntu xenial InRelease
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]                           
Hit:5 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial InRelease                               
Hit:6 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu xenial InRelease                               
Hit:7 http://archive.ubuntu.com/ubuntu xenial-backports InRelease                                            
Hit:8 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease                            
Get:9 http://archive.ubuntu.com/ubuntu xenial-security InRelease [107 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main Sources [319 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/universe Sources [218 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [840 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [757 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [681 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [622 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-security/main Sources [131 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-security/universe Sources [71.6 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages [549 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages [476 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [368 kB]
Fetched 5,248 kB in 3s (1,481 kB/s)                        
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/trusty-getdeb/InRelease  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused)
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Here are the results for sudo apt full-upgrade:

```
murchrob@bznlinux038:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libreadline5 linux-headers-4.15.0-30 linux-headers-4.15.0-30-generic linux-image-4.15.0-30-generic
  linux-modules-4.15.0-30-generic linux-modules-extra-4.15.0-30-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libpoppler-glib8 libpoppler58 poppler-utils
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 991 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] yes
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpoppler58 amd64 0.41.0-0ubuntu1.8 [756 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpoppler-glib8 amd64 0.41.0-0ubuntu1.8 [104 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 poppler-utils amd64 0.41.0-0ubuntu1.8 [131 kB]
Fetched 991 kB in 1s (712 kB/s)        
(Reading database ... 387299 files and directories currently installed.)
Preparing to unpack .../libpoppler58_0.41.0-0ubuntu1.8_amd64.deb ...
Unpacking libpoppler58:amd64 (0.41.0-0ubuntu1.8) over (0.41.0-0ubuntu1.7) ...
Preparing to unpack .../libpoppler-glib8_0.41.0-0ubuntu1.8_amd64.deb ...
Unpacking libpoppler-glib8:amd64 (0.41.0-0ubuntu1.8) over (0.41.0-0ubuntu1.7) ...
Preparing to unpack .../poppler-utils_0.41.0-0ubuntu1.8_amd64.deb ...
Unpacking poppler-utils (0.41.0-0ubuntu1.8) over (0.41.0-0ubuntu1.7) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpoppler58:amd64 (0.41.0-0ubuntu1.8) ...
Setting up libpoppler-glib8:amd64 (0.41.0-0ubuntu1.8) ...
Setting up poppler-utils (0.41.0-0ubuntu1.8) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
```

On the last part are you asking me to start 'Ubuntu Software' from the terminal instead of the icon? I am capable of installing apps from 'Ubuntu Software'.

Hmm maybe if I give an example run:

I open terminal and type ubuntu-software (normally I would just double-click the icon) then I install notepad++. It installs just fine and shows up on the installed page. Now if I go to edit say some kind of .cpp file by right-clicking the file and choosing: open with notepad++. It attempts to open the file with notepad++ (as evident by the icon for notepad++ showing up) however, it never succeeds. The notepad++ icon just flashes a few times and then goes away.

Does that makes sense? Sorry, its an odd issue and I am not sure if I am explaining it fully.

---

### Post by monkeybrain20122 on 2018-08-29
> Err:1 [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb InRelease
  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused

This repository is for Trusty (Ubuntu 14.04) and it seems that you are running Ubuntu 16.04 (xenial) from the rest. You should remove that ppa.


> I open terminal and type ubuntu-software (normally I would just 
double-click the icon) then I install notepad++. It installs just fine 
and shows up on the installed page. Now if I go to edit say some kind of
 .cpp file by right-clicking the file and choosing: open with notepad++.
 It attempts to open the file with notepad++ (as evident by the icon for
 notepad++ showing up) however, it never succeeds. The notepad++ icon 
just flashes a few times and then goes away.


Well notepad++ is a windows app, I don't know why you would need it in the first place, there are tons of editors available on Linux and gedit is more than adequate for your purpose. That being said this is yet another snap package from the Software store, so not surprised if it is broken. I would just remove it.

```
sudo snap remove notepad++
```

---

### Post by DuckHook on 2018-08-29
monkeybrain has zeroed in on most of your issues. Over the course of 12 posts, it is easy to lose the thread, so to both extrapolate and summarize the advice:

[LIST=1]
[*]You apparently do not actually have a problem updating and upgrading "regular" software. *apt* runs and isn't broken.
[*]You do have an old PPA pointing to a trusty app that probably doesn't work in Xenial and is unlikely to be even supported by its author given that it is obsolete.
[*]You seem to install apps a little too freely. So far, you've mentioned a number of snaps and a broken source install. You also have at least 5 PPAs. While not all PPAs are problematic, they are unvetted by the devs and therefore increase your attack/breakage surface.
[*]You are perhaps confusing regular packages with *snaps*. I agree with monkeybrain that you should stay away from *snaps*, at least until you are more familiar with the Ubuntu ecosystem and know what you are getting into when you install one.
[*]I also feel that you should avoid installing anything from source. If you find this to be non-negotiable, then at least use monkeybrain's suggestion of *checkinstall* which produces a *.deb* file that can then be installed using *apt* and will be tracked by your *dpkg* database.
[*]Like monkeybrain, I don't know why you want to install *notepad++*. This seems to indicate that you are not that familiar with the Linux ecosystem or the differences between Windows and Linux. There is a link in my sig, "Linux is not Windows", that might help.
[*]You may wish to reconsider your computing habits. Many ordinary users add far too many unnecessary apps into their installs. This not only destabilizes the system, but adds attack surfaces for scoundrels. PPAs are a known risk. Earlier this year, two rogue apps were found in the *snap* store.
[*]If you are an inveterate tinkerer and app sampler, consider installing a VM and doing all of your experimentation within a secure and easily recoverable sandbox.
[/LIST]
Hope this summary is useful.

---

### Post by vysero on 2018-08-30
Sure yeah no problem. Tbh I just picked notepad++ randomly I don't actually want to use it. I was not aware of what a snap app was so that's good to know. Just to be sure I will try downloading an app from 'Ubuntu Software' that is not a snap app and I will post my results.

It was mentioned that I "...have an old PPA pointing to a trusty app that probably doesn't work in Xenial...". How would I go about removing what I need to remove with regards to this 'Trusty'?

---

### Post by deadflowr on 2018-08-30
> It was mentioned that I "...have an old PPA pointing to a trusty app that probably doesn't work in Xenial...". How would I go about removing what I need to remove with regards to this 'Trusty'?
   &#65532; 

Quick way, open the program Software and Updates and go to the tab-section Other Software.
Scroll down to find the getdeb entry and uncheck it (or highlight it and select the remove option at the bottom area.
Then close Software and Updates.

Fyi, there is no use trying to update it to xenial as the getdeb repo is dead, currently. (Or was dead)
In case you wanted to do that.
In fact that's what the error you got was for.
The error isn't because of some mix-match repo problem, but because the repo it's looking for does not exist.
And that issue applies to the xenial version of the getdeb repo as well.

As if that helps

---

### Post by vysero on 2018-08-30
Okay great thanks!

---

