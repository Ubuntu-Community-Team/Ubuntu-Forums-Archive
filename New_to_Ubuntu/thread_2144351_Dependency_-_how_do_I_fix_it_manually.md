---
title: "Dependency - how do I fix it manually"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by layers on 2013-05-11
I have never understood how to fix the dependency probems, when they happen.

I have to install my printer software (even if it breaks something else - to force it). But I don't know how. This is what I get:> The following packages have unmet dependencies:

hplip: Depends: libhpmud0 (= 3.12.2-1ubuntu3) but 3.12.2-1ubuntu3.1 is to be installed
       Depends: libsane-hpaio (= 3.12.2-1ubuntu3) but 3.12.2-1ubuntu3.1 is to be installed
       Depends: hplip-data (= 3.12.2-1ubuntu3) but 3.12.2-1ubuntu3.1 is to be installed
       Depends: printer-driver-hpcups (= 3.12.2-1ubuntu3) but 3.12.2-1ubuntu3.1 is to be installed
       Depends: python (< 2.8) but 2.7.3-0ubuntu2 is to be installed
       Depends: coreutils (>= 5.1.0) but 8.13-3ubuntu3.2 is to be installed
       Depends: adduser (>= 3.34) but 3.113ubuntu2 is to be installed

How do I force the installation, even if ither stuff become broken?

---

### Post by ibjsb4 on 2013-05-11
Are you installing hplip from the software center?

---

### Post by squakie on 2013-05-11
From the outside looking in, it looks like you are trying to install something that relies on older library versions than your current version of Ubuntu.

There are some basic things first, though:

What kind of printer?  It appears you are installing for an HP printer.  Just loading the hp print package(s) via the software center or Synaptic Package Manger should load what you need and should load the dependencies as well.

Most of the time I have seen dependency issues have been with people manually installing, and not usually not from the Ubuntu repositories.  In such instances, dependencies are not automatically resolved as they are with the the software center or the package managers.  It is always recommended to install from the repositories using the package manager.  With that being said, exactly what are you trying to install?  Where did you get it?

---

### Post by layers on 2013-05-12
When I try instaling it manually, from sh, it gives an error(from hplip's website). When I try through the Software Centre, the quote is shown.

Should I just install synaptic then? Would that force it?

---

### Post by squakie on 2013-05-12
So, are you installing a package from hplip's site that you have downloaded, or have you been using the hplip from the repositories?  To met, it looks like you have a version of hplip that is not compatiable with your current version of Ubuntu.  So, a couple of more questions:

- is this a package you downloaded?  If so, from where? (the http address).
- what version/release of Ubuntu are you running?

---

### Post by mc4man on 2013-05-12
what does this show
```
apt-cache policy hplip
```

---

### Post by ibjsb4 on 2013-05-12
I don't have any use for hplip package, but I did just download it (from the software center) without problems.

[Try this in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal"), enter one line at a time.

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install hplip
```

EDIT: Try post #6 first.

---

### Post by layers on 2013-05-12
I downloaded an sh script form HPLIP's website, and that gives me an error.
I also found hplip in the software centre, that gives me the quote on post#1
Ubuntu 12.04
> ibo@ibo-VPCF130FD:~$ apt-cache policy hplip
hplip:
  Installed: (none)
  Candidate: 3.12.2-1ubuntu3
  Version table:
     3.12.2-1ubuntu3.1 0
        100 /var/lib/dpkg/status
     3.12.2-1ubuntu3 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
ibo@ibo-VPCF130FD:~$ 


---

### Post by mc4man on 2013-05-13
> **layers said:**
> I downloaded an sh script form HPLIP's website, and that gives me an error.
I also found hplip in the software centre, that gives me the quote on post#1Ubuntu 12.04
You need to  install the precise-updates version of hplip, it's 3.12.2-1ubuntu3**.1** 

open software sources
Under the Update tab make sure the first 2 are enabled, (precise-security, precise-updates
If not enabled then do so & run an update, then try to install hplip again

If both were already enabled - 
Update your sources & see if 3.12.2-1ubuntu3.1  becomes available

If not, then back in software sources change to the Main or US mirror, update sources & recheck

If still not avail. then enable the proposed repo in software sources > Update tab, update sources yet again & see. 
If installing from proposed you may wish to disable the proposed repo afterwards

---

### Post by squakie on 2013-05-13
Please remember to use the Ubuntu tools - like software center or one of the package managers to install software like this.  Hp has always had great support for Linux and everything you should need are available via Ubuntu.  You shouldn't normally need to go to HP's site for anything - not the software, not a script.  That's why I suggested backing out what you have done.  Then be sure, as mentioned by others, that the repositories are set correctly for your version of Ubuntu.  Once that is done you shouldn't have a problem.  *if* you downloaded a driver package from HP and then tried installing it either from the shell or by clicking on it and having it open via the software center, that is probably part of your problem right now - that's why I recommended backing it all out, as it wants some things that aren't part of your current Ubuntu installation.

It's not something I would normally try in a case like this, but there is also sudo apt-get build-dep <package name> that will try to resolve the dependencies for <package>.  In your case, *if* it did work, you'd end up with multiple versions of some libraries that could cause problems.  This may not work in this case anyway as it still uses the repositories and they appear to not match whatever version of the package you are installing.

---

### Post by layers on 2013-05-15
many thanks, once again, the ubutnu community is best.
I had turned off those two update options, as I normally don't do updates. After enabling them, the installer script ran without a fail, and it's been printing without problems for a few days now.

---

### Post by ibjsb4 on 2013-05-15
Congratulations and don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

