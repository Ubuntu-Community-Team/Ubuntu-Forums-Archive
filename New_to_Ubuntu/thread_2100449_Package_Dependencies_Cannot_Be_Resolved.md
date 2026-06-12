---
title: "Package Dependencies Cannot Be Resolved"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by LukeZoetebier on 2013-01-01
Hi guys, 
whenever I want to install Wine I get this error

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

Would anybody want to help me ?

Luke.

---

### Post by JiuJitsu500 on 2013-01-01
how are you trying to install WINE?

---

### Post by LukeZoetebier on 2013-01-01
Through Ubuntu software center

---

### Post by JiuJitsu500 on 2013-01-01
Open a terminal and try to run:

sudo apt-get -f install

and see if it fixes anything. If not, you might have to install the dependencies first, then the package. Sounds like an old problem when people would install a package from a repo that wasn't in their distribution's repository... which is odd.

---

### Post by JiuJitsu500 on 2013-01-01
You know what, I bet that doesn't do anything...

Try going to Software Sources, click on the Software Sources Tab, then adding all the boxes, change the download from box to Main Server, Add everything in the next tab except the CD options, and check all four boxes in the next tab.

Then, close out of that, and either click "check" in update manager, or run "sudo apt-get update && sudo apt-get upgrade"

Then, you may have to reboot, but that's fine. Try installing WINE again when you've updated everything.

---

### Post by LukeZoetebier on 2013-01-01
Thanks for your quick reply.
Weird, still can't install WINE.
Still get the same error.

---

### Post by LukeZoetebier on 2013-01-01
I actually downloaded WINE of the official website.
But how do I install it?  because it's a rpm file.

---

### Post by JiuJitsu500 on 2013-01-01
[Here]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien") is a link to converting rpm to deb.

.rpm is for red hat, suse, mandriva, fedora, CentOS too I think. Ubuntu is Debian based, so requires .deb. The good thing about Debian is that it's the most common type of linux so most developers will package as .deb... I know wine has a debian file. Also tarballs are universal for linux, but are not so easy to install as having the software center or gdebi do it for you. Either way though, any tarball or .deb is what you'd need.

Download the .deb, or use the alien tool to convert and see if that helps. If not, try installing all those packages it says you need through synaptic or apt-get, then wine.

---

### Post by Cheesehead on 2013-01-01
> **LukeZoetebier said:**
> Hi guys, 
whenever I want to install Wine I get this error

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

That error message is important.

The package manager is telling you two important facts:
1) You already have wine installed.
2) You are trying to replace a newer version of wine with an older version. Rarely is that action intended by the user, so the package manager balks.

The package manager isn't telling you an important third fact:
3) Your package management system is broken. You cannot install, uninstall, upgrade, or receive security updates until you fix it.


You seem to have installed an upstream version of wine, you're trying to install an rpm of wine, and you're trying to install wine through the software center. That's unusual, too.

Are you simply having trouble installing wine? What kind of trouble?

Are you trying different versions of wine in the hopes that a specific application will work? There are easier ways, like checking the upstream version in the package. Or the wine compatibility database.

Do you know how to uninstall an application if you want to replace it? Or did you have a problem with the uninstall?

Do you know how you installed non-Ubuntu version(s) of wine 1.4? Do you remeber where you downloaded it(them) to? Are they still there? Do you have the original install/uninstall instruction(s)?

---

### Post by LukeZoetebier on 2013-01-02
Hi guys, 

I actually deleted a few WINE packages. 
I tried to install it with synaptic now but I get this error :

wine1.4-common:
 Depends: wine1.4 but it is not going to be installed

I tried to install the .rpm package with :
Sudo alien wine.rpm
it says this:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "nl_NL.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
File "wine.rpm" not found.

which is weird because the file is called wine.rpm.

Luke.

---

### Post by zombifier25 on 2013-01-02
You should not use the .rpm package though. Try using the wine PPA
```
sudo add-apt-repository ppa:ubuntu-wine/ppa && sudo apt-get update
sudo apt-get purge wine wine1.4
sudo apt-get install wine1.4
```
and see if it fixes it.

---

### Post by mc4man on 2013-01-02
Don't bother with a rpm, no need, no good.

Either get the ubuntu repo wine installed or use the team wine ppa

For ubuntu repo try this - 
open synaptic, search wine, mark **all** wine packages installed for removal, click Apply.
Then click the "Reload" button in synaptic, when done just mark the "**wine**" package for install, apply.

For the ppa - 
open synaptic, search wine, mark **all** wine packages installed for removal, Apply. Then close synaptic
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
then after adding - 
```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by Cheesehead on 2013-01-02
The type of messages you describe may indicate that you installed a wine package using a package manager, but then uninstalled the package manually by deleting files. If true, the package manager still thinks wine is installed, and you will need to reinstall the same package properly, then uninstall it properly to resolve the problem. The package manager will easily do both those actions for you...if you tell it to.

Don't try to install a new version of wine until you have *properly* uninstalled the old. Or you will make things worse.

How, exactly did you install the now-removed version. Be specific: Where did you get it from, what instructions did you follow? 

And how, in exact detail if possible, did you remove it? Did you follow any instructions to remove it? Did you manually delete any files? Do you remember any commands you used?

---

### Post by LukeZoetebier on 2013-01-02
When I tried to install it with terminal I get this: 
The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Sad story, sad story..

---

### Post by LukeZoetebier on 2013-01-02
Synaptic says that I don't have Wine installed.
I deleted it with terminal,
don't remember the command though..

When I click ''fix broken packages'' in Synaptic I get this :
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Oh wait I remember I used : sudo apt-get remove wine
after that I used a command to see all the packages.
Then I used the same command to remove other packages that involve wine

---

### Post by Cheesehead on 2013-01-02
Since you uninstalled wine properly (good job!), the next step is to check your sources.list. Most package management conflicts come from a PPA or third-party repository. There's also the possibility that you uninstalled a package that is needed by more than wine. Next time use the 'autoremove' option to safely remove orphaned packages.

Run the command [FONT="Courier New"]cat /etc/apt/sources.list[/FONT] and post the entire output here.

Next, run the command [FONT="Courier New"]sudo apt-get check[/FONT] and post the entire output here.

---

### Post by LukeZoetebier on 2013-01-02
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed restricted main multiverse universe


sudo apt-get check 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

---

### Post by squakie on 2013-01-02
> **LukeZoetebier said:**
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed restricted main multiverse universe


If that is the output of cat /etc/apt/sources.list, somehow you have gotten the souces.list file really messed up - there should be a lot more in there, including some comments, etc..  Did you manually edit the source.list file somewhere along the line?

---

### Post by squakie on 2013-01-02
Also, if dependencies are messed up:

sudo apt-get build-dep <package name>

---

### Post by oldos2er on 2013-01-02
> **LukeZoetebier said:**
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed restricted main multiverse universe


sudo apt-get check 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

Go to [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to generate a new sources.list file. Unless you're using them for a specific reason, you might want to re-think using the backports and proposed repositories, they may potentially cause problems.

---

