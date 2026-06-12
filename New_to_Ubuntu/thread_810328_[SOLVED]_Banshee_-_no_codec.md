---
title: "[SOLVED] Banshee - no codec"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by tqprvn on 2008-05-28
hi all

Just went up to 8.04, had to reinstall Banshee, which detected my library fine, but is unable to play any of my music - every song says 'no codec'

huh?

Matt

---

### Post by sayakb on 2008-05-28
At a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
Will install the gstreamer codecs.

---

### Post by kpkeerthi on 2008-05-28
```
sudo aptitude --with-recommends --with-suggests install banshee
```

That will install the suggessted and recommended codecs for banshee.

---

### Post by tqprvn on 2008-05-28
> At a terminal:
Code:

sudo apt-get install ubuntu-restricted-extras

Will install the gstreamer codecs.

I guess I had to do that at some point anyhow, but nup, that didnt get it - all still codecless.

---

### Post by sayakb on 2008-05-28
Are all your repos enabled?
Goto System->Administration->Software sources and enable all your repos.
Then do:
```
sudo apt-get update
```
And try to install using either of the above.

---

### Post by tqprvn on 2008-05-28
> **kpkeerthi said:**
> ```
sudo aptitude --with-recommends --with-suggests install banshee
```

That will install the suggessted and recommended codecs for banshee.
hmm, tried this and now i get more options (newbie at the wheel - caution!)

this is what came back

```
matt@matt-laptop:~$ sudo aptitude --with-recommends --with-suggests install banshee
aptitude: unrecognized option `--with-suggests'
aptitude 0.4.9
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends	Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
matt@matt-laptop:~$ install
install: missing file operand
Try `install --help' for more information.
matt@matt-laptop:~$ 

```

gulp.

---

### Post by sayakb on 2008-05-28
Try installing the restricted extras packages..

---

### Post by kpkeerthi on 2008-05-28
> **tqprvn said:**
> hmm, tried this and now i get more options (newbie at the wheel - caution!)

this is what came back

--edited--

gulp.

Change it to **sudo aptitude --with-recommends install banshee**

---

### Post by tqprvn on 2008-05-28
> **LinuxIsInnovation said:**
> Try installing the restricted extras packages..
did that first, restarted Banshee, still 'no codec' all round.

tried the second suggestion, and got the result in my subsequent post.

---

### Post by kpkeerthi on 2008-05-28
Go to System -> Admin -> Software Sources and enable the **Universe **and **Multiverse **repositories and then run the command below.

```
sudo aptitude --with-recommends install banshee
```

---

### Post by tqprvn on 2008-05-28
> **kpkeerthi said:**
> Change it to **sudo aptitude --with-recommends install banshee**
which leads me here...

```
matt@matt-laptop:~$ sudo aptitude --with-recommends install banshee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libfaad2-0 libiso9660-4 liblzo1 libmp4v2-0 libungif4g libx264-54 
The following packages have been automatically kept back:
  gcc-3.3-base 
The following packages have been kept back:
  libpam-smbpass libstdc++5 samba samba-common smbclient smbfs thunderbird 
0 packages upgraded, 0 newly installed, 6 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 2028kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 69550 files and directories currently installed.)
Removing libfaad2-0 ...
Removing libiso9660-4 ...
Removing liblzo1 ...
Removing libmp4v2-0 ...
Removing libungif4g ...
Removing libx264-54 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
matt@matt-laptop:~$ 
```

....but with still no codecs.

---

### Post by sayakb on 2008-05-28
Okay.. open synaptic package manager and search for gstreamer plugins. Check whether you've got them installed or not..

---

### Post by kpkeerthi on 2008-05-28
> **kpkeerthi said:**
> Go to System -> Admin -> Software Sources and enable the **Universe **and **Multiverse **repositories and then run the command below.

```
sudo aptitude --with-recommends install banshee
```

Did you try this?

---

### Post by tqprvn on 2008-05-28
> **kpkeerthi said:**
> Go to System -> Admin -> Software Sources and enable the **Universe **and **Multiverse **repositories and then run the command below.

```
sudo aptitude --with-recommends install banshee
```
done.  Still no go.

---

### Post by tqprvn on 2008-05-28
> **LinuxIsInnovation said:**
> Okay.. open synaptic package manager and search for gstreamer plugins. Check whether you've got them installed or not..
done - theyre installed already.

---

### Post by sayakb on 2008-05-28
You're playing MP3s, right? Just reboot once. If still this doesn't work, goto ~/.config/banshee and copy the file banshee.db to some safe place and do:
```
sudo apt-get purge banshee
sudo apt-get install banshee
```

Then copy back the banshee.db to the original location and try again..

---

### Post by kpkeerthi on 2008-05-28
> **tqprvn said:**
> done.  Still no go.

Does totem play your music files?

---

### Post by tqprvn on 2008-05-28
> **LinuxIsInnovation said:**
> You're playing MP3s, right? Just reboot once. If still this doesn't work, goto ~/.config/banshee and copy the file banshee.db to some safe place and do:
```
sudo apt-get purge banshee
sudo apt-get install banshee
```

Then copy back the banshee.db to the original location and try again..

yup, this got it, thanks.

---

### Post by itsjustarumour on 2008-06-07
> **LinuxIsInnovation said:**
> You're playing MP3s, right? Just reboot once. If still this doesn't work, goto ~/.config/banshee and copy the file banshee.db to some safe place and do:
```
sudo apt-get purge banshee
sudo apt-get install banshee
```

Then copy back the banshee.db to the original location and try again..

Had the same problem with the new Banshee 1.0.0 but this fixed it - thanks!

---

